---
title: <servicePointManager>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089127"
---
# <a name="servicepointmanager-element-network-settings"></a>\<élément servicePointManager > (paramètres réseau)
Configure les connexions aux ressources réseau.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**paramètres**](settings-element-network-settings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**servicePointManager >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`checkCertificateName`|Spécifie si le système doit vérifier que le nom du certificat correspond au nom d’hôte du serveur avant d’utiliser le certificat. La valeur par défaut est `true`.|  
|`checkCertificateRevocationList`|Spécifie si le système doit vérifier si le certificat a été révoqué avant d’utiliser le certificat. La valeur par défaut est `false`.|  
|`dnsRefreshTimeout`|Spécifie la durée de mise en cache des résolutions DNS (Domain Name Service) dans le cadre de l’option de tourniquet (Round Robin) DNS, en millisecondes. La valeur par défaut est 120 000 millisecondes (deux minutes).|  
|`enableDnsRoundRobin`|Spécifie si les résolutions DNS des noms d’hôtes avec plusieurs adresses IP (Internet Protocol) renvoient toutes les adresses ou uniquement la première. La valeur par défaut est `false`.|  
|`encryptionPolicy`|Spécifie la stratégie de chiffrement appliquée à une session SSL/TLS sur une instance de <xref:System.Net.ServicePointManager>. Les valeurs possibles sont équivalentes aux valeurs de l’énumération <xref:System.Net.Security.EncryptionPolicy>. L’utilisation de <xref:System.Security.Authentication.CipherAlgorithmType.Null> est requise lorsque la stratégie de chiffrement est définie sur `NoEncryption`. La valeur par défaut est `RequireEncryption`.|  
|`expect100Continue`|Spécifie si les méthodes de publication doivent s’attendre à recevoir une réponse `100-continue` du serveur. La valeur par défaut est `true`.|  
|`useNagleAlgorithm`|Spécifie si les connexions contrôlées par le gestionnaire de point de service utilisent l’algorithme Nagle. La valeur par défaut est `true`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[Réglages](settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Schéma des paramètres réseau](index.md)
