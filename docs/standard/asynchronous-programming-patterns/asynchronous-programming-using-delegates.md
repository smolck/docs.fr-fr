---
title: Programmation asynchrone à l'aide de délégués
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121742"
---
# <a name="asynchronous-programming-using-delegates"></a>Programmation asynchrone à l'aide de délégués
Les délégués permettent d’appeler une méthode synchrone de manière asynchrone. Lorsque vous appelez un délégué de manière synchrone, la méthode `Invoke` appelle la méthode cible directement sur le thread actuel. Si la méthode `BeginInvoke` est appelée, le common language runtime (CLR) met en file d’attente la demande et retourne immédiatement à l’appelant. La méthode cible est appelée de façon asynchrone sur un thread du pool de threads. Le thread d’origine, qui a envoyé la demande, est libre de continuer à s’exécuter en parallèle avec la méthode cible. Si une méthode de rappel a été spécifiée dans l’appel à la méthode `BeginInvoke`, la méthode de rappel est appelée lorsque la méthode cible se termine. Dans la méthode de rappel, la méthode `EndInvoke` obtient la valeur de retour et d’éventuels paramètres d’entrée/sortie ou de sortie uniquement. Si aucune méthode de rappel n’est spécifiée lors de l’appel à `BeginInvoke`, `EndInvoke` peut être appelé depuis le thread qui a appelé `BeginInvoke`.  
  
> [!IMPORTANT]
> Les compilateurs doivent émettre des classes déléguées avec les méthodes `Invoke`, `BeginInvoke` et `EndInvoke` à l’aide de la signature de délégué spécifiée par l’utilisateur. Les méthodes `BeginInvoke` et `EndInvoke` doivent être décorées comme étant natives. Étant donné que ces méthodes sont marquées comme étant natives, le CLR fournit automatiquement l’implémentation au moment du chargement de la classe. Le chargeur garantit qu’elles ne sont pas remplacées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Appel de méthodes synchrones de manière asynchrone](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Décrit l’utilisation de délégués pour effectuer des appels asynchrones à des méthodes ordinaires et fournit des exemples de code simples qui présentent les quatre façons d’attendre un appel asynchrone à retourner.  
  
## <a name="related-sections"></a>Sections connexes  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Décrit la programmation asynchrone avec le .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Delegate>
