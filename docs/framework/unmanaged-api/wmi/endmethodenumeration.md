---
title: "EndMethodEnumeration (fonction) (référence des API non managées)"
description: "La fonction EndMethodEnumeration met fin à une séquence d’énumération de méthode."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: EndMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: EndMethodEnumeration
helpviewer_keywords: EndMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1b768292811a752e7a319f853ca8eff85f1bb08
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="5615b-103">EndMethodEnumeration (fonction)</span><span class="sxs-lookup"><span data-stu-id="5615b-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="5615b-104">Met fin à une séquence d’énumération démarrée avec un appel à la [BeginMethodEnumeration fonction](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5615b-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5615b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5615b-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="5615b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5615b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5615b-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="5615b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5615b-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="5615b-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="5615b-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5615b-109">Return value</span></span>

<span data-ttu-id="5615b-110">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="5615b-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5615b-111">Constante</span><span class="sxs-lookup"><span data-stu-id="5615b-111">Constant</span></span>  |<span data-ttu-id="5615b-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="5615b-112">Value</span></span>  |<span data-ttu-id="5615b-113">Description</span><span class="sxs-lookup"><span data-stu-id="5615b-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="5615b-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="5615b-114">0x8004101d</span></span> | <span data-ttu-id="5615b-115">Une erreur interne s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5615b-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5615b-116">0</span><span class="sxs-lookup"><span data-stu-id="5615b-116">0</span></span> | <span data-ttu-id="5615b-117">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="5615b-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5615b-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="5615b-118">Remarks</span></span>

<span data-ttu-id="5615b-119">Cette fonction encapsule un appel à la [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5615b-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5615b-120">L’appelant commence la séquence d’énumération à l’aide [BeginMethodEnumeration fonction](beginmethodenumeration.md), puis appelle la [NextMethod fonction](nextmethod.md )jusqu'à ce que la méthode retourne `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="5615b-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="5615b-121">L’appelant éventuellement termine la séquence en appelant `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="5615b-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="5615b-122">L’appelant peut terminer l’énumération au début en appelant `EndMethodEnumeration` à tout moment.</span><span class="sxs-lookup"><span data-stu-id="5615b-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="5615b-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5615b-123">Requirements</span></span>  
 <span data-ttu-id="5615b-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5615b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5615b-125">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5615b-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5615b-126">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5615b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5615b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5615b-127">See also</span></span>  
[<span data-ttu-id="5615b-128">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="5615b-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)