---
title: '#If...Then...#Else, directives'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 40e93b718241c9819e3c0fd84595e76eb0c86472
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343811"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else, directives

Compile conditionnellement les blocs sélectionnés de Visual Basic code.

## <a name="syntax"></a>Syntaxe

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a>Composants

`expression`  
Obligatoire pour les instructions `#If` et `#ElseIf`, facultatives ailleurs. Toute expression, composée exclusivement d’une ou de plusieurs constantes de compilateur conditionnelles, de littéraux et d’opérateurs, qui prend la valeur `True` ou `False`.

`statements`  
Requis pour `#If` bloc d’instructions, facultatif ailleurs. Visual Basic des lignes de programme ou des directives de compilateur compilées si l’expression associée prend la valeur `True`.

`#End If`  
Termine le bloc d’instructions `#If`.

## <a name="remarks"></a>Notes

Sur la surface, le comportement des directives `#If...Then...#Else` est identique à celui des instructions `If...Then...Else`. Toutefois, les directives `#If...Then...#Else` évaluent ce qui est compilé par le compilateur, tandis que les instructions `If...Then...Else` évaluent des conditions au moment de l’exécution.

La compilation conditionnelle est généralement utilisée pour compiler le même programme pour différentes plateformes. Il est également utilisé pour empêcher le débogage du code d’apparaître dans un fichier exécutable. Le code exclu pendant la compilation conditionnelle est complètement omis du fichier exécutable final. il n’a donc aucun effet sur la taille ou les performances.

Quel que soit le résultat de l’évaluation, toutes les expressions sont évaluées à l’aide de `Option Compare Binary`. L’instruction `Option Compare` n’affecte pas les expressions dans les instructions `#If` et `#ElseIf`.

> [!NOTE]
> Il n’existe pas de formulaire à ligne unique des directives `#If`, `#Else`, `#ElseIf`et `#End If`. Aucun autre code ne peut apparaître sur la même ligne que les directives.

Les instructions contenues dans un bloc de compilation conditionnelle doivent être des instructions logiques complètes. Par exemple, vous ne pouvez pas compiler de façon conditionnelle uniquement les attributs d’une fonction, mais vous pouvez déclarer la fonction de manière conditionnelle avec ses attributs :

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a>Exemple

Cet exemple utilise la construction `#If...Then...#Else` pour déterminer s’il faut compiler certaines instructions.

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>Voir aussi

- [#Const (directive)](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
