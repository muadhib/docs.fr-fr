---
title: "ICorRuntimeHost::Start, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d79046db904de68e5b24b2f96206bb1de2de470
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststart-method"></a>ICorRuntimeHost::Start, méthode
Démarre le common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’opération a réussi.|  
|S_FALSE|L’opération a échoué.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
  
## <a name="remarks"></a>Notes  
 Il n’est généralement pas nécessaire d’appeler le `Start` (méthode), car le CLR démarre automatiquement dès la première demande d’exécuter du code managé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :** 1.0, 1.1  
  
## <a name="see-also"></a>Voir aussi  
 [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
