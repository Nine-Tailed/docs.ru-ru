---
title: '&lt;bypassTrustedAppStrongNames&gt; элемент'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6988be28e3129748ee7f7996a66c728ccde3c70b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745387"
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypassTrustedAppStrongNames&gt; элемент
Указывает, следует ли пропустить проверку строгих имен для сборок с полным доверием, которые загружаются с полным доверием <xref:System.AppDomain>.  
  
 \<configuration>  
\<Среда выполнения >  
\<bypassTrustedAppStrongNames >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`enabled`|Обязательный атрибут.<br /><br /> Указывает, включена ли функция пропуска, позволяющая избежать проверки строгих имен для сборок с полным доверием. Если эта функция включена, строгие имена не проверяются на правильность после загрузки сборки. Значение по умолчанию — `true`.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|`true`|Подписей строгих имен для сборок с полным доверием не проверяются при загрузке в полностью доверенных сборок <xref:System.AppDomain>. Это значение по умолчанию.|  
|`false`|Подписей строгих имен для сборок с полным доверием проверяются при загрузке в полностью доверенных сборок <xref:System.AppDomain>. Подпись со строгим именем проверяется только правильность подписи; не сравнивается с другим строгим именем для сопоставления.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|  
  
## <a name="remarks"></a>Примечания  
 Функция обхода строгих имен позволяет избежать затрат ресурсов для проверки подписей строгих имен сборок с полным доверием.  
  
 Функция обхода применима к любой сборке, подписанной со строгим именем и имеющей следующие характеристики.  
  
-   Полное доверие без <xref:System.Security.Policy.StrongName> свидетельства (например, имеет `MyComputer` доказательства зоны).  
  
-   Загрузка в домен <xref:System.AppDomain> с полным доверием.  
  
-   Загрузка из расположения со свойством <xref:System.AppDomainSetup.ApplicationBase%2A> домена <xref:System.AppDomain>.  
  
-   Подпись осуществлена без задержки.  
  
> [!NOTE]
>  Если функция пропуска отключена для всех приложений на компьютере с помощью раздела реестра, этот параметр не делает ничего. Дополнительные сведения см. в разделе [как: отключение функции пропуска строгих имен](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как указать поведение, которое проверяет подпись строгого имени для сборок с полным доверием.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
 [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Практическое руководство. Отключение возможности обхода строгих имен](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
