---
title: Références et l'instruction Imports
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 31b4fe001f2b8a62ac30488053c57cd186020421
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347276"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Références et l'instruction Imports (Visual Basic)
Vous pouvez rendre des objets externes disponibles pour votre projet en sélectionnant la commande **Ajouter une référence** dans le menu **projet** . Les références dans Visual Basic peuvent pointer vers des assemblys, comme les bibliothèques de types, mais contiennent davantage d’informations.  
  
## <a name="the-imports-statement"></a>Instruction Imports  
 Les assemblys incluent un ou plusieurs espaces de noms. Lorsque vous ajoutez une référence à un assembly, vous pouvez également ajouter une instruction `Imports` à un module qui contrôle la visibilité des espaces de noms de cet assembly dans le module. L’instruction `Imports` fournit un contexte d’étendue qui vous permet d’utiliser uniquement la partie de l’espace de noms nécessaire pour fournir une référence unique.  
  
 L’instruction `Imports` a la syntaxe suivante :  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` fait référence à un nom abrégé que vous pouvez utiliser dans le code pour faire référence à un espace de noms importé. `Namespace` est un espace de noms disponible via une référence de projet, par le biais d’une définition dans le projet ou par le biais d’une instruction `Imports` précédente.  
  
 Un module peut contenir un nombre quelconque d’instructions `Imports`. Ils doivent apparaître après les instructions `Option`, le cas échéant, mais avant tout autre code.  
  
> [!NOTE]
> Ne confondez pas les références de projet avec l’instruction `Imports` ou l’instruction `Declare`. Les références de projet rendent des objets externes, tels que des objets dans les assemblys, accessibles aux projets Visual Basic. L’instruction `Imports` est utilisée pour simplifier l’accès aux références de projet, mais ne fournit pas l’accès à ces objets. L’instruction `Declare` permet de déclarer une référence à une procédure externe dans une bibliothèque de liens dynamiques (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Utilisation d’alias avec l’instruction Imports  
 Grâce à l’instruction `Imports`, il est plus facile d’accéder aux méthodes des classes en éliminant le besoin de taper explicitement les noms complets des références. Les alias vous permettent d’assigner un nom plus convivial à une seule partie d’un espace de noms. Par exemple, la séquence de retour chariot/saut de ligne qui provoque l’affichage d’une seule partie du texte sur plusieurs lignes fait partie du module <xref:Microsoft.VisualBasic.ControlChars> dans l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=nameWithType>. Pour utiliser cette constante dans un programme sans alias, vous devez taper le code suivant :  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports` instructions doivent toujours être les premières lignes qui suivent immédiatement les instructions `Option` dans un module. Le fragment de code suivant montre comment importer et assigner un alias au module <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> :  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 Les futures références à cet espace de noms peuvent être beaucoup plus courtes :  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 Si une instruction `Imports` n’inclut pas de nom d’alias, les éléments définis dans l’espace de noms importé peuvent être utilisés dans le module sans qualification. Si le nom d’alias est spécifié, il doit être utilisé en tant que qualificateur pour les noms contenus dans cet espace de noms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Espaces de noms dans Visual Basic](namespaces.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Imports (instruction) (espace de noms et type .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
