---
title: 'Comment : récupérer des métadonnées et implémenter un service conforme'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 0a13d504b1c7c38ec13fee58c36913a75119271b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184857"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Comment : récupérer des métadonnées et implémenter un service conforme
Souvent, la personne qui conçoit et implémente des services n'est pas la même. Dans les environnements où l'interaction d'applications est importante, les contrats peuvent être conçus ou décrits en WSDL (Web Services Description Language) et un développeur doit implémenter un service qui se conforme au contrat fourni. Vous pouvez également migrer un service existant vers Windows Communication Foundation (WCF) mais préserver le format de fil. De plus, les contrats duplex requièrent que les appelants implémentent également un contrat de rappel.  
  
 Dans ces cas, vous devez utiliser [l’outil utilitaire De métadonnées De ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (ou un outil équivalent) pour générer une interface de contrat de service dans un langage géré que vous pouvez mettre en œuvre pour répondre aux exigences du contrat. En règle générale, [l’outil utilitaire De métadonnées de ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) est utilisé pour acquérir un contrat de service qui est utilisé avec une usine de canal ou un type de client WCF ainsi qu’avec un fichier de configuration client qui définit la liaison et l’adresse correctes. Pour utiliser le fichier de configuration généré, vous devez le remplacer par un fichier de configuration de service. Vous devrez peut-être aussi modifier le contrat de service.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Pour récupérer des données et implémenter un service conforme  
  
1. Utilisez [l’outil utilitaire De métadonnées de ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contre des fichiers de métadonnées ou un point de terminaison de métadonnées pour générer un fichier de code.  
  
2. Recherchez la portion du fichier de code de sortie qui contient l'interface souhaitée (s'il y en a plusieurs) marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>. L’exemple de code suivant montre les deux interfaces générées par [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). La première (`ISampleService`) est l'interface de contrat de service que vous implémentez pour créer un service conforme. La seconde (`ISampleServiceChannel`) est une interface d'assistance destinée au client qui étend à la fois l'interface de contrat de service et <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>, et qui est utilisée dans une application cliente.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. Si WSDL ne spécifie pas d'action de réponse pour toutes les opérations, les contrats d'opération générés peuvent avoir la propriété <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> définie avec le caractère générique (*). Supprimez ce paramètre de propriété. Sinon, lorsque vous implémentez les métadonnées de contrat de service, celles-ci ne peuvent pas être exportées pour ces opérations.  
  
4. Implémentez l'interface sur une classe et hébergez le service. Par exemple, voir [comment : Mettre en œuvre un contrat de service,](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)ou voir une mise en œuvre simple ci-dessous dans la section Exemple.  
  
5. Dans le fichier de configuration client généré par [l’outil utilitaire De métadonnées (Svcutil.exe) de ServiceModel,](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) modifiez la [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) section de configuration>client en une [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section de configuration>services. (Pour obtenir un exemple d'un fichier de configuration d'application cliente généré, consultez la section « Exemple » suivante.)  
  
6. Dans [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) la section>configuration des `name` services, créez un attribut dans la [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section de configuration>des services pour votre implémentation de service.  
  
7. Affectez à l'attribut `name` de service le nom de configuration pour votre implémentation de service.  
  
8. Ajoutez les éléments de configuration de point de terminaison qui utilisent le contrat de service implémenté à la section de configuration du service.  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant montre la majorité d’un fichier de code généré par l’exécution [de l’outil utilitaire De métadonnées De ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contre les fichiers de métadonnées.  
  
 L'exemple de code suivant montre :  
  
- L’interface de contrat de service qui, lorsqu’elle est implémentée, se conforme aux exigences de contrat (`ISampleService`).  
  
- L'interface d'assistance destinée au client qui étend à la fois l'interface de contrat de service et <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>, et doit être utilisée dans une application cliente `ISampleServiceChannel`.  
  
- La classe d'assistance qui étend <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> et doit être utilisée dans une application cliente (`SampleServiceClient`).  
  
- Le fichier de configuration généré à partir du service.  
  
- L'implémentation d'un service `ISampleService` simple.  
  
- Conversion du fichier de configuration côté client vers une version côté service.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Voir aussi

- [Outil Service Model Metadata Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
