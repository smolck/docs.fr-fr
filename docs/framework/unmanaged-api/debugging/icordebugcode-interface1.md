---
title: ICorDebugCode, interface
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893471"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode, interface

Représente un segment de code MSIL ou de code natif.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](icordebugcode-createbreakpoint-method.md)|Crée un point d’arrêt à l’offset spécifié.|  
|[GetAddress, méthode](icordebugcode-getaddress-method.md)|Obtient l’adresse virtuelle relative (RVA) du segment de code que ce `ICorDebugCode` représente.|  
|[GetCode, méthode](icordebugcode-getcode-method.md)|Obtient tout le code pour la fonction spécifiée, mis en forme pour le code machine. Cette méthode a été dépréciée ; Utilisez [ICorDebugCode2 :: GetCodeChunks,](icordebugcode2-getcodechunks-method.md) à la place.|  
|[GetEnCRemapSequencePoints, méthode](icordebugcode-getencremapsequencepoints-method.md)|Non implémenté.|  
|[GetFunction, méthode](icordebugcode-getfunction-method.md)|Obtient le « ICorDebugFunction » associé à ce `ICorDebugCode`.|  
|[GetILToNativeMapping, méthode](icordebugcode-getiltonativemapping-method.md)|Obtient un tableau d’instances « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent les mappages des offsets MSIL aux offsets natifs.|  
|[GetSize, méthode](icordebugcode-getsize-method.md)|Obtient la taille, en octets, du code binaire représenté par ce `ICorDebugCode`.|  
|[GetVersionNumber, méthode](icordebugcode-getversionnumber-method.md)|Obtient le nombre de base 1 qui identifie la version du code que ce `ICorDebugCode` représente.|  
|[IsIL, méthode](icordebugcode-isil-method.md)|Obtient une valeur qui indique si ce `ICorDebugCode` est compilé en MSIL.|  
  
## <a name="remarks"></a>Notes   
 `ICorDebugCode`peut représenter le code MSIL ou le code natif. Un objet « ICorDebugFunction » qui représente le code MSIL peut avoir zéro ou un `ICorDebugCode` objet associé. Un objet « ICorDebugFunction » qui représente du code natif peut avoir un nombre `ICorDebugCode` quelconque d’objets associés.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugCode3, interface](icordebugcode3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
