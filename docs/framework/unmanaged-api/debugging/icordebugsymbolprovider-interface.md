---
title: ICorDebugSymbolProvider, interface
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 25faad4f4bc67b57c339bc63d1a18ab4d275cd71
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379349"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider, interface
Fournit des méthodes pouvant être utilisées pour récupérer des informations sur les symboles de débogage.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAssemblyImageBytes, méthode](icordebugsymbolprovider-getassemblyimagebytes-method.md)|Lit les données d’un assembly fusionné pour une adresse virtuelle relative (RVA) donnée dans l’assembly fusionné.|  
|[GetAssemblyImageMetadata, méthode](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Retourne les métadonnées d'un assembly fusionné.|  
|[GetCodeRange, méthode](icordebugsymbolprovider-getcoderange-method.md)|Obtient l'adresse de début et la taille de la méthode pour une adresse virtuelle relative (RVA) donnée dans une méthode.|  
|[GetInstanceFieldSymbols, méthode](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Obtient les symboles de champ d'instance qui correspondent à une signature typespec.|  
|[GetMergedAssemblyRecords, méthode](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Obtient les enregistrements de symbole de tous les assemblys fusionnés.|  
|[GetMethodLocalSymbols, méthode](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Obtient les symboles locaux d'une méthode selon l'adresse virtuelle relative (RVA) de cette méthode.|  
|[GetMethodParameterSymbols, méthode](icordebugsymbolprovider-getmethodparametersymbols-method.md)|Obtient les symboles de paramètre d'une méthode en fonction de l'adresse virtuelle relative (RVA) de cette méthode.|  
|[GetMethodProps, méthode](icordebugsymbolprovider-getmethodprops-method.md)|Retourne des informations sur les propriétés de la méthode, telles que le jeton de métadonnées de la méthode et des informations sur ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans cette méthode.|  
|[GetObjectSize, méthode](icordebugsymbolprovider-getobjectsize-method.md)|Retourne la taille d'un objet en fonction de sa signature typespec.|  
|[GetStaticFieldSymbols, méthode](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Obtient les symboles de champ statique qui correspondent à une signature typespec.|  
|[GetTypeProps, méthode](icordebugsymbolprovider-gettypeprops-method.md)|Retourne des informations sur les propriétés d'un type, comme le nombre de signature de ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans une vtable.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
