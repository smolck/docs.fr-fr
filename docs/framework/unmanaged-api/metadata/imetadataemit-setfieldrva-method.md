---
title: IMetaDataEmit::SetFieldRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: d429995e41006798aee5f796150bedbd6ae87f6f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003866"
---
# <a name="imetadataemitsetfieldrva-method"></a>IMetaDataEmit::SetFieldRVA, méthode
Définit une valeur de variable globale pour l’adresse virtuelle relative du champ référencé par le jeton spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fd`  
 dans Jeton pour le champ cible.  
  
 `ulRVA`  
 dans Adresse d’un code ou d’une zone de données.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
