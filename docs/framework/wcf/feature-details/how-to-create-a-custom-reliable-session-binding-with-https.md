---
title: "Comment : créer une liaison de session fiable personnalisée à l'aide de HTTPS"
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 26466a97ae44e6852c189d0b72bdba1b93d86141
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141738"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Comment : créer une liaison de session fiable personnalisée à l'aide de HTTPS

Cette rubrique décrit l'utilisation de la sécurité de transport SSL (Secure Socket Layer) avec les sessions fiables. Pour utiliser une session fiable sur HTTPS, vous devez créer une liaison personnalisée qui utilise une session fiable et le transport HTTPS. Vous activez la session fiable de manière impérative en utilisant le code ou de façon déclarative dans le fichier de configuration. Cette procédure utilise les fichiers de configuration du client et du service pour activer la session fiable et l’élément [ **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) .

La partie clé de cette procédure est que le **point de terminaison\<** élément de configuration contient un attribut `bindingConfiguration` qui référence une configuration de liaison personnalisée nommée `reliableSessionOverHttps`. La [**liaison\<** ](../../configure-apps/file-schema/wcf/bindings.md) élément de configuration fait référence à ce nom pour spécifier qu’une session fiable et le transport HTTPS sont utilisés en incluant des éléments **\<reliableSession >** et **\<httpsTransport >** .

Pour obtenir la copie source de cet exemple, consultez [liaison personnalisée session fiable sur https](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Configurer le service avec une connexion CustomBinding pour utiliser une session fiable avec HTTPs

1. Définissez un contrat de service pour le type de service.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implémentez le contrat de service dans une classe de service. Notez que l’adresse ou les informations de liaison ne sont pas spécifiées dans l’implémentation du service. Vous n’êtes pas obligé d’écrire du code pour récupérer l’adresse ou les informations de liaison à partir du fichier de configuration.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Créez un fichier *Web. config* pour configurer un point de terminaison pour l' `CalculatorService` avec une liaison personnalisée nommée `reliableSessionOverHttps` qui utilise une session fiable et le transport HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Créez un fichier *service. svc* qui contient la ligne :

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. Placez le fichier *service. svc* dans votre répertoire virtuel Internet Information Services (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Configurer le client avec une connexion CustomBinding pour utiliser une session fiable avec HTTPs

1. Utilisez l' [outil ServiceModel Metadata Utility Tool (*Svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code à partir des métadonnées de service.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Le client généré contient l’interface `ICalculator` qui définit le contrat de service que l’implémentation du client doit satisfaire.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. L'application cliente générée contient également l'implémentation de `ClientCalculator`. Notez que les informations d’adresse et de liaison ne sont pas spécifiées dans l’implémentation du service. Vous n’êtes pas obligé d’écrire du code pour récupérer les informations d’adresse et de liaison à partir du fichier de configuration.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Configurez une liaison personnalisée nommée `reliableSessionOverHttps` pour utiliser le transport HTTPs et des sessions fiables.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Créez une instance `ClientCalculator` dans une application, puis appelez les opérations de service.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Compilez, puis exécutez le client.  

## <a name="net-framework-security"></a>sécurité du .NET Framework

Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec *Makecert. exe*, une alerte de sécurité s’affiche lorsque vous essayez d’accéder à une adresse https, telle que `https://localhost/servicemodelsamples/service.svc`, à partir de votre navigateur.

## <a name="see-also"></a>Voir aussi

- [Sessions fiables](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
