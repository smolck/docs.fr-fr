---
title: ExportNestedTypeForwarder, méthode
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: cc81ccd1c754e3d34c54737f4560b4f81d5cc916
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438410"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder, méthode
Ajoute un redirecteur de type pour un type imbriqué à la table de types de l’assembly donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly à partir duquel effectuer l’exportation.  
  
 `FileToken`  
 Jeton de fichier ou ID d’assembly du fichier qui définit le type.  
  
 `TypeToken`  
 Jeton pour le type.  
  
 `ParentType`  
 Jeton de type parent.  
  
 `pszTypename`  
 Nom de type qualifié complet à exporter.  
  
 `dwFlags`  
 `ComType` indicateurs tels que `tdPublic` ou `tdNested`.  
  
 `pType`  
 Reçoit le jeton de type d’exportation. Cela est nécessaire uniquement pour l’émission de types imbriqués.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
