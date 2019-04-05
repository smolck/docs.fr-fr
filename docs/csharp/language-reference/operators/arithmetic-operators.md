---
title: Opérateurs arithmétiques - Informations de référence sur C#
description: Découvrez les opérateurs C# qui effectuent des opérations de multiplication, division, reste, addition et soustraction avec des types numériques.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 192acf6fea0c6014aaf092077f8deaa844dfd2ec
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633801"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="647ac-103">Opérateurs arithmétiques (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="647ac-103">Arithmetic operators (C# Reference)</span></span>

<span data-ttu-id="647ac-104">Les opérateurs suivants effectuent des opérations arithmétiques avec des types numériques :</span><span class="sxs-lookup"><span data-stu-id="647ac-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="647ac-105">Opérateurs unaires [`++` (incrément)](#increment-operator-), [`--` (décrément)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators) et [`-` (moins)](#unary-plus-and-minus-operators).</span><span class="sxs-lookup"><span data-stu-id="647ac-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators.</span></span>
- <span data-ttu-id="647ac-106">Opérateurs binaires [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (reste)](#remainder-operator-), [`+` (addition)](#addition-operator-) et [`-` (soustraction)](#subtraction-operator--).</span><span class="sxs-lookup"><span data-stu-id="647ac-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators.</span></span>

<span data-ttu-id="647ac-107">Ces opérateurs prennent en charge tous les types numériques [intégraux](../keywords/integral-types-table.md) et [à virgule flottante](../keywords/floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-107">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="647ac-108">Opérateur d’incrémentation ++</span><span class="sxs-lookup"><span data-stu-id="647ac-108">Increment operator ++</span></span>

<span data-ttu-id="647ac-109">L’opérateur d’incrémentation unaire `++` incrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="647ac-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="647ac-110">L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="647ac-111">L’opérateur d’incrémentation est pris en charge sous deux formes : l’opérateur d’incrémentation suffixé, `x++`, et l’opérateur d’incrémentation préfixé, `++x`.</span><span class="sxs-lookup"><span data-stu-id="647ac-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="647ac-112">Opérateur d'incrément suffixé</span><span class="sxs-lookup"><span data-stu-id="647ac-112">Postfix increment operator</span></span>

<span data-ttu-id="647ac-113">Le résultat de `x++` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="647ac-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="647ac-114">Opérateur d'incrémentation préfixé</span><span class="sxs-lookup"><span data-stu-id="647ac-114">Prefix increment operator</span></span>

<span data-ttu-id="647ac-115">Le résultat de `++x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="647ac-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="647ac-116">Opérateur de décrémentation --</span><span class="sxs-lookup"><span data-stu-id="647ac-116">Decrement operator --</span></span>

<span data-ttu-id="647ac-117">L’opérateur de décrémentation unaire `--` décrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="647ac-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="647ac-118">L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="647ac-119">L’opérateur de décrémentation est pris en charge sous deux formes : l’opérateur de décrémentation suffixé, `x--`, et l’opérateur de décrémentation préfixé, `--x`.</span><span class="sxs-lookup"><span data-stu-id="647ac-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="647ac-120">Opérateur de décrémentation suffixé</span><span class="sxs-lookup"><span data-stu-id="647ac-120">Postfix decrement operator</span></span>

<span data-ttu-id="647ac-121">Le résultat de `x--` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="647ac-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="647ac-122">Opérateur de décrémentation préfixé</span><span class="sxs-lookup"><span data-stu-id="647ac-122">Prefix decrement operator</span></span>

<span data-ttu-id="647ac-123">Le résultat de `--x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="647ac-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="647ac-124">Opérateurs plus et moins unaires</span><span class="sxs-lookup"><span data-stu-id="647ac-124">Unary plus and minus operators</span></span>

<span data-ttu-id="647ac-125">L’opérateur unaire `+` retourne la valeur de son opérande.</span><span class="sxs-lookup"><span data-stu-id="647ac-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="647ac-126">L’opérateur unaire `-` calcule la négation numérique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="647ac-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="647ac-127">L’opérateur unaire `-` ne prend pas en charge le type [ulong](../keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-127">The unary `-` operator doesn't support the [ulong](../keywords/ulong.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="647ac-128">Opérateur de multiplication \*</span><span class="sxs-lookup"><span data-stu-id="647ac-128">Multiplication operator \*</span></span>

<span data-ttu-id="647ac-129">L’opérateur de multiplication `*` calcule le produit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="647ac-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="647ac-130">L’opérateur unaire `*` est un [opérateur d’indirection de pointeur](multiplication-operator.md#pointer-indirection-operator).</span><span class="sxs-lookup"><span data-stu-id="647ac-130">The unary `*` operator is a [pointer indirection operator](multiplication-operator.md#pointer-indirection-operator).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="647ac-131">Opérateur de division /</span><span class="sxs-lookup"><span data-stu-id="647ac-131">Division operator /</span></span>

<span data-ttu-id="647ac-132">L’opérateur de division `/` divise son premier opérande par son deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="647ac-132">The division operator `/` divides its first operand by its second operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="647ac-133">Division d'entier</span><span class="sxs-lookup"><span data-stu-id="647ac-133">Integer division</span></span>

<span data-ttu-id="647ac-134">Pour les opérandes des types entiers, le résultat de l’opérateur `/` est de type entier et égal au quotient de deux opérandes arrondis vers le zéro :</span><span class="sxs-lookup"><span data-stu-id="647ac-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="647ac-135">Pour obtenir le quotient de deux opérandes comme un nombre à virgule flottante, utilisez le type `float`, `double` ou `decimal` :</span><span class="sxs-lookup"><span data-stu-id="647ac-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="647ac-136">Division à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="647ac-136">Floating-point division</span></span>

<span data-ttu-id="647ac-137">Pour les types `float`, `double` et `decimal`, le résultat de l’opérateur `/` est le quotient de deux opérandes :</span><span class="sxs-lookup"><span data-stu-id="647ac-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="647ac-138">Si l’un des opérandes est `decimal`, un autre opérande ne peut être `float` ni `double`, car ni `float` ni `double` ne sont implicitement convertibles en `decimal`.</span><span class="sxs-lookup"><span data-stu-id="647ac-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="647ac-139">Vous devez convertir explicitement l’opérande `float` ou `double` en type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="647ac-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="647ac-140">Pour plus d’informations sur les conversions implicites entre des types numériques, consultez [Tableau des conversions numériques implicites](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-140">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="647ac-141">Opérateur de reste %</span><span class="sxs-lookup"><span data-stu-id="647ac-141">Remainder operator %</span></span>

<span data-ttu-id="647ac-142">L’opérateur de reste `%` calcule le reste après avoir divisé son premier opérande par son second opérande.</span><span class="sxs-lookup"><span data-stu-id="647ac-142">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="647ac-143">Reste entier</span><span class="sxs-lookup"><span data-stu-id="647ac-143">Integer remainder</span></span>
  
<span data-ttu-id="647ac-144">Pour les opérandes des types entiers, le résultat de `a % b` est la valeur produite par `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="647ac-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="647ac-145">Le signe du reste non nul est le même que celui du premier opérande, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="647ac-145">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="647ac-146">Utilisez la méthode <xref:System.Math.DivRem%2A?displayProperty=nameWithType> pour calculer à la fois la division entière et les résultats du reste.</span><span class="sxs-lookup"><span data-stu-id="647ac-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="647ac-147">Reste à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="647ac-147">Floating-point remainder</span></span>

<span data-ttu-id="647ac-148">En ce qui concerne les opérandes `float` et `double`, le résultat de `x % y` pour le `x` et le `y` finis est la valeur `z` afin que</span><span class="sxs-lookup"><span data-stu-id="647ac-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="647ac-149">Le signe de `z`, s’il est différent de zéro, soit identique au signe de `x`.</span><span class="sxs-lookup"><span data-stu-id="647ac-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="647ac-150">La valeur absolue de `z` soit la valeur produite par `|x| - n * |y|`, où `n` représente le plus grand entier possible inférieur ou égal à `|x| / |y|`, et où `|x|` et `|y|` sont les valeurs absolues de `x` et `y`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="647ac-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="647ac-151">Cette méthode de calcul du reste est analogue à celle utilisée pour les opérandes entiers. Toutefois, elle ne suit pas la norme IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="647ac-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="647ac-152">Si l’opération de reste doit être conforme à la norme IEEE 754, utilisez la méthode <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="647ac-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="647ac-153">Pour plus d’informations sur le comportement de l’opérateur `%` avec des opérandes non finis, consultez la section [Opérateur de reste](~/_csharplang/spec/expressions.md#remainder-operator) dans la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="647ac-154">Pour les opérandes `decimal`, l’opérateur de reste `%` équivaut à l’[opérateur de reste](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) de type <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="647ac-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="647ac-155">L’exemple suivant illustre le comportement de l’opérateur de reste pour les opérandes à virgule flottante :</span><span class="sxs-lookup"><span data-stu-id="647ac-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="647ac-156">Opérateur d’addition +</span><span class="sxs-lookup"><span data-stu-id="647ac-156">Addition operator +</span></span>

<span data-ttu-id="647ac-157">L’opérateur d’addition `+` calcule la somme de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="647ac-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="647ac-158">Vous pouvez également utiliser l’opérateur `+` pour la concaténation de chaînes et la combinaison de délégués.</span><span class="sxs-lookup"><span data-stu-id="647ac-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="647ac-159">Pour plus d’informations, consultez l’article sur l’[opérateur `+`](addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-159">For more information, see the [`+` operator](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="647ac-160">Opérateur de soustraction -</span><span class="sxs-lookup"><span data-stu-id="647ac-160">Subtraction operator -</span></span>

<span data-ttu-id="647ac-161">L’opérateur de soustraction `-` soustrait son second opérande de son premier opérande :</span><span class="sxs-lookup"><span data-stu-id="647ac-161">The subtraction operator `-` subtracts its second operand from its first operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="647ac-162">Vous pouvez également utiliser l’opérateur `-` pour la suppression de délégués.</span><span class="sxs-lookup"><span data-stu-id="647ac-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="647ac-163">Pour plus d’informations, consultez l’article sur l’[opérateur `-`](subtraction-operator.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="647ac-164">Priorité des opérateurs et associativité</span><span class="sxs-lookup"><span data-stu-id="647ac-164">Operator precedence and associativity</span></span>

<span data-ttu-id="647ac-165">La liste suivante présente les opérateurs arithmétiques de la priorité la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="647ac-165">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="647ac-166">Opérateurs suffixés d’incrémentation `x++` et de décrémentation `x--`.</span><span class="sxs-lookup"><span data-stu-id="647ac-166">Postfix increment `x++` and decrement `x--` operators.</span></span>
- <span data-ttu-id="647ac-167">Opérateurs préfixés d’incrémentation `++x` et de décrémentation `--x` et opérateurs unaires `+` et `-`.</span><span class="sxs-lookup"><span data-stu-id="647ac-167">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators.</span></span>
- <span data-ttu-id="647ac-168">Opérateurs multiplicatifs `*`, `/` et `%`.</span><span class="sxs-lookup"><span data-stu-id="647ac-168">Multiplicative `*`, `/`, and `%` operators.</span></span>
- <span data-ttu-id="647ac-169">Opérateurs additifs `+` et `-`.</span><span class="sxs-lookup"><span data-stu-id="647ac-169">Additive `+` and `-` operators.</span></span>

<span data-ttu-id="647ac-170">Les opérateurs arithmétiques binaires sont associatifs sur leur gauche.</span><span class="sxs-lookup"><span data-stu-id="647ac-170">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="647ac-171">Autrement dit, les opérateurs de même niveau de priorité sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="647ac-171">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="647ac-172">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la priorité et l’associativité de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="647ac-172">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="647ac-173">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-173">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="647ac-174">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="647ac-174">Compound assignment</span></span>

<span data-ttu-id="647ac-175">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="647ac-175">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="647ac-176">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="647ac-176">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="647ac-177">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="647ac-177">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="647ac-178">L’exemple suivant illustre l’utilisation de l’assignation composée avec des opérateurs arithmétiques :</span><span class="sxs-lookup"><span data-stu-id="647ac-178">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="647ac-179">Vous utilisez également les opérateurs `+=` et `-=` pour vous abonner et annuler l’abonnement à des [événements](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-179">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="647ac-180">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="647ac-180">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="647ac-181">Débordement arithmétique et division par zéro</span><span class="sxs-lookup"><span data-stu-id="647ac-181">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="647ac-182">Quand le résultat d’une opération arithmétique n’est pas compris dans la plage de valeurs finies possibles du type numérique impliqué, le comportement d’un opérateur arithmétique varie selon le type de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="647ac-182">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="647ac-183">Débordement arithmétique entier</span><span class="sxs-lookup"><span data-stu-id="647ac-183">Integer arithmetic overflow</span></span>

<span data-ttu-id="647ac-184">La division d'un entier par zéro lève toujours une exception <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="647ac-184">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="647ac-185">En cas de débordement arithmétique entier, un contexte de vérification de débordement, qui peut être [vérifié ou non vérifié](../keywords/checked-and-unchecked.md), contrôle le comportement qui en résulte :</span><span class="sxs-lookup"><span data-stu-id="647ac-185">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="647ac-186">Dans un contexte vérifié, si le débordement se produit dans une expression constante, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="647ac-186">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="647ac-187">Sinon, un <xref:System.OverflowException> est levé quand l’opération est effectuée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="647ac-187">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="647ac-188">Dans un contexte non vérifié, le résultat est tronqué en supprimant tous les bits de poids fort qui ne tiennent pas dans le type destinataire.</span><span class="sxs-lookup"><span data-stu-id="647ac-188">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="647ac-189">Avec les instructions [vérifiées et non vérifiées](../keywords/checked-and-unchecked.md), vous pouvez utiliser les opérateurs `checked` et `unchecked` pour contrôler le contexte de vérification de débordement, dans lequel une expression est évaluée :</span><span class="sxs-lookup"><span data-stu-id="647ac-189">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="647ac-190">Par défaut, les opérations arithmétiques se produisent dans un contexte *unchecked*.</span><span class="sxs-lookup"><span data-stu-id="647ac-190">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="647ac-191">Débordement arithmétique à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="647ac-191">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="647ac-192">Les opérations arithmétiques avec les types `float` et `double` ne lèvent jamais d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="647ac-192">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="647ac-193">Le résultat des opérations arithmétiques avec ces types peut être une des valeurs spéciales qui représentent l’infini et non un nombre :</span><span class="sxs-lookup"><span data-stu-id="647ac-193">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="647ac-194">Pour les opérandes du type `decimal`, le débordement arithmétique lève toujours un <xref:System.OverflowException> et la division par zéro lève toujours un <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="647ac-194">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="647ac-195">Erreurs d’arrondi</span><span class="sxs-lookup"><span data-stu-id="647ac-195">Round-off errors</span></span>

<span data-ttu-id="647ac-196">En raison des limitations générales de la représentation à virgule flottante des nombres réels et de l’arithmétique à virgule flottante, des erreurs d’arrondi peuvent se produire dans les calculs avec les types à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="647ac-196">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="647ac-197">Autrement dit, le résultat d’une expression peut différer du résultat mathématique attendu.</span><span class="sxs-lookup"><span data-stu-id="647ac-197">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="647ac-198">L’exemple suivant illustre plusieurs cas de ce genre :</span><span class="sxs-lookup"><span data-stu-id="647ac-198">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="647ac-199">Pour plus d’informations, consultez les remarques dans les pages de référence [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks) ou [System.Decimal](/dotnet/api/system.decimal#remarks).</span><span class="sxs-lookup"><span data-stu-id="647ac-199">For more information, see remarks at [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="647ac-200">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="647ac-200">Operator overloadability</span></span>

<span data-ttu-id="647ac-201">Les types définis par l’utilisateur peuvent [surcharger](../keywords/operator.md) les opérateurs arithmétiques unaires (`++`, `--`, `+` et `-`) et binaires (`*`, `/`, `%`, `+` et `-`).</span><span class="sxs-lookup"><span data-stu-id="647ac-201">User-defined types can [overload](../keywords/operator.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="647ac-202">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="647ac-202">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="647ac-203">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="647ac-203">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="647ac-204">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="647ac-204">C# language specification</span></span>

<span data-ttu-id="647ac-205">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="647ac-205">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="647ac-206">Opérateurs suffixés d’incrémentation et de décrémentation</span><span class="sxs-lookup"><span data-stu-id="647ac-206">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="647ac-207">Opérateurs préfixés d’incrémentation et de décrémentation</span><span class="sxs-lookup"><span data-stu-id="647ac-207">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="647ac-208">Opérateur plus unaire</span><span class="sxs-lookup"><span data-stu-id="647ac-208">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="647ac-209">Opération moins unaire</span><span class="sxs-lookup"><span data-stu-id="647ac-209">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="647ac-210">Opérateur de multiplication</span><span class="sxs-lookup"><span data-stu-id="647ac-210">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="647ac-211">Opérateur de division</span><span class="sxs-lookup"><span data-stu-id="647ac-211">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="647ac-212">Opérateur de reste</span><span class="sxs-lookup"><span data-stu-id="647ac-212">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="647ac-213">Opérateur d’addition</span><span class="sxs-lookup"><span data-stu-id="647ac-213">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="647ac-214">Opérateur de soustraction</span><span class="sxs-lookup"><span data-stu-id="647ac-214">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="647ac-215">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="647ac-215">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="647ac-216">Opérateurs vérifiés et non vérifiés</span><span class="sxs-lookup"><span data-stu-id="647ac-216">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)

## <a name="see-also"></a><span data-ttu-id="647ac-217">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="647ac-217">See also</span></span>

- [<span data-ttu-id="647ac-218">Référence C#</span><span class="sxs-lookup"><span data-stu-id="647ac-218">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="647ac-219">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="647ac-219">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="647ac-220">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="647ac-220">C# Operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="647ac-221">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="647ac-221">Numerics in .NET</span></span>](../../../standard/numerics.md)