---
title: ICorDebugValue3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 9f521eb942f37b8cf1d00bcc672071a69692b876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396650"
---
# <a name="icordebugvalue3-interface"></a>ICorDebugValue3, interface
Étend les interfaces « ICorDebugValue » et « ICorDebugValue2 » pour assurer la prise en charge des tableaux d’une taille supérieure à 2 Go.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetSize64, méthode](icordebugvalue3-getsize64-method.md)|Obtient la taille, en octets, de cet `ICorDebugValue3` objet.|  
  
## <a name="remarks"></a>Notes  
 La méthode [ICorDebugValue ::](icordebugvalue3-getsize64-method.md) Desize retourne une taille d’objet comprise entre 0 et 2 147 483 647 octets. Dans le .NET Framework 4,5, la taille des tableaux peut dépasser 2 Go. L' `ICorDebugValue3` interface vous permet de déterminer la taille de ces tableaux.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
