---
title: élément <security> de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738726"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a>\<> élément de sécurité de \<ws2007FederationHttpBinding >
Définit les paramètres de sécurité de l’élément [\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) .  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**WS2007FederationHttpBinding**](ws2007federationhttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< **\**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`mode`|Optionnel. Spécifie le type de sécurité appliqué. La valeur par défaut est `Message`. Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Attribut Mode  
  
|valeur|Description|  
|-----------|-----------------|  
|aucune.|Le message SOAP n'est pas sécurisé pendant le transfert.|  
|Message|L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP. Par défaut, le corps est chiffré et signé. Le service doit être configuré à l'aide d'un certificat. L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.|  
|TransportWithMessageCredential|L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS. Le service doit être configuré à l'aide d'un certificat. L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[message de \<](message-of-ws2007httpbinding.md)|Définit les paramètres de sécurité au niveau du message. Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[liaison de \<](bindings.md)|Définit toutes les fonctions de liaison du [\<WSDualHttpBinding](wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [Guide pratique pour créer une liaison WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Sélection d’un type d’informations d’identification](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [liaison de \<](bindings.md)
