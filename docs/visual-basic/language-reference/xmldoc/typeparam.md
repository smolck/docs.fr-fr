---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 00cb62827381146c172e0d15a2c64b167c21f025
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352187"
---
# <a name="typeparam-visual-basic"></a>> \<typeparam (Visual Basic)
Définit un nom de paramètre de type et une description.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Paramètres  
 `name`  
 Nom du paramètre de type. Mettez le nom entre guillemets doubles (" ").  
  
 `description`  
 Description du paramètre de type.  
  
## <a name="remarks"></a>Notes  
 Utilisez la balise `<typeparam>` dans le commentaire pour un type générique ou une déclaration de membre générique pour décrire l’un des paramètres de type.  
  
 Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la balise `<typeparam>` pour décrire le paramètre `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
