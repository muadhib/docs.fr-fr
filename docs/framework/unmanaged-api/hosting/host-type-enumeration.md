---
title: "HOST_TYPE, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: HOST_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: HOST_TYPE
helpviewer_keywords: HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e191293ff7bde6b1be2210af4e7830fec0d7290d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="9128d-102">HOST_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="9128d-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="9128d-103">Contient des valeurs qui spécifient le type d’hôte qui lance une application.</span><span class="sxs-lookup"><span data-stu-id="9128d-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9128d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9128d-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9128d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9128d-105">Members</span></span>  
  
|<span data-ttu-id="9128d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9128d-106">Member</span></span>|<span data-ttu-id="9128d-107">Description</span><span class="sxs-lookup"><span data-stu-id="9128d-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="9128d-108">Lancez l’application à partir d’AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="9128d-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="9128d-109">Utilisez cette valeur pour les applications de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="9128d-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="9128d-110">Lancer l’application directement.</span><span class="sxs-lookup"><span data-stu-id="9128d-110">Launch the application directly.</span></span> <span data-ttu-id="9128d-111">Autrement dit, lancez l’application à partir de son propre fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="9128d-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="9128d-112">Utilisez cette valeur pour les applications de confiance.</span><span class="sxs-lookup"><span data-stu-id="9128d-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="9128d-113">Identique à HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="9128d-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9128d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9128d-114">Requirements</span></span>  
 <span data-ttu-id="9128d-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9128d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9128d-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9128d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9128d-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9128d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9128d-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9128d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9128d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9128d-119">See Also</span></span>  
 [<span data-ttu-id="9128d-120">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9128d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)