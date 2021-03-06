---
title: ICorPublishProcessEnum, interface
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421070"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum, interface
Sous-classe de l’interface [ICorPublishEnum](icorpublishenum-interface.md) qui fournit des méthodes pour parcourir une collection d’objets [ICorPublishProcess](icorpublishprocess-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icorpublishprocessenum-next-method.md)|Obtient le nombre d' `ICorPublishProcess` instances spécifié à partir de la collection, en commençant à la position actuelle.|  
  
## <a name="remarks"></a>Notes  
 L' `ICorPublishProcessEnum` interface implémente les méthodes de l’interface abstraite, [ICorPublishEnum](icorpublishenum-interface.md).  
  
 Une `ICorPublishProcessEnum` instance est créée par la méthode [ICorPublish :: EnumProcesses](icorpublish-enumprocesses-method.md) . Le parcours de la collection d' `ICorPublishProcess` objets est basé sur les critères de filtre spécifiés au moment de la création de l' `ICorPublishProcessEnum` instance.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [CorpubPublish (coclasse)](corpubpublish-coclass.md)
