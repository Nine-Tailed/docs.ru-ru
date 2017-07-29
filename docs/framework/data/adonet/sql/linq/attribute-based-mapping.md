---
title: "Сопоставление на основе атрибутов | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Сопоставление на основе атрибутов
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] сопоставляет базу данных SQL Server с объектной моделью [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] либо путем применения атрибутов, либо с использованием файла внешнего сопоставления.  В этом разделе представлен подход на основе атрибутов.  
  
 В своей самой простой форме [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] сопоставляет базу данных с <xref:System.Data.Linq.DataContext>, таблицу с классом, а столбцы и связи \- со свойствами этих классов.  Атрибуты также можно использовать для сопоставления иерархии наследования в объектной модели.  Дополнительные сведения см. в разделе [Как создать модель объектов на языке Visual Basic или C\#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Разработчики, использующие [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], обычно выполняют сопоставление на основе атрибутов с помощью [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Можно также использовать программу командной строки SQLMetal или вручную написать код атрибутов самостоятельно.  Дополнительные сведения см. в разделе [Как создать модель объектов на языке Visual Basic или C\#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
>  Сопоставление можно также выполнять с помощью внешнего файла XML.  Дополнительные сведения см. в разделе [Внешние сопоставления](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 В следующих разделах представлено более подробное описание сопоставления на основе атрибутов.  Дополнительные сведения см. в описании пространства имен <xref:System.Data.Linq.Mapping>.  
  
## Атрибут DatabaseAttribute  
 Этот атрибут используется для указания имени базы данных по умолчанию, если оно не предоставлено при подключении.  Данный атрибут является необязательным, однако если он используется, следует применить свойство <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>, как описано в следующей таблице.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Строка|См. раздел <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.|Используется со свойством <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>, указывает имя базы данных.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## Атрибут TableAttribute  
 Чтобы определить класс как класс сущности, связанный с таблицей базы данных или представлением, используется атрибут.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] интерпретирует классы, имеющие данный атрибут, как постоянные.  В следующей таблице приводится описание свойства <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|Строка|Строка, соответствующая имени класса|Определяет класс как класс сущности, связанный с таблицей базы данных.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## Атрибут ColumnAttribute  
 Этот атрибут используется для назначения члена класса сущности, представляющего столбец в таблице базы данных.  Этот атрибут можно применять к любому полю или свойству.  
  
 Когда [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] сохраняет изменения в базе данных, извлекаются и сохраняются только те члены класса, которые определены как столбцы.  Члены без данного атрибута считаются непостоянными и не передаются для вставок или обновлений.  
  
 В следующей таблице представлено описание свойств этого атрибута.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|Никогда|Указывает среде CLR на необходимость получить значение после выполнения операции вставки или обновления.<br /><br /> Параметры: Always, Never, OnUpdate, OnInsert.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|Указывает, что столбец может содержать значения NULL.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|Строка|Определенный тип столбца базы данных|Для указания типа столбца базы данных использует типы и модификаторы базы данных.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|Строка|Empty|Определяет вычисляемый столбец в базе данных.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|Указывает, что столбец содержит значения, автоматически генерируемые базой данных.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|Указывает, что столбец содержит значение дискриминатора для иерархии наследования [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|Указывает, что этот член класса представляет столбец, входящий в состав первичных ключей таблицы.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|Определяет тип столбца члена как отметка времени или номер версии в базе данных.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, до тех пор, пока <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> имеет значение `true` для члена|Указывает, какой подход реализуется в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для обнаружения конфликтов оптимистичного параллелизма.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
>  В значениях свойства Storage для атрибутов AssociationAttribute и ColumnAttribute учитывается регистр.  Например, следует убедиться в том, что регистр символов в значении, использованном в атрибуте свойства AssociationAttribute.Storage, соответствует регистру символов в соответствующих именах свойств в остальном коде.  Это относится ко всем языкам программирования среды .NET, даже к тем, которые обычно не учитывают регистр, включая [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)].  Дополнительные сведения о свойстве Storage см. в разделе <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=fullName>.  
  
## Атрибут AssociationAttribute  
 Применяйте этот атрибут для указания свойства, которое будет представлять связь в базе данных, такую как отношение внешнего и первичного ключей.  Дополнительные сведения о связях см. в разделе [Как сопоставить связи базы данных](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
 В следующей таблице представлено описание свойств этого атрибута.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|При задании данного свойства для ассоциации, в которой члены внешнего ключа не поддерживают значение NULL, удаляет объект при установке ассоциации значения NULL.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|Строка|Нет|Добавляет в ассоциацию поведение удаления.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|При значении "true" назначает член в качестве внешнего ключа в ассоциации, представляющей отношение базы данных.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|При значении «true» указывает ограничение уникальности для первичного ключа.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|Строка|Идентификатор связанного класса|Назначает один или более членов целевого класса сущности в качестве ключевых значений на другой стороне ассоциации.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|Строка|Идентификатор содержащего класса|Назначает элементы данного класса сущности, которые будут представлять ключевые значения на этой стороне ассоциации.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
>  В значениях свойства Storage для атрибутов AssociationAttribute и ColumnAttribute учитывается регистр.  Например, следует убедиться в том, что регистр символов в значении, использованном в атрибуте свойства AssociationAttribute.Storage, соответствует регистру символов в соответствующих именах свойств в остальном коде.  Это относится ко всем языкам программирования среды .NET, даже к тем, которые обычно не учитывают регистр, включая [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)].  Дополнительные сведения о свойстве Storage см. в разделе <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=fullName>.  
  
## Атрибут InheritanceMappingAttribute  
 Применяйте этот атрибут для сопоставления иерархии наследования.  
  
 В следующей таблице представлено описание свойств этого атрибута.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|Строка|Отсутствует.  Необходимо предоставить значение.|Указывает значение кода дискриминатора.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|При значении "true" создает объект данного типа, когда значение дискриминатора в хранилище не соответствует ни одному заданному значению.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Тип|Отсутствует.  Необходимо предоставить значение.|Указывает тип класса в иерархии.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## Атрибут FunctionAttribute  
 Этот атрибут используется для назначения метода, представляющего хранимую процедуру или пользовательской функцию в базе данных.  
  
 В следующей таблице представлено описание свойств этого атрибута.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|Если значение равно false, указывает сопоставление с хранимой процедурой.  При значении «true» указывает сопоставление с пользовательской функцией.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|Строка|Строка, соответствующая имени базы данных|Указывает имя хранимой процедуры или пользовательской функции.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## Атрибут ParameterAttribute  
 Этот атрибут используется для сопоставления входных параметров в методах хранимых процедур.  
  
 В следующей таблице представлено описание свойств этого атрибута.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|Строка|Нет|Указывает тип базы данных.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|Строка|Строка, соответствующая имени параметра в базе данных|Указывает имя для параметра.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## Атрибут ResultTypeAttribute  
 Этот атрибут используется для указания типа результата.  
  
 В следующей таблице представлено описание свойств этого атрибута.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Тип|\(Нет\)|Используется в методах, сопоставленных с хранимыми процедурами, возвращающих <xref:System.Data.Linq.IMultipleResults>.  Объявляет допустимые или ожидаемые сопоставления типов для хранимых процедур.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## Атрибут DataAttribute  
 Этот атрибут используется для указания имен и закрытых полей хранения.  
  
 В следующей таблице представлено описание свойств этого атрибута.  
  
|Свойство|Тип|По умолчанию|Описание|  
|--------------|---------|------------------|--------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|Строка|Строка, соответствующая имени базы данных|Указывает имя таблицы, столбца и т. д.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|Строка|Открытые методы доступа|Указывает имя базового поля хранения.|  
  
 Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## См. также  
 [Ссылки](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)