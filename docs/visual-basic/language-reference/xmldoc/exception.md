---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346958"
---
# <a name="exception-visual-basic"></a>> d’exception \<(Visual Basic)
Spécifie les exceptions qui peuvent être levées.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Paramètres  
 `member`  
 Référence à une exception qui est disponible à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie. `member` doit apparaître entre guillemets doubles (" ").  
  
 `description`  
 Description.  
  
## <a name="remarks"></a>Notes  
 Utilisez la balise `<exception>` pour spécifier les exceptions qui peuvent être levées. Cette balise est appliquée à une définition de méthode.  
  
 Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la balise `<exception>` pour décrire une exception que la fonction `IntDivide` peut lever.  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
