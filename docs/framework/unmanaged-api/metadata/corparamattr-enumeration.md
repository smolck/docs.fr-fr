---
title: CorParamAttr, énumération
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: e8afcb972cab9757458c7032c3678d45c6418fac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007570"
---
# <a name="corparamattr-enumeration"></a>CorParamAttr, énumération
Contient des valeurs qui décrivent les métadonnées d'un paramètre de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pdIn`|Spécifie que le paramètre est passé dans l’appel de méthode.|  
|`pdOut`|Spécifie que le paramètre est passé à partir du retour de la méthode.|  
|`pdOptional`|Spécifie que le paramètre est facultatif.|  
|`pdReservedMask`|Réservé à un usage interne par la common language runtime.|  
|`pdHasDefault`|Spécifie que le paramètre a une valeur par défaut.|  
|`pdHasFieldMarshal`|Spécifie que le paramètre comporte des informations de marshaling.|  
|`pdUnused`|Inutilisé.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
