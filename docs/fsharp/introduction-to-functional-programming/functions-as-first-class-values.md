---
title: "Функции как значения первого класса (F#)"
description: "Узнайте, как функции повышаются до состояния первого класса в языке F #."
keywords: "visual f#, f#, функциональное программирование"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="e4be5-104">Функции как значения первого класса</span><span class="sxs-lookup"><span data-stu-id="e4be5-104">Functions as First-Class Values</span></span>

<span data-ttu-id="e4be5-105">Определяющей характеристикой функциональных языков программирования является повышение функций до состояния первого класса.</span><span class="sxs-lookup"><span data-stu-id="e4be5-105">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="e4be5-106">Можно сделать с помощью функции, все, что можно сделать со значениями других встроенных типов и иметь возможность сделать это с сопоставимым трудозатрат.</span><span class="sxs-lookup"><span data-stu-id="e4be5-106">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="e4be5-107">Ниже приведены типичные вопросы для состояния первого класса:</span><span class="sxs-lookup"><span data-stu-id="e4be5-107">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="e4be5-108">Можно ли привязать к идентификаторам функций?</span><span class="sxs-lookup"><span data-stu-id="e4be5-108">Can you bind functions to identifiers?</span></span> <span data-ttu-id="e4be5-109">То есть можно предоставить имена?</span><span class="sxs-lookup"><span data-stu-id="e4be5-109">That is, can you give them names?</span></span>

- <span data-ttu-id="e4be5-110">Для хранения функций в структурах данных, например, в списке.</span><span class="sxs-lookup"><span data-stu-id="e4be5-110">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="e4be5-111">Можно передать функции в качестве аргумента в вызове функции?</span><span class="sxs-lookup"><span data-stu-id="e4be5-111">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="e4be5-112">Можно вернуть функцию из вызова функции?</span><span class="sxs-lookup"><span data-stu-id="e4be5-112">Can you return a function from a function call?</span></span>

<span data-ttu-id="e4be5-113">Последние две меры определяют, что известно как *операции высшего порядка* или *функции высшего порядка*.</span><span class="sxs-lookup"><span data-stu-id="e4be5-113">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="e4be5-114">Функции высшего порядка принимают функции в качестве аргументов и возвращают функции в качестве значений из вызовов функций.</span><span class="sxs-lookup"><span data-stu-id="e4be5-114">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="e4be5-115">Эти операции поддерживают такие основы функционального программирования как функции сопоставления и объединение функций.</span><span class="sxs-lookup"><span data-stu-id="e4be5-115">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="e4be5-116">Присвойте имя значения</span><span class="sxs-lookup"><span data-stu-id="e4be5-116">Give the Value a Name</span></span>

<span data-ttu-id="e4be5-117">Если функция является значением первого класса, необходимо присвоить ей имя так же, как целые числа, строки и другие встроенные типы данных.</span><span class="sxs-lookup"><span data-stu-id="e4be5-117">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="e4be5-118">Это упоминается в литературе о функциональном программировании привязкой значение идентификатора.</span><span class="sxs-lookup"><span data-stu-id="e4be5-118">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="e4be5-119">F # использует [ `let` привязки](../language-reference/functions/let-bindings.md) для привязки к значениям имена: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-119">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="e4be5-120">Ниже представлены два примера.</span><span class="sxs-lookup"><span data-stu-id="e4be5-120">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="e4be5-121">Функция так же, как легко можно задать имя.</span><span class="sxs-lookup"><span data-stu-id="e4be5-121">You can name a function just as easily.</span></span> <span data-ttu-id="e4be5-122">В следующем примере определяется функция с именем `squareIt` путем связывания идентификатора `squareIt` для [лямбда-выражение](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-122">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="e4be5-123">Функция `squareIt` имеет один параметр `n`, и она возвращает квадрат этого параметра.</span><span class="sxs-lookup"><span data-stu-id="e4be5-123">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="e4be5-124">F # предоставляет следующий более сокращенный синтаксис для достижения такого же результата с меньше ввода кода.</span><span class="sxs-lookup"><span data-stu-id="e4be5-124">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="e4be5-125">В примерах, приведенных в основном используется первый стиль `let <function-name> = <lambda-expression>`, чтобы подчеркнуть сходства объявления функций и объявления других типов значений.</span><span class="sxs-lookup"><span data-stu-id="e4be5-125">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="e4be5-126">Тем не менее именованных функций могут быть написаны с сокращенный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="e4be5-126">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="e4be5-127">Некоторые примеры записываются в обоих направлениях.</span><span class="sxs-lookup"><span data-stu-id="e4be5-127">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="e4be5-128">Сохранение значения в структуре данных</span><span class="sxs-lookup"><span data-stu-id="e4be5-128">Store the Value in a Data Structure</span></span>

<span data-ttu-id="e4be5-129">Значение первого класса может храниться в структуре данных.</span><span class="sxs-lookup"><span data-stu-id="e4be5-129">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="e4be5-130">В следующем коде показано примеры, демонстрирующие хранение значений в списках и в кортеже.</span><span class="sxs-lookup"><span data-stu-id="e4be5-130">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="e4be5-131">Чтобы убедиться, что имя функции, хранимое в кортеже фактически выполняет вычисление функции, в следующем примере используется `fst` и `snd` операторов для извлечения первого и второго элемента из кортежа `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-131">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="e4be5-132">Первый элемент в кортеже — `squareIt` и второй элемент — `num`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-132">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="e4be5-133">Идентификатор `num` привязана в предыдущем примере целое число 10, которое является допустимым аргументом для `squareIt` функции.</span><span class="sxs-lookup"><span data-stu-id="e4be5-133">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="e4be5-134">Второе выражение применяется первый элемент в кортеже, второй элемент в кортеже: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-134">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="e4be5-135">Аналогичным образом, так как идентификатор `num` и может принимать целое число 10 взаимозаменяемы, поэтому можно идентификатор `squareIt` и лямбда-выражение `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-135">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="e4be5-136">Передайте значение в качестве аргумента</span><span class="sxs-lookup"><span data-stu-id="e4be5-136">Pass the Value as an Argument</span></span>

<span data-ttu-id="e4be5-137">Если значение имеет состояние первого класса на языке, можно передать в качестве аргумента в функцию.</span><span class="sxs-lookup"><span data-stu-id="e4be5-137">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="e4be5-138">Например общие для передачи целых чисел и строк в качестве аргументов.</span><span class="sxs-lookup"><span data-stu-id="e4be5-138">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="e4be5-139">В следующем коде показано целые числа и строки, передаваемые в качестве аргументов в языке F #.</span><span class="sxs-lookup"><span data-stu-id="e4be5-139">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="e4be5-140">Если функции имеют состояние первого, необходимо передать в качестве аргументов таким же образом.</span><span class="sxs-lookup"><span data-stu-id="e4be5-140">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="e4be5-141">Помните, что это первая характеристика функции высшего порядка.</span><span class="sxs-lookup"><span data-stu-id="e4be5-141">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="e4be5-142">В следующем примере функция `applyIt` имеет два параметра `op` и `arg`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-142">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="e4be5-143">При отправке в функцию, которая имеет один параметр для `op` и соответствующий аргумент для функции `arg`, функция возвращает результат применения `op` для `arg`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-143">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="e4be5-144">В следующем примере аргумент функции и целочисленный аргумент отправляются таким же образом, с помощью их имен.</span><span class="sxs-lookup"><span data-stu-id="e4be5-144">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="e4be5-145">Возможность отправки функции в качестве аргумента другой функции лежит в основе типичных абстракций функциональных языков программирования, таких как операции сопоставления или фильтрации.</span><span class="sxs-lookup"><span data-stu-id="e4be5-145">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="e4be5-146">Операция сопоставления, например, является функция высшего порядка, захватывающей общее вычисление функции, которые перехода по списку, каким-либо образом каждый элемент и затем возвращают список результатов.</span><span class="sxs-lookup"><span data-stu-id="e4be5-146">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="e4be5-147">Можно увеличить значение каждого элемента в список целых чисел, или квадрат каждого элемента или перевести каждый элемент в списке строк в верхний регистр.</span><span class="sxs-lookup"><span data-stu-id="e4be5-147">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="e4be5-148">Ошибкам часть вычисления является рекурсивным процессом, который проходит по списку и выполняет построение списка возвращаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="e4be5-148">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="e4be5-149">Эта часть захватывается функцией сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e4be5-149">That part is captured in the mapping function.</span></span> <span data-ttu-id="e4be5-150">Все же придется создавать для конкретного приложения — функция, которая будет применяться к каждому элементу списка по отдельности (Добавление, возведение в квадрат, изменение регистра).</span><span class="sxs-lookup"><span data-stu-id="e4be5-150">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="e4be5-151">Эта функция отправляется в качестве аргумента в функцию сопоставления как `squareIt` отправляется `applyIt` в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="e4be5-151">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="e4be5-152">F # предоставляет методы сопоставления для большинства типов коллекций, включая [перечислены](../language-reference/lists.md), [массивы](../language-reference/arrays.md), и [последовательности](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="e4be5-152">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="e4be5-153">В следующих примерах используются списки.</span><span class="sxs-lookup"><span data-stu-id="e4be5-153">The following examples use lists.</span></span> <span data-ttu-id="e4be5-154">Синтаксис `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-154">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="e4be5-155">Дополнительные сведения см. в разделе [перечислены](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="e4be5-155">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="e4be5-156">Возвращаемое значение из вызова функции</span><span class="sxs-lookup"><span data-stu-id="e4be5-156">Return the Value from a Function Call</span></span>

<span data-ttu-id="e4be5-157">Наконец Если функция имеет состояние первого класса на языке, необходимо вернуть в качестве значения вызова функции, так же, как возвращаются другие типы, такие как Integer и String.</span><span class="sxs-lookup"><span data-stu-id="e4be5-157">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="e4be5-158">Следующие вызовы функции возвращают целые числа и отобразить их.</span><span class="sxs-lookup"><span data-stu-id="e4be5-158">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="e4be5-159">Следующий вызов функции возвращает строку.</span><span class="sxs-lookup"><span data-stu-id="e4be5-159">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="e4be5-160">Следующий вызов функции, объявленный внутри нее, возвращает значение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="e4be5-160">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="e4be5-161">Отображается значение `True`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-161">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="e4be5-162">Возможность возвращать функцию в качестве значения вызова функции является второй характеристикой функции высшего порядка.</span><span class="sxs-lookup"><span data-stu-id="e4be5-162">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="e4be5-163">В следующем примере `checkFor` определяется как функция, которая принимает один аргумент `item`и возвращает новую функцию в качестве его значения.</span><span class="sxs-lookup"><span data-stu-id="e4be5-163">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="e4be5-164">Возвращаемая функция принимает список в качестве аргумента, `lst`и выполняется поиск `item` в `lst`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-164">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="e4be5-165">Если `item` присутствует, то функция возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-165">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="e4be5-166">Если `item` не указан, функция возвращает `false`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-166">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="e4be5-167">Как показано в предыдущем разделе, в следующем коде используется функция списка, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), для поиска в списке.</span><span class="sxs-lookup"><span data-stu-id="e4be5-167">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="e4be5-168">В следующем коде используется `checkFor` для создания новой функции, которая принимает один аргумент, списки и ищет 7 в списке.</span><span class="sxs-lookup"><span data-stu-id="e4be5-168">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="e4be5-169">В следующем примере состояние первого класса функций в языке F # для объявления функции, `compose`, которая возвращает композицию двух аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="e4be5-169">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="e4be5-170">Для более краткую версию в следующем разделе, «Функции Curried».</span><span class="sxs-lookup"><span data-stu-id="e4be5-170">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="e4be5-171">Следующий код отправляет две функции в качестве аргументов `compose`, оба из которых принимает один аргумент того же типа.</span><span class="sxs-lookup"><span data-stu-id="e4be5-171">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="e4be5-172">Возвращаемое значение имеет новую функцию, которая представляет собой сочетание двух аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="e4be5-172">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="e4be5-173">F # предоставляет два оператора `<<` и `>>`, которая объединяет функции.</span><span class="sxs-lookup"><span data-stu-id="e4be5-173">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="e4be5-174">Например `let squareAndDouble2 = doubleIt << squareIt` эквивалентно `let squareAndDouble = compose doubleIt squareIt` в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="e4be5-174">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="e4be5-175">В следующем примере возврата функции в качестве значения вызова функции создается простая игра по угадыванию.</span><span class="sxs-lookup"><span data-stu-id="e4be5-175">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="e4be5-176">Чтобы создать игру, вызовите `makeGame` со значением должен угадать, отправленным для `target`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-176">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="e4be5-177">Возвращаемое значение функции `makeGame` — функция, которая принимает один аргумент (предположение) и сообщает, является ли пробное значение правильным.</span><span class="sxs-lookup"><span data-stu-id="e4be5-177">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="e4be5-178">Следующий код вызывает `makeGame`, отправка значение `7` для `target`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-178">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="e4be5-179">Идентификатор `playGame` привязан к возвращаемому лямбда-выражению.</span><span class="sxs-lookup"><span data-stu-id="e4be5-179">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="e4be5-180">Таким образом `playGame` — функция, которая принимает в качестве одного аргумента значение для `guess`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-180">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="e4be5-181">Каррированные функции</span><span class="sxs-lookup"><span data-stu-id="e4be5-181">Curried Functions</span></span>

<span data-ttu-id="e4be5-182">Во многих примерах предыдущего раздела можно написать более кратко, используя преимущества неявный *каррирования* в объявлениях функций F #.</span><span class="sxs-lookup"><span data-stu-id="e4be5-182">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="e4be5-183">Каррирование — это процесс преобразования функции, которая имеет более одного параметра в ряд встроенных функций, каждая из которых принимает один параметр.</span><span class="sxs-lookup"><span data-stu-id="e4be5-183">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="e4be5-184">В языке F # по своей природе каррированные функции, имеющие более одного параметра.</span><span class="sxs-lookup"><span data-stu-id="e4be5-184">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="e4be5-185">Например `compose` из предыдущего раздела можно написать, как показано в следующем кратком стиле, с тремя параметрами.</span><span class="sxs-lookup"><span data-stu-id="e4be5-185">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="e4be5-186">Тем не менее, результат зависит от один параметр, который возвращает функция одного параметра, который в свою очередь, возвращает другую функцию одного параметра, как показано в `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-186">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="e4be5-187">Можно получить доступ к этой функции несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="e4be5-187">You can access this function in several ways.</span></span> <span data-ttu-id="e4be5-188">В каждом из следующих примеров возвращает и отображает 18.</span><span class="sxs-lookup"><span data-stu-id="e4be5-188">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="e4be5-189">Можно заменить `compose4` с `compose4curried` ни в одном из примеров.</span><span class="sxs-lookup"><span data-stu-id="e4be5-189">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="e4be5-190">Чтобы убедиться, что функция по-прежнему будет работать как раньше, повторите попытку исходных тестовых случаев.</span><span class="sxs-lookup"><span data-stu-id="e4be5-190">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="e4be5-191">Вы можете ограничить каррирование, поместив параметры в кортежи.</span><span class="sxs-lookup"><span data-stu-id="e4be5-191">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="e4be5-192">Дополнительные сведения см. в разделе «Шаблоны параметров» в [параметры и аргументы](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="e4be5-192">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="e4be5-193">В следующем примере неявное каррирование для написания краткая версия `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-193">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="e4be5-194">Сведения о том, как `makeGame` создает и возвращает `game` функции являются менее явными в этом формате, но можно проверить с помощью исходных тестовых случаев, результат равен.</span><span class="sxs-lookup"><span data-stu-id="e4be5-194">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="e4be5-195">Дополнительные сведения о каррировании. в разделе «Частичное приложения из аргументы» в [функции](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4be5-195">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="e4be5-196">Идентификатор и определение функции являются взаимозаменяемыми</span><span class="sxs-lookup"><span data-stu-id="e4be5-196">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="e4be5-197">Имя переменной `num` в предыдущих примерах имеет значение целого числа 10, и не удивительно, где `num` является допустимым, 10 допустим также.</span><span class="sxs-lookup"><span data-stu-id="e4be5-197">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="e4be5-198">То же самое справедливо для идентификаторов функций и их значений: везде, где можно использовать имя функции, можно использовать лямбда-выражение, к которому он привязан.</span><span class="sxs-lookup"><span data-stu-id="e4be5-198">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="e4be5-199">В следующем примере определяется `Boolean` функция, вызываемая `isNegative`, а затем попеременно использует имя функции и определение функции.</span><span class="sxs-lookup"><span data-stu-id="e4be5-199">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="e4be5-200">Следующие три примера возвращают и отображают `False`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-200">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="e4be5-201">Чтобы смотреть дальнейшей, заменить значение, `applyIt` привязывается к `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="e4be5-201">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="e4be5-202">Функции являются значения первого класса в языке F #</span><span class="sxs-lookup"><span data-stu-id="e4be5-202">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="e4be5-203">В примерах в предыдущих разделах показано, что функции в F # удовлетворяют критерии для значений первого класса в языке F #:</span><span class="sxs-lookup"><span data-stu-id="e4be5-203">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="e4be5-204">Идентификатор можно привязать к определению функции.</span><span class="sxs-lookup"><span data-stu-id="e4be5-204">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="e4be5-205">Функцию можно хранить в структуре данных.</span><span class="sxs-lookup"><span data-stu-id="e4be5-205">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="e4be5-206">Функцию можно передать в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="e4be5-206">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="e4be5-207">Функция может возвращать в качестве значения вызова функции.</span><span class="sxs-lookup"><span data-stu-id="e4be5-207">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="e4be5-208">Дополнительные сведения о F # см. в разделе [Справочник по языку F #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4be5-208">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="e4be5-209">Пример</span><span class="sxs-lookup"><span data-stu-id="e4be5-209">Example</span></span>

### <a name="description"></a><span data-ttu-id="e4be5-210">Описание</span><span class="sxs-lookup"><span data-stu-id="e4be5-210">Description</span></span>

<span data-ttu-id="e4be5-211">Следующий код содержит все примеры в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="e4be5-211">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="e4be5-212">Код</span><span class="sxs-lookup"><span data-stu-id="e4be5-212">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="e4be5-213">См. также</span><span class="sxs-lookup"><span data-stu-id="e4be5-213">See Also</span></span>

[<span data-ttu-id="e4be5-214">Списки</span><span class="sxs-lookup"><span data-stu-id="e4be5-214">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="e4be5-215">Кортежи</span><span class="sxs-lookup"><span data-stu-id="e4be5-215">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="e4be5-216">Функции</span><span class="sxs-lookup"><span data-stu-id="e4be5-216">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="e4be5-217">`let`Привязки</span><span class="sxs-lookup"><span data-stu-id="e4be5-217">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="e4be5-218">Лямбда-выражения: `fun` ключевое слово</span><span class="sxs-lookup"><span data-stu-id="e4be5-218">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)