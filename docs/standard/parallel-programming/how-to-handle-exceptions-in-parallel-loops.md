---
title: 'Comment : gérer des exceptions dans des boucles parallèles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 5d108937e6ab2483cd1633d4b398c1e250f5c098
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453011"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Comment : gérer des exceptions dans des boucles parallèles
Les surcharges <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ne possèdent pas de mécanisme permettant de gérer les exceptions. À cet égard, `for` ils `foreach` ressemblent`For` à `For Each` des boucles régulières et (et dans Visual Basic); une exception non manipulée provoque la fin de la boucle dès que toutes les itérations en cours d’exécution se terminent.
  
 Quand vous ajoutez votre propre logique de gestion des exceptions à des boucles parallèles, gérez le cas dans lequel de telles exceptions peuvent être levées simultanément sur plusieurs threads et le cas dans lequel une exception levée sur un thread provoque la levée d'une autre exception sur un autre thread. Vous pouvez gérer les deux cas en encapsulant toutes les exceptions de la boucle dans un <xref:System.AggregateException?displayProperty=nameWithType>. L'exemple suivant montre une méthode possible.  
  
> [!NOTE]
> Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans l'exemple ci-dessous. Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.  
  
## <a name="example"></a> Exemple  
 Dans cet exemple, toutes les exceptions sont interceptées, puis encapsulées dans une <xref:System.AggregateException?displayProperty=nameWithType> qui est ensuite levée. L'appelant peut décider des exceptions à gérer.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Voir aussi

- [Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
