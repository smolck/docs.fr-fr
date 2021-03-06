---
title: JoinOpérations (C)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868003"
---
# <a name="join-operations-c"></a>Opérations de jointure (C#)

Une *jointure* de deux sources de données est l’association des objets d’une source de données aux objets qui partagent un attribut commun dans une autre source de données.  
  
 La jointure est une opération importante dans les requêtes qui ciblent les sources de données dont les relations ne peuvent pas être suivies directement. En programmation orientée objet, cela peut correspondre à une corrélation entre objets qui n'est pas modélisée, par exemple la direction vers l'arrière dans une relation à sens unique. Voici un exemple de relation à sens unique : une classe Customer a une propriété de type City, alors que la classe City n'a aucune propriété correspondant à une collection d'objets Customer. Si vous avez une liste d'objets City et si vous souhaitez rechercher tous les clients de chaque ville, vous pouvez recourir à une opération de jointure.  
  
 Les méthodes de jointure fournies dans le framework LINQ sont <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>. Ces méthodes effectuent des équijointures, qui sont des jointures associant deux sources de données en fonction de l’égalité de leurs clés. (À titre de comparaison, Les supports Transact-SQL rejoignent des opérateurs autres que les « égaux », par exemple l’opérateur « inférieur à ». En termes de <xref:System.Linq.Enumerable.Join%2A> base de données relationnelles, implémente une jointure intérieure, un type de jointure dans lequel seuls les objets qui ont une correspondance dans l’autre ensemble de données sont retournés. La méthode <xref:System.Linq.Enumerable.GroupJoin%2A> n’a aucun équivalent direct dans le contexte des bases de données relationnelles, mais elle implémente un sur-ensemble de jointures internes et de jointures externes gauches. Une jointure externe gauche est une jointure qui retourne chaque élément de la source de données (gauche), même si elle n’a pas d’éléments corrélés dans l’autre source de données.  
  
 L'illustration suivante présente une vue conceptuelle de deux ensembles, ainsi que leurs éléments inclus dans une jointure interne ou une jointure externe gauche.  
  
 ![Deux cercles se chevauchant montrant l’interne&#47;externe.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Joint deux séquences selon les fonctions de sélection de clé et extrait des paires de valeurs.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Joint deux séquences selon les fonctions de sélection de clé et regroupe les résultats correspondants pour chaque élément.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d’expression de requête
  
### Join  
  
L’exemple suivant `join … in … on … equals …` utilise la clause pour joindre deux séquences basées sur une valeur spécifique :
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

L’exemple suivant `join … in … on … equals … into …` utilise la clause pour joindre deux séquences basées sur une valeur spécifique et regroupe les correspondances résultantes pour chaque élément :
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [Types anonymes](../../classes-and-structs/anonymous-types.md)
- [Formuler des jointures et des requêtes de produit croisé](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [clause d’adhésion](../../../language-reference/keywords/join-clause.md)
- [Joinen utilisant des clés composites](../../../linq/join-by-using-composite-keys.md)
- [Comment joindre le contenu des fichiers différents (LINQ) (C)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Classer les résultats d’une clause join](../../../linq/order-the-results-of-a-join-clause.md)
- [Effectuer des opérations de jointure personnalisée](../../../linq/perform-custom-join-operations.md)
- [Effectuer des jointures groupées](../../../linq/perform-grouped-joins.md)
- [Effectuer des jointures intérieures](../../../linq/perform-inner-joins.md)
- [Effectuer des jointures externes gauches](../../../linq/perform-left-outer-joins.md)
- [Comment remplir les collections d’objets à partir de sources multiples (LINQ) (C)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
