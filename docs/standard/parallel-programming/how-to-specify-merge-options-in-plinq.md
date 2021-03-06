---
title: 'Comment : spécifier des options de fusion en PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: e98ede3664a8815c60a490239a789c69fa557895
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588562"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Comment : spécifier des options de fusion en PLINQ
Cet exemple montre comment spécifier les options de fusion qui seront appliquées à tous les opérateurs suivants dans une requête PLINQ. Il n’est pas nécessaire de définir explicitement les options de fusion, mais cela peut améliorer les performances. Pour plus d’informations sur les options de fusion, consultez [Options de fusion en PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
> Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le comportement des options de fusion dans un scénario de base qui a une source non ordonnée et qui applique une fonction coûteuse à chaque élément.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 Dans les cas où l’option <xref:System.Linq.ParallelMergeOptions.AutoBuffered> entraînerait une latence indésirable avant la transmission du premier élément, essayez l’option <xref:System.Linq.ParallelMergeOptions.NotBuffered> pour transmettre des éléments de résultat plus rapidement et plus facilement.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelMergeOptions>
- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
