---
title: Оператор goto (справочник по C#)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: d4fd9f1f26b82b409d704c45e4bcf18cceef8282
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507527"
---
# <a name="goto-c-reference"></a>goto (Справочник по C#)

Оператор `goto` передает управление программой непосредственно оператору с меткой.

Оператор `goto` часто используется для передачи управления определенной метке смены регистра или метке по умолчанию в операторе `switch`.

`goto` Этот оператор также удобно использовать для выхода из глубоко вложенных циклов.

## <a name="example"></a>Пример

В следующем примере демонстрируется использование `goto` в операторе [switch](switch.md).

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Пример

В следующем примере демонстрируется использование `goto` для выхода из вложенных циклов.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)  
- [Руководство по программированию на C#](../../programming-guide/index.md)  
- [Ключевые слова в C#](index.md)  
- [Оператор goto (C++)](/cpp/cpp/goto-statement-cpp)  
- [Операторы перехода](jump-statements.md)  
