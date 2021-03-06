---
title: Выбор между классом и структурой
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7590d5628f4951a8c7c2199f0e954007ed9fa962
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "50757430"
---
# <a name="choosing-between-class-and-struct"></a>Выбор между классом и структурой
Одним из основных проектных решений, каждый конструктор framework сталкивается является разработки типом, как класс (ссылочного типа) или как структура (тип значения). При этом важно хорошо понимать различия в поведении ссылочных типов и типов значений.  
  
 Первый разница между ссылочные типы и типы значений, которые мы будем считать, является то, что ссылочные типы выделенными в куче и сборщиком мусора, тогда как выделяются типы значений, либо в стеке или встроенный в, которая содержит типы и освобожден, когда стек Освобождает или когда освобождается содержащего их типа. Поэтому операций выделения и освобождения типы значений являются в целом дешевле, чем операций выделения и освобождения ссылочных типов.  
  
 Далее массивы, ссылки на типы: выделить вне строки, то есть элементы массива имеют только ссылки на экземпляры ссылочного типа, размещенных в куче. Массивы типов значений выделяются встроенный, это означает, что элементы массива являются фактическим экземплярам типа значения. Поэтому операций выделения и освобождения массивы типов значений являются гораздо дешевле, чем операций выделения и освобождения массивов ссылочного типа. Кроме того в большинстве случаев значение массивов типа проявляется гораздо лучше расположение ссылок.  
  
 Далее разницу связана с использование памяти. Типы значений упаковываться при приведении к ссылочным типом или один из интерфейсов, которые они реализуют. Они получают из упакованной при приведении к типу значения. Так как поля являются объектами, которые назначаются в куче и сборщиком мусора, слишком много упаковке и распаковке может иметь негативное влияние на кучи сборщика мусора и в конечном счете производительность приложения.  Напротив таких упаковка-преобразование не происходит, когда они приводятся ссылочные типы. (Дополнительные сведения см. в разделе [упаковка-преобразование и распаковка-преобразование](../../csharp/programming-guide/types/boxing-and-unboxing.md)).
  
 Затем назначения типа ссылки Копировать ссылку, тогда как назначения типа значение скопируйте все значение. Поэтому назначения больших ссылочных типов являются дешевле, чем назначения типов больших значений.  
  
 Наконец ссылочные типы передаются по ссылке, тогда как типы значений передаются по значению. Изменение экземпляра ссылочного типа влияет на все ссылки, указывающие на экземпляре. Экземпляры типов значения копируются в том случае, когда они передаются по значению. При изменении экземпляра типа значения, она Конечно не влияет на любой из его копии. Так как копии явным образом не создаются пользователем, но создаются неявно, когда аргументы передаются или возвращаемые значения возвращаются, типы значений, которые могут быть изменены могут запутать многие пользователи. Таким образом типы значений должны быть неизменными.  
  
 Как правило большинство типов в платформе должно быть классов. Тем не менее, существуют некоторые ситуации, в которых характеристики типа значением делающие их более подходящими использовать структуры.  
  
 **✓ CONSIDER** определение структуры вместо класса, если экземпляры типа невелики и имеют короткое время существования или внедрены в другие объекты.  
  
 **X AVOID** определение структуры, если тип не содержит все следующие характеристики:  
  
-   Он логически представляет одиночное значение, аналогичную типы-примитивы (`int`, `double`и т. д.).  
  
-   Он имеет размер экземпляра в разделе 16 байт.  
  
-   Он станет неизменяемым.  
  
-   Упаковываемый часто не будет.  
  
 Во всех остальных случаях необходимо определить типы как классы.  
  
 *Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*  
  
 *Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*  
  
## <a name="see-also"></a>См. также

- [Рекомендации по разработке типов](../../../docs/standard/design-guidelines/type.md)  
- [Рекомендации по проектированию на основе Framework](../../../docs/standard/design-guidelines/index.md)
