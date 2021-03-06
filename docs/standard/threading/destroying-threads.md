---
title: Détruire des threads
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155930"
---
# <a name="destroying-threads"></a>Détruire des threads

Pour mettre fin à l’exécution du fil, vous utilisez généralement le [modèle d’annulation coopérative](cancellation-in-managed-threads.md). Parfois, il n’est pas possible d’arrêter un thread en coopération, car il exécute un code tiers non conçu pour l’annulation coopérative. La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode dans .NET Framework peut être utilisée pour mettre fin à un thread géré de force. Lorsque vous <xref:System.Threading.Thread.Abort%2A>appelez, le Common Language <xref:System.Threading.ThreadAbortException> Runtime jette un dans le thread cible, que le thread cible peut attraper. Pour plus d’informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. La <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> méthode n’est pas prise en charge dans .NET Core. Si vous avez besoin de mettre fin à l’exécution du code tiers <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>de force dans .NET Core, l’exécuter dans le processus séparé et l’utiliser .

> [!NOTE]
> Si un thread est en train d’exécuter du code non managé quand sa méthode <xref:System.Threading.Thread.Abort%2A> est appelée, le runtime le marque comme <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. L’exception est levée quand le thread retourne au code managé.  
  
 Une fois un thread annulé, il ne peut pas être redémarré.  
  
 La méthode <xref:System.Threading.Thread.Abort%2A> n’entraîne pas l’annulation immédiate du thread, car le thread cible peut intercepter l’exception <xref:System.Threading.ThreadAbortException> et exécuter arbitrairement des quantités de code dans un bloc `finally`. Vous pouvez appeler <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> si vous devez attendre que le thread se termine. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> est un appel bloquant qui ne retourne de résultats que quand le thread a réellement arrêté son exécution ou qu’un intervalle de délai d’attente facultatif a expiré. Le thread annulé pourrait appeler la méthode <xref:System.Threading.Thread.ResetAbort%2A> ou exécuter un traitement illimité dans un bloc `finally`. Par conséquent, si vous ne spécifiez pas de délai d’attente, l’attente pourrait ne jamais se terminer.  
  
 Les threads qui attendent suite à un appel à la méthode <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> peuvent être interrompus par d’autres threads qui appellent <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Gestion de ThreadAbortException  
 Si vous pensez que votre thread sera annulé, soit suite à un appel de votre propre code à <xref:System.Threading.Thread.Abort%2A>, soit suite au déchargement d’un domaine d’application dans lequel le thread est en cours d’exécution (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> utilise <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour arrêter des threads), votre thread doit gérer l’exception <xref:System.Threading.ThreadAbortException> et exécuter tout traitement final dans une clause `finally`, comme indiqué dans le code suivant.  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try
{  
    // Code that is executing when the thread is aborted.  
}
catch (ThreadAbortException ex)
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.
}  
// Do not put clean-up code here, because the exception
// is rethrown at the end of the Finally clause.  
```  
  
 Votre code de nettoyage doit se trouver dans la clause `catch` ou la clause `finally`, car une exception <xref:System.Threading.ThreadAbortException> est de nouveau levée par le système à la fin de la clause `finally`, ou à la fin de la clause `catch` s’il n’existe pas de clause `finally`.  
  
 Vous pouvez empêcher le système de lever une nouvelle exception en appelant la méthode <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>. Vous ne devez néanmoins le faire que si c’est votre propre code qui a provoqué l’exception <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)
