---
title: Littéraux de commentaires XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349397"
---
# <a name="xml-comment-literal-visual-basic"></a>Littéraux de commentaires XML (Visual Basic)
Littéral représentant un objet <xref:System.Xml.Linq.XComment>.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`<!--`|Requis. Indique le début du commentaire XML.|  
|`content`|Requis. Texte à afficher dans le commentaire XML. Ne peut pas contenir une série de deux traits d’Union (--) ou se terminer par un trait d’Union adjacent à la balise de fermeture.|  
|`-->`|Requis. Désigne la fin du commentaire XML.|  
  
## <a name="return-value"></a>Valeur de retour  
 Objet <xref:System.Xml.Linq.XComment>.  
  
## <a name="remarks"></a>Notes  
 Les littéraux de commentaire XML ne contiennent pas de contenu de document ; elles contiennent des informations sur le document. La section de commentaire XML se termine par la séquence « --> ». Cela implique les points suivants :  
  
- Vous ne pouvez pas utiliser une expression incorporée dans un littéral de commentaire XML, car les délimiteurs d’expressions incorporées sont du contenu de commentaire XML valide.  
  
- Les sections de commentaires XML ne peuvent pas être imbriquées, car `content` ne peut pas contenir la valeur « --> ».  
  
 Vous pouvez assigner un littéral de commentaire XML à une variable, ou vous pouvez l’inclure dans un littéral d’élément XML.  
  
> [!NOTE]
> Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne. Cette fonctionnalité vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.  
  
 Le compilateur Visual Basic convertit le littéral de commentaire XML en un appel au constructeur <xref:System.Xml.Linq.XComment.%23ctor%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un commentaire XML qui contient le texte « This is a comments ».  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XComment>
- [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
