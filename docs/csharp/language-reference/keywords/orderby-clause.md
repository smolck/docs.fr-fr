---
title: orderby, clause - Référence C#
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173573"
---
# <a name="orderby-clause-c-reference"></a>orderby, clause (Référence C#)

Dans une expression de requête, la clause `orderby` a pour effet de trier la séquence ou la sous-séquence (groupe) retournée par ordre croissant ou décroissant. Il est possible de spécifier plusieurs clés de façon à effectuer une ou plusieurs opérations de tri secondaire. Le tri est effectué par le comparateur par défaut du type de l’élément. L’ordre de tri par défaut est croissant. Vous pouvez aussi spécifier un comparateur personnalisé. Cependant, sa disponibilité est soumise à l’utilisation d’une syntaxe fondée sur une méthode. Pour plus d’informations, consultez [Tri des données](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a> Exemple

Dans l’exemple suivant, la première requête trie les mots par ordre alphabétique à partir de A, tandis que la deuxième requête trie les mêmes mots par ordre décroissant. (Le mot clé `ascending` est la valeur de tri par défaut et peut être omis.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a> Exemple

L’exemple suivant effectue un tri principal sur les noms des étudiants, puis un tri secondaire sur leurs prénoms.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Notes 

Au moment de la compilation, la clause `orderby` est traduite en appel à la méthode <xref:System.Linq.Enumerable.OrderBy%2A>. Les différentes clés présentes dans la clause `orderby` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.ThenBy%2A>.

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Mots-clés de requête (LINQ)](query-keywords.md)
- [LINQ en C#](../../linq/index.md)
- [group, clause](group-clause.md)
- [Requête intégrée linguistique (LINQ)](../../programming-guide/concepts/linq/index.md)
