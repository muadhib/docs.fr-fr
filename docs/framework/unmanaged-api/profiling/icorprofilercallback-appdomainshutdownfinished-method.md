---
title: "ICorProfilerCallback::AppDomainShutdownFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 443f5cd48693d6ac3ce732746666bd2d5e3786fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="7eb9b-102">ICorProfilerCallback::AppDomainShutdownFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="7eb9b-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="7eb9b-103">Informe le profileur qu’un domaine d’application a été déchargé à partir d’un processus.</span><span class="sxs-lookup"><span data-stu-id="7eb9b-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb9b-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eb9b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7eb9b-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="7eb9b-106">[in] Identifie le domaine dans lequel sont stockés les assemblys de l’application.</span><span class="sxs-lookup"><span data-stu-id="7eb9b-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7eb9b-107">[in] HRESULT qui indique si le domaine d’application a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="7eb9b-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eb9b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="7eb9b-108">Remarks</span></span>  
 <span data-ttu-id="7eb9b-109">La valeur de `appDomainId` n’est pas valide pour une demande d’informations après le [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) retourne de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7eb9b-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="7eb9b-110">Certaines parties du déchargement du domaine d’application peuvent continuer après le `AppDomainCreationFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="7eb9b-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="7eb9b-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="7eb9b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7eb9b-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement du domaine d’application a réussi.</span><span class="sxs-lookup"><span data-stu-id="7eb9b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb9b-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7eb9b-113">Requirements</span></span>  
 <span data-ttu-id="7eb9b-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb9b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb9b-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7eb9b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7eb9b-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eb9b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eb9b-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb9b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb9b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eb9b-118">See Also</span></span>  
 [<span data-ttu-id="7eb9b-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7eb9b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)