---
title: <uri>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697436"
---
# <a name="uri-element-uri-settings"></a>\<URI >, élément (paramètres d’URI)
Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<uri >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributes  
 Aucune.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[idn](idn-element-uri-settings.md)|Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.|  
|[iriParsing](iriparsing-element-uri-settings.md)|Spécifie si l’analyse IRI (International Resource Identifier) est appliquée à <xref:System.Uri> et si les règles d’analyse IRI doivent être appliquées.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[configuration](../configuration-element.md)|Contient les paramètres de tous les espaces de noms.|  
  
## <a name="remarks"></a>Remarques  
 L’élément `uri` contient des paramètres pour les membres de la classe <xref:System.Uri> utilisée par les classes de l’espace de noms <xref:System.Net>. Les paramètres configurent la prise en charge des IRI et des IDN.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour prendre en charge l’analyse des IRI et les noms IDN. L’exemple efface également tous les paramètres de schéma, puis ajoute la prise en charge pour ne pas échapper les délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.  
  
### <a name="code"></a>Code  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres réseau](index.md)
