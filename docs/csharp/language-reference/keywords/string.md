---
title: string (Справочник по C#)
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: ab2e69c60872aed19d46450f17becc918ffe2a38
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181464"
---
# <a name="string-c-reference"></a>string (Справочник по C#)

Тип `string` представляет последовательность, состоящую из нуля или более символов в кодировке Юникод. `string` является псевдонимом для <xref:System.String> в .NET.

Несмотря на то, что `string` представляет собой ссылочный тип, операторы равенства (`==` и`!=`) по определению сравнивают не ссылки, а значения объектов `string`. Это делает проверку равенства строк более интуитивно понятной. Пример:

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

Отображается значение True, а затем False, поскольку содержимое строк эквивалентно, однако `a` и `b` не относятся к одному и тому же экземпляру строки.

Оператор + объединяет строки:

```csharp
string a = "good " + "morning";
```

При этом создается строковый объект, содержащий слова "good morning".

Строки *неизменяемы*, т. е. содержимое созданного строкового объекта изменить нельзя, хотя синтаксис выглядит так, будто это возможно. Например, при написании кода компилятор фактически создает новый строковый объект для хранения новой последовательности символов, а затем этот новый объект назначается b. После этого строка h может быть отправлена в мусор.

```csharp
string b = "h";
b += "ello";
```

Оператор [] позволяет предоставить к отдельным символам `string` доступ только для чтения:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Строковые литералы имеют тип `string` и могут быть записаны в двух формах: в кавычках или с @-quoted. Строковые литералы в кавычках заключаются в двойные кавычки ("):

```csharp
"good morning"  // a string literal
```

Строковые литералы могут содержать любые символьные литералы. Escape-последовательности включены. В следующем примере escape-последовательность `\\` используется для получения обратной косой черты, `\u0066` — для получения буквы f, и `\n` — для получения новой строки.

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> Escape-код `\udddd` (где `dddd` состоит из четырех цифр) представляет символ Юникода U+`dddd`. Также распознаются восьмизначные escape-коды Юникода: `\Udddddddd`.

Строковые литералы verbatim начинаются с `@` и также заключаются в двойные кавычки. Пример:

```csharp
@"good morning"  // a string literal
```

Преимущество сток verbatim состоит в том, что escape-последовательности *не* обрабатываются, что позволяет легко написать, например, полное имя файла:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Чтобы добавить в строку @-quoted двойные кавычки, продублируйте этот символ:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

Другие варианты использования специального символа `@` см. в разделе [@ — буквальный идентификатор](../tokens/verbatim.md).

Дополнительные сведения о строках в С# см. в разделе [Строки](../../programming-guide/strings/index.md).

## <a name="example"></a>Пример

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Рекомендации по использованию строк](../../../standard/base-types/best-practices-strings.md)
- [Ключевые слова в C#](index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ссылочные типы](reference-types.md)
- [Типы значений](value-types.md)
- [Базовые операции со строками в .NET Framework](../../../standard/base-types/basic-string-operations.md)
- [Создание строк](../../../standard/base-types/creating-new.md)
- [Таблица форматирования числовых результатов](formatting-numeric-results-table.md)