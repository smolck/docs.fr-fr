---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716649"
---
# <a name="-imports-visual-basic"></a>-Imports (Visual Basic)
Importe des espaces de noms à partir d’un assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`namespaceList`|Obligatoire. Liste délimitée par des virgules des espaces de noms à importer.|  
  
## <a name="remarks"></a>Notes  
 L' `-imports` option importe tout espace de noms défini dans l’ensemble actuel de fichiers sources ou à partir d’un assembly référencé.  
  
 Les membres d’un espace de noms `-imports` spécifié avec sont disponibles pour tous les fichiers de code source de la compilation. Utilisez l' [instruction Imports (espace de noms et type .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour utiliser un espace de noms dans un fichier de code source unique.  
  
|Pour définir-Imports dans l’environnement de développement intégré Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **références** .<br />3. Entrez le nom de l’espace de noms dans la zone en regard du bouton **Ajouter une importation utilisateur** .<br />4. cliquez sur le bouton **Ajouter une importation d’utilisateur** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile lorsque `-imports:system.globalization` est spécifié. Sans cela, la réussite de la compilation requiert `Imports System.Globalization` qu’une instruction soit incluse au début du fichier de code source, ou que la propriété soit qualifiée `System.Globalization.CultureInfo.CurrentCulture.Name`complète en tant que.

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Références et instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
