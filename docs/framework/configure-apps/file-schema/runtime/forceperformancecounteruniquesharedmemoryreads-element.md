---
title: '&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; элемент'
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f041cbfb4195b2c649c3af4fa061bf63e227df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754292"
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a>&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; элемент
Указывает, использует ли файл PerfCounter.dll параметр реестра CategoryOptions в приложении .NET Framework версии 1.1, чтобы определить, следует ли загружать данные счетчиков производительности из общей памяти конкретной категории или глобальной памяти.  
  
 \<configuration>  
\<Среда выполнения >  
\<forcePerformanceCounterUniqueSharedMemoryReads >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`enabled`|Обязательный атрибут.<br /><br /> Указывает, использует ли PerfCounter.dll параметр реестра CategoryOptions для определения необходимости загрузки данных счетчиков производительности из общей памяти конкретной категории или глобальной памяти.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|`false`|PerfCounter.dll не использует параметр реестра, установка этого параметра значение по умолчанию.|  
|`true`|PerfCounter.dll параметр CategoryOptions реестра.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|  
  
## <a name="remarks"></a>Примечания  
 В версиях .NET Framework до [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], значение соответствовало версии PerfCounter.dll, который был загружен в среду выполнения, который был загружен в процессе. Ли компьютер у обоих .NET Framework версии 1.1 и [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] установки приложения .NET Framework 1.1 загружает версию .NET Framework 1.1 PerfCounter.dll. Начиная с [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], загружается PerfCounter.dll последней установленной версии. Это означает, что приложения .NET Framework 1.1 будет загружать [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] версии PerfCounter.dll Если [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] установлен на компьютере.  
  
 Начиная с [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], при использовании счетчиков производительности, PerfCounter.dll проверяет параметр реестра для каждого поставщика определить, следует ли считать из общей памяти конкретной категории или глобальную общую память. .NET Framework 1.1 PerfCounter.dll не поддерживает эту запись реестра, так как он не учитывает общей памяти категориям; он считывает из глобальную общую память.  
  
 Для обеспечения обратной совместимости [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll не проверяет параметр CategoryOptions при запуске в приложении .NET Framework 1.1. Он просто использует глобальную общую память, так же, как .NET Framework 1.1 PerfCounter.dll. Тем не менее, можно указать [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll Проверка параметра реестра, включив `<forcePerformanceCounterUniqueSharedMemoryReads>` элемента.  
  
> [!NOTE]
>  Включение `<forcePerformanceCounterUniqueSharedMemoryReads>` элемент не гарантирует использования общей памяти конкретной категории. Политика включена для `true` только вызывает PerfCounter.dll параметр реестра CategoryOptions ссылок. Параметр по умолчанию является использование общей памяти категориям; Тем не менее можно изменить параметр, чтобы указать, что следует использовать глобальную общую память.  
  
 Раздел реестра, содержащий параметр CategoryOptions — HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. По умолчанию параметр имеет значение 3, отдает PerfCounter.dll для использования общей памяти конкретной категории. Если параметр имеет значение 0, PerfCounter.dll использует глобальную общую память. Данные экземпляра будут повторно только в том случае, если имя экземпляра не идентичен используемому экземпляру. Все версии смогут записывать в категорию. Если параметр имеет значение 1, используется глобальную общую память, но данные экземпляра можно использовать повторно, если имя категории имеет одинаковую длину поля, повторно используемые категории.  
  
 Параметры 0 и 1 может привести к утечке памяти и заполнению памяти счетчиков производительности.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как указать, что PerfCounter.dll должны ссылаться на параметр реестра CategoryOptions для определения, следует ли использовать категориям общей памяти.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
 [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)
