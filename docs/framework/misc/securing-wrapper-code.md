---
title: Sécurisation du code wrapper
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
ms.openlocfilehash: 3d38a4d4fd33798cf5987f5ce67305725ad9daec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399909"
---
# <a name="securing-wrapper-code"></a>Sécurisation du code wrapper
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Le code wrapper, en particulier quand le wrapper est d'un niveau de confiance supérieur au code qui l'utilise, peut faire apparaître un ensemble unique de failles en matière de sécurité. Toutes les opérations effectuées au nom d'un appelant, où les autorisations limitées de l'appelant ne sont pas incluses dans la vérification de sécurité appropriée, constituent une faille potentielle exploitable.  
  
 N'autorisez jamais une opération par l'intermédiaire du wrapper que l'appelant ne peut pas effectuer lui-même. Toute opération impliquant une vérification de sécurité limitée représente un danger particulier contrairement à l'obligation d'effectuer un parcours de pile complet. Dans le cadre de vérifications de niveau unique, l'interposition du code wrapper entre l'appelant réel et l'élément d'API dont il est question peut amener facilement la vérification de sécurité à aboutir quand elle ne le devrait pas, ce qui affaiblit la sécurité.  
  
## <a name="delegates"></a>Délégués  
 La sécurité de délégué diffère selon les versions du .NET Framework.  Cette section décrit les différents comportements de délégué et les considérations sur la sécurité associées.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Dans les versions 1.0 et 1.1 du .NET Framework  
 Les versions 1.0 et 1.1 du .NET Framework exécutent les actions de sécurité suivantes sur un créateur de délégués et un appelant de délégués.  
  
- Quand un délégué est créé, des demandes de liaison de sécurité sur la méthode cible du délégué sont exécutées sur le jeu d'autorisations du créateur de délégués.  Si la satisfaction de l'action de sécurité échoue, une <xref:System.Security.SecurityException> est levée.  
  
- Quand le délégué est appelé, toutes les demandes de sécurité existantes sur l'appelant de délégués sont exécutées.  
  
 Chaque fois que votre code prend un <xref:System.Delegate> à partir de code d'un niveau de confiance moindre et susceptible de l'appeler, veillez à ne pas permettre au code d'un niveau de confiance moindre d'élargir ses autorisations. Si vous prenez un délégué et que vous l'utilisez ultérieurement, le code qui a créé le délégué ne se trouve pas dans la pile des appels et ses autorisations ne seront pas testées si le code dans ou sous le délégué tente une opération protégée. Si votre code et le code de l’appelant disposent de privilèges supérieurs à ceux du créateur, ce dernier peut gérer le chemin d’appel sans faire partie de la pile des appels.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Dans la version 2.0 et les versions ultérieures du cadre .NET  
 Contrairement aux versions précédentes, la version 2.0 et les versions ultérieures du cadre .NET effectue une action de sécurité contre le créateur délégué lorsque le délégué est créé et appelé.  
  
- Quand un délégué est créé, des demandes de liaison de sécurité sur la méthode cible du délégué sont exécutées sur le jeu d'autorisations du créateur de délégués.  Si la satisfaction de l'action de sécurité échoue, une <xref:System.Security.SecurityException> est levée.  
  
- Le jeu d'autorisations du créateur de délégués est également capturé au cours de la création du délégué et stocké avec celui-ci.  
  
- Quand le délégué est appelé, le jeu d'autorisations capturé du créateur de délégués est d'abord évalué par rapport à toutes les demandes dans le contexte actuel, si le créateur et l'appelant de délégués appartiennent à des assemblys différents.  Ensuite, toutes les demandes de sécurité existantes sur l'appelant de délégués sont exécutées.  
  
## <a name="link-demands-and-wrappers"></a>Demandes de liaison et wrappers  
 Un cas de protection particulier avec des demandes de liaison a fait l'objet d'une consolidation dans l'infrastructure de sécurité, mais il représente toujours une source de failles possibles dans votre code.  
  
 Si un code entièrement fiable appelle une propriété, un événement ou une méthode protégée par un [LinkDemand,](link-demands.md)l’appel réussit si le contrôle d’autorisation **LinkDemand** pour l’appelant est satisfait. En outre, si le code entièrement fiable expose une classe qui prend le nom d’une propriété et appelle son accesseur **obtenir** en utilisant la réflexion, cet appel à **l’accesseur obtenir** réussit même si le code utilisateur n’a pas le droit d’accéder à cette propriété. C’est parce que le **LinkDemand** vérifie seulement l’appelant immédiat, qui est le code entièrement fiable. Essentiellement, le code d'un niveau de confiance suffisant effectue un appel privilégié pour le compte du code utilisateur sans s'assurer que celui-ci a le droit d'effectuer cet appel.  
  
 Pour aider à prévenir de tels trous de sécurité, le runtime langue commune étend le contrôle dans une demande complète de pile-marche sur n’importe quel appel indirect à une méthode, constructeur, propriété, ou un événement protégé par un **LinkDemand**. Cette protection entraîne des coûts de performance et change la sémantique de la vérification de sécurité ; la demande de parcours de pile complet risque d'échouer là où la vérification de niveau unique plus rapide aurait réussi.  
  
## <a name="assembly-loading-wrappers"></a>Wrappers chargeant des assemblys  
 Plusieurs méthodes utilisées pour charger du code managé, y compris <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, chargent des assemblys avec la preuve de l'appelant. Si vous encapsulez une de ces méthodes, le système de sécurité peut utiliser l'octroi d'autorisation de votre code à la place des autorisations de l'appelant à votre wrapper afin de charger les assemblys. Vous ne devez pas permettre au code d'un niveau de confiance moindre de charger du code dont les autorisations accordées sont supérieures à celles de l'appelant à votre wrapper.  
  
 Tout code de confiance totale ou dont le niveau de confiance est nettement supérieur à un appelant potentiel (y compris un appelant avec des autorisations au niveau d'Internet) risque d'affaiblir la sécurité dans ce contexte. Si votre code a une méthode publique qui prend un tableau d’or et le transmet à **Assembly.Load**, créant ainsi un assemblage au nom de l’appelant, il pourrait briser la sécurité.  
  
 Ce problème s'applique aux éléments d'API suivants :  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Demand et LinkDemand  
 La sécurité déclarative propose deux types de vérification de sécurité similaires, mais qui effectuent des vérifications très différentes. Vous devez connaître les deux formes, car un mauvais choix pourrait nuire aux performances et à la sécurité.  
  
 La sécurité déclarative propose les vérifications de sécurité suivantes :  
  
- <xref:System.Security.Permissions.SecurityAction.Demand> spécifie le parcours de pile de sécurité d'accès du code. Tous les appelants sur la pile doivent avoir l'autorisation ou l'identité spécifiée pour passer. **La demande** se produit sur chaque appel parce que la pile peut contenir différents appelants. Si vous appelez une méthode de façon répétée, cette vérification de sécurité se produit à chaque fois. **La demande** est une bonne protection contre les attaques de leurre; code non autorisé essayant de le passer sera détecté.  
  
- [LinkDemand](link-demands.md) se produit à l’heure de compilation juste-à-temps (JIT) et ne vérifie que l’appelant immédiat. Cette vérification de sécurité ne vérifie pas l'appelant de l'appelant. Une fois cette vérification effectuée, il n'y a pas de charge de sécurité supplémentaire, quel que soit le nombre d'appels effectués par l'appelant. Cependant, il n'y a pas non plus de protection contre les attaques malveillantes. Avec **LinkDemand**, tout code qui passe le test et peut référencer votre code peut potentiellement briser la sécurité en permettant au code malveillant d’appeler à l’aide du code autorisé. Par conséquent, n’utilisez pas **LinkDemand** à moins que toutes les faiblesses possibles puissent être soigneusement évitées.  
  
    > [!NOTE]
    > Dans le cadre .NET 4, les <xref:System.Security.SecurityCriticalAttribute> demandes <xref:System.Security.SecurityRuleSet.Level2> de liaison ont été remplacées par l’attribut dans les assemblées. Il <xref:System.Security.SecurityCriticalAttribute> s’agit d’une demande de lien pour la pleine confiance; cependant, elle affecte également les règles d’héritage. Pour plus d’informations sur cette modification, voir [Code Sécurité-Transparent, Niveau 2](security-transparent-code-level-2.md).  
  
 Les précautions supplémentaires requises lors de l’utilisation **de LinkDemand** doivent être programmées individuellement; le système de sécurité peut aider à l’application de la loi. La moindre erreur fait apparaître une défaillance en matière de sécurité. Tout le code autorisé qui utilise votre code doit prendre en charge l'implémentation de la sécurité supplémentaire en effectuant les opérations suivantes :  
  
- Limiter l'accès du code appelant à la classe ou à l'assembly.  
  
- Placer les mêmes vérifications de sécurité sur le code appelant que celles figurant dans le code appelé et forcer ses appelants à effectuer les vérifications. Par exemple, si vous écrivez du code qui appelle une <xref:System.Security.Permissions.SecurityPermission> méthode <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> qui est protégée par un **LinkDemand** pour le drapeau spécifié, votre méthode doit également faire un **LinkDemand** (ou **demande**, qui est plus forte) pour cette autorisation. L’exception est si votre code utilise la méthode **LinkDemand-protégé**d’une manière limitée que vous décidez est sûr, étant donné d’autres mécanismes de protection de sécurité (tels que les demandes) dans votre code. Dans ce cas exceptionnel, l'appelant prend la responsabilité d'affaiblir la protection de la sécurité sur le code sous-jacent.  
  
- Veiller à ce que les appelants de votre code ne puissent pas tromper celui-ci et lui faire appeler le code protégé de leur part. En d'autres termes, les appelants ne peuvent pas forcer le code autorisé à passer des paramètres spécifiques au code protégé ou pour obtenir de ce dernier des résultats.  
  
### <a name="interfaces-and-link-demands"></a>Interfaces et demandes de liaison  
 Si une méthode, une propriété ou un événement virtuel avec **LinkDemand** remplace une méthode de classe de base, la méthode de classe de base doit également avoir le même **LinkDemand** pour la méthode dépassée afin d’être efficace. Il est possible pour le code nuisible d'effectuer un cast en type de base en retour et d'appeler la méthode de la classe de base. Notez également que les demandes de liaison peuvent être ajoutées implicitement aux assemblys qui n'ont pas l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de niveau assembly.  
  
 Il est recommandé de protéger les implémentations des méthodes avec des demandes de liaison quand des méthodes d'interface possèdent également des demandes de liaison. Notez les informations suivantes concernant l'utilisation de demandes de liaison avec des interfaces :  
  
- Si vous placez un **LinkDemand** sur une méthode publique d’une classe qui implémente une méthode d’interface, le **LinkDemand** ne sera pas appliqué si vous lancez ensuite à l’interface et appelez la méthode. Dans ce cas, parce que vous avez lié contre l’interface, seul le **LinkDemand** sur l’interface est honoré.  
  
 Passez en revue les éléments suivants en examinant les questions de sécurité :  
  
- Explicitez les demandes de liaison sur des méthodes d'interface. Veillez à ce que ces demandes de liaison offrent la protection attendue. Déterminez si du code nuisible peut utiliser un cast pour contourner les demandes de liaison comme décrit précédemment.  
  
- Méthodes virtuelles avec demandes de liaison appliquées.  
  
- Types et interfaces qu'ils implémentent. Ceux-ci doivent utiliser les demandes de liaison de manière cohérente.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
