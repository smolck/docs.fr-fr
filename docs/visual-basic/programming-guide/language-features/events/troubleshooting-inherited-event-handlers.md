---
title: Dépannage des gestionnaires d’événements hérités
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345103"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Dépannage des gestionnaires d'événements hérités dans Visual Basic
Cette rubrique répertorie les problèmes courants qui surviennent avec les gestionnaires d’événements dans les composants hérités.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Le code dans le gestionnaire d’événements s’exécute deux fois pour chaque appel  
  
- Un gestionnaire d’événements hérité ne doit pas inclure une clause [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) . La méthode dans la classe de base est déjà associée à l’événement et est déclenchée en conséquence. Supprimez la clause `Handles` de la méthode héritée.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Si la méthode héritée n’a pas de mot clé `Handles`, vérifiez que votre code ne contient pas d' [instruction AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) supplémentaire ou de toute autre méthode qui gère le même événement.  
  
## <a name="see-also"></a>Voir aussi

- [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)
