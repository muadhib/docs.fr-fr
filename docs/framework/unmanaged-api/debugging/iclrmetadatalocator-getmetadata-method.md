---
title: "ICLRMetadataLocator::GetMetadata, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator.GetMetadata
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8758a96464d1465d92fb17314f1e36ab8d9169c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata, méthode
Appelé par les services d’accès aux données du common language runtime (CLR) pour récupérer les métadonnées d’une image.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `imagePath`  
 [in] Chaîne qui spécifie le chemin d’accès du fichier image.  
  
 `imageTimestamp`  
 [in] L’horodatage du fichier image.  
  
 `imageSize`  
 [in] La taille du fichier image.  
  
 `mvid`  
 [in] L’identificateur global unique de l’image.  
  
 `mdRva`  
 [in] L’adresse virtuelle relative (RVA) des métadonnées. L’adresse est relatif à l’adresse de base d’image.  
  
 `flags`  
 [in] Réservé à un usage ultérieur.  
  
 `bufferSize`  
 [in] La taille de la mémoire tampon dans laquelle placer les métadonnées.  
  
 `buffer`  
 [out] La mémoire tampon dans laquelle placer les métadonnées.  
  
 `dataSize`  
 [out] La taille des métadonnées qui sont retournée.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRMetadataLocator, interface](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
