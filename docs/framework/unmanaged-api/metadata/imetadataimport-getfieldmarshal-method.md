---
title: "IMetaDataImport::GetFieldMarshal, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce29990bf9e6b5b670a9a277442adac4ceef2947
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="7201d-102">IMetaDataImport::GetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="7201d-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="7201d-103">Obtient un pointeur vers le type natif non managé du champ représenté par le jeton de métadonnées de champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="7201d-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7201d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7201d-104">Syntax</span></span>  
  
```  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7201d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7201d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7201d-106">[in] Le jeton de métadonnées qui représente le champ pour obtenir des informations de marshaling interop de.</span><span class="sxs-lookup"><span data-stu-id="7201d-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="7201d-107">[out] Pointeur vers la signature de métadonnées de type natif du champ.</span><span class="sxs-lookup"><span data-stu-id="7201d-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="7201d-108">[out] La taille en octets de `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="7201d-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7201d-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7201d-109">Requirements</span></span>  
 <span data-ttu-id="7201d-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7201d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7201d-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7201d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7201d-112">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7201d-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7201d-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7201d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7201d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7201d-114">See Also</span></span>  
 [<span data-ttu-id="7201d-115">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="7201d-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7201d-116">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="7201d-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)