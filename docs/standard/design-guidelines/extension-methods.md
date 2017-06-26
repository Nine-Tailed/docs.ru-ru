---
title: "Методы расширения | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# Методы расширения
Методы расширения — это функция языка, который позволяет статических методов, вызываемых с помощью синтаксиса вызова метода экземпляра. Эти методы необходимо выполнить по крайней мере один параметр, который представляет экземпляр, который является метод для выполнения операции.  
  
 Класс, который определяет такие методы расширения упоминается как класса «спонсора», и они должны объявляться как статические. Чтобы использовать методы расширения, один необходимо импортировать пространство имен определения класса спонсора.  
  
 **ИЗБЕЖАТЬ X** frivolously определяет методы расширения, особенно на типах, вы не владеете.  
  
 Если у вас есть исходный код типа, рекомендуется использовать методы регулярных экземпляра. Если у вас нет, и требуется добавить метод, необходимо Будьте очень осторожным. Надлежащее использование методов расширения может загромождения интерфейсов API типов, которые не были спроектированы для обеспечения этих методов.  
  
 **✓ Рассмотрите ВОЗМОЖНОСТЬ** использование методов расширения в любом из следующих сценариев:  
  
-   Для обеспечения поддержки функции, относящиеся к каждой реализации интерфейса, если функциональность могут быть записаны в терминах основной интерфейс. Это вызвано конкретные реализации в противном случае не может быть назначен интерфейсов. Например `LINQ to Objects` операторы реализуются как методы расширения для всех <xref:System.Collections.Generic.IEnumerable%601> типов. Таким образом, любой `IEnumerable<>` реализацию LINQ\-включается автоматически.  
  
-   Когда метод экземпляра стало бы причиной зависимость для некоторого типа, но такая зависимость нарушит правила управления зависимостей. Например, зависимость от <xref:System.String> для <xref:System.Uri?displayProperty=fullName> вероятно, не является нежелательным и поэтому `String.ToUri()` возврат метода экземпляра `System.Uri` бы неправильный проектирования с точки зрения управления зависимостей. Метод статического расширения `Uri.ToUri(this string str)` Возврат `System.Uri` бы гораздо лучше конструктора.  
  
 **ИЗБЕЖАТЬ X** определения методов расширения в <xref:System.Object?displayProperty=fullName>.  
  
 Для пользователей Visual Basic не будет иметь возможность вызывать такие методы для ссылок на объекты, используя синтаксис методов расширения. VB не поддерживается вызов таких методов, поскольку в VB, объявление ссылку как объект заставляет все вызовы метода в его конце привязан \(фактический элемент с именем определяется во время выполнения\), во время привязки к методам расширения определяются во время компиляции \(раннее связывание\).  
  
 Обратите внимание, что правило применяется для других языков, где присутствует одно и то же поведение привязки и где методы расширения не поддерживаются.  
  
 **X не** поместить методы расширения в пространстве имен, расширенный тип применяется для добавления методов к интерфейсам, или для управления зависимостями.  
  
 **ИЗБЕЖАТЬ X** определения двух или нескольких методов расширения с такой же сигнатурой, даже если они находятся в разных пространствах имен.  
  
 **✓ Рассмотрите ВОЗМОЖНОСТЬ** определение методов расширения в пространстве имен, расширенный тип, если тип является интерфейсом, а методы расширения предназначены для использования в большинство или все случаи.  
  
 **X не** определять методы расширения, реализации функции в пространствах имен, обычно связанные с другими компонентами. Вместо этого их определения в пространство имен, связанное с функцией, к которому они принадлежат.  
  
 **ИЗБЕЖАТЬ X** универсальных имен пространств имен, выделенных для методов расширения \(например, «расширения»\). Используйте описательное имя \(например, «маршрут»\) вместо.  
  
 *Частей © 2005, 2009 корпорации Microsoft. Все права защищены.*  
  
 *Воспроизведены разрешении Пирсон образования, Inc. из [Framework рекомендации по проектированию: условные обозначения, стили и шаблоны для повторного использования библиотеки .NET, второе издание](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina и Брэд Абрамс опубликованы 22 октября 2008 г., издательство Addison\-Wesley Professional как часть цикла разработки Microsoft Windows.*  
  
## См. также  
 [Рекомендации по разработке членов](../../../docs/standard/design-guidelines/member.md)   
 [Рекомендации по проектированию Framework](../../../docs/standard/design-guidelines/index.md)