---
title: '>>=, opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351992"
---
# <a name="-operator-visual-basic"></a>> > =, opérateur (Visual Basic)
Effectue un décalage arithmétique vers la droite sur la valeur d’une variable ou d’une propriété et réassigne le résultat à la variable ou à la propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Requis. Variable ou propriété d’un type intégral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`ou `ULong`).  
  
 `amount`  
 Requis. Expression numérique d’un type de données qui s’étend à `Integer`.  
  
## <a name="remarks"></a>Notes  
 L’élément situé à gauche de l’opérateur `>>=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 L’opérateur `>>=` effectue d’abord un décalage arithmétique à droite sur la valeur de la variable ou de la propriété. L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Dans un décalage arithmétique vers la droite, les bits décalés au-delà de la position du bit le plus à droite sont ignorés, et le bit le plus à gauche est propagé dans les positions de bits libérées à gauche. Cela signifie que si `variableorproperty` a une valeur négative, les positions libérées sont définies sur un. Si `variableorproperty` est positif, ou si son type de données est un type non signé, les positions libérées sont définies à zéro.  
  
## <a name="overloading"></a>Surcharge  
 L' [opérateur > >](../../../visual-basic/language-reference/operators/right-shift-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. La surcharge de l’opérateur `>>` affecte le comportement de l’opérateur `>>=`. Si votre code utilise `>>=` sur une classe ou une structure qui surcharge `>>`, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `>>=` pour décaler le modèle binaire d’une variable `Integer` à droite de la valeur spécifiée et assigner le résultat à la variable.  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- [>>, opérateur](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Opérateurs de décalage de bits](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
