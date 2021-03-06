---
title: Is, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349536"
---
# <a name="is-operator-visual-basic"></a>Is, opérateur (Visual Basic)
Compare deux variables de référence d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Requis. Toute valeur `Boolean`.  
  
 `object1`  
 Requis. N’importe quel nom de `Object`.  
  
 `object2`  
 Requis. N’importe quel nom de `Object`.  
  
## <a name="remarks"></a>Notes  
 L’opérateur `Is` détermine si deux références d’objet font référence au même objet. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `object2` font tous deux référence à la même instance d’objet, `result` est `True`. Si ce n’est pas le cas, `result` est `False`.  
  
 `Is` peut également être utilisé avec le mot clé `TypeOf` pour créer une expression `TypeOf`...`Is`, qui teste si une variable objet est compatible avec un type de données.  
  
> [!NOTE]
> Le mot clé `Is` est également utilisé dans la [sélection... Instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `Is` pour comparer des paires de références d’objets. Les résultats sont assignés à une valeur `Boolean` indiquant si les deux objets sont identiques.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Comme le montre l’exemple précédent, vous pouvez utiliser l’opérateur `Is` pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.  
  
## <a name="see-also"></a>Voir aussi

- [TypeOf (opérateur)](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Opérateurs de comparaison dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
