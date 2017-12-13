---
title: CorElementType Enumeration1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorElementType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorElementType
helpviewer_keywords: CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8932e295aa1a6c6cf961e7b3a218e76984da02cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corelementtype-enumeration1"></a><span data-ttu-id="1199e-102">CorElementType Enumeration1</span><span class="sxs-lookup"><span data-stu-id="1199e-102">CorElementType Enumeration1</span></span>
<span data-ttu-id="1199e-103">Spécifie un common language runtime <xref:System.Type>, un modificateur de type ou des informations sur un type dans une signature de type de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="1199e-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1199e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1199e-104">Syntax</span></span>  
  
```  
typedef enum CorElementType {  
    ELEMENT_TYPE_END            = 0x0,  
    ELEMENT_TYPE_VOID           = 0x1,  
    ELEMENT_TYPE_BOOLEAN        = 0x2,  
    ELEMENT_TYPE_CHAR           = 0x3,  
    ELEMENT_TYPE_I1             = 0x4,  
    ELEMENT_TYPE_U1             = 0x5,  
    ELEMENT_TYPE_I2             = 0x6,  
    ELEMENT_TYPE_U2             = 0x7,  
    ELEMENT_TYPE_I4             = 0x8,  
    ELEMENT_TYPE_U4             = 0x9,  
    ELEMENT_TYPE_I8             = 0xa,  
    ELEMENT_TYPE_U8             = 0xb,  
    ELEMENT_TYPE_R4             = 0xc,  
    ELEMENT_TYPE_R8             = 0xd,  
    ELEMENT_TYPE_STRING         = 0xe,  
  
    ELEMENT_TYPE_PTR            = 0xf,  
    ELEMENT_TYPE_BYREF          = 0x10,  
  
    ELEMENT_TYPE_VALUETYPE      = 0x11,  
    ELEMENT_TYPE_CLASS          = 0x12,  
    ELEMENT_TYPE_VAR            = 0x13,  
    ELEMENT_TYPE_ARRAY          = 0x14,  
    ELEMENT_TYPE_GENERICINST    = 0x15,  
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,  
  
    ELEMENT_TYPE_I              = 0x18,  
    ELEMENT_TYPE_U              = 0x19,  
    ELEMENT_TYPE_FNPTR          = 0x1B,  
    ELEMENT_TYPE_OBJECT         = 0x1C,  
    ELEMENT_TYPE_SZARRAY        = 0x1D,  
    ELEMENT_TYPE_MVAR           = 0x1e,  
  
    ELEMENT_TYPE_CMOD_REQD      = 0x1F,  
    ELEMENT_TYPE_CMOD_OPT       = 0x20,  
  
    ELEMENT_TYPE_INTERNAL       = 0x21,  
    ELEMENT_TYPE_MAX            = 0x22,  
  
    ELEMENT_TYPE_MODIFIER       = 0x40,  
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,  
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER  
  
} CorElementType;  
```  
  
## <a name="members"></a><span data-ttu-id="1199e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1199e-105">Members</span></span>  
  
|<span data-ttu-id="1199e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1199e-106">Member</span></span>|<span data-ttu-id="1199e-107">Description</span><span class="sxs-lookup"><span data-stu-id="1199e-107">Description</span></span>|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|<span data-ttu-id="1199e-108">Utilisé en interne.</span><span class="sxs-lookup"><span data-stu-id="1199e-108">Used internally.</span></span>|  
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="1199e-109">Un type void.</span><span class="sxs-lookup"><span data-stu-id="1199e-109">A void type.</span></span>|  
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="1199e-110">Un type Boolean</span><span class="sxs-lookup"><span data-stu-id="1199e-110">A Boolean type</span></span>|  
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="1199e-111">Type de caractère.</span><span class="sxs-lookup"><span data-stu-id="1199e-111">A character type.</span></span>|  
|`ELEMENT_TYPE_I1`|<span data-ttu-id="1199e-112">Entier signé sur 1 octet.</span><span class="sxs-lookup"><span data-stu-id="1199e-112">A signed 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_U1`|<span data-ttu-id="1199e-113">Entier non signé sur 1 octet.</span><span class="sxs-lookup"><span data-stu-id="1199e-113">An unsigned 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_I2`|<span data-ttu-id="1199e-114">Un entier signé de 2 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-114">A signed 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_U2`|<span data-ttu-id="1199e-115">Entier non signé sur 2 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-115">An unsigned 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_I4`|<span data-ttu-id="1199e-116">Un entier signé de 4 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-116">A signed 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_U4`|<span data-ttu-id="1199e-117">Entier non signé sur 4 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-117">An unsigned 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_I8`|<span data-ttu-id="1199e-118">Un entier signé de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-118">A signed 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_U8`|<span data-ttu-id="1199e-119">Entier non signé sur 8 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-119">An unsigned 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_R4`|<span data-ttu-id="1199e-120">Un virgule flottante de 4 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-120">A 4-byte floating point.</span></span>|  
|`ELEMENT_TYPE_R8`|<span data-ttu-id="1199e-121">Une virgule flottante de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="1199e-121">An 8-byte floating point.</span></span>|  
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="1199e-122">Un type System.String.</span><span class="sxs-lookup"><span data-stu-id="1199e-122">A System.String type.</span></span>|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="1199e-123">Un modificateur de type pointeur.</span><span class="sxs-lookup"><span data-stu-id="1199e-123">A pointer type modifier.</span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="1199e-124">Un modificateur de type référence.</span><span class="sxs-lookup"><span data-stu-id="1199e-124">A reference type modifier.</span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="1199e-125">Un modificateur de type valeur.</span><span class="sxs-lookup"><span data-stu-id="1199e-125">A value type modifier.</span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="1199e-126">Un modificateur de type classe.</span><span class="sxs-lookup"><span data-stu-id="1199e-126">A class type modifier.</span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="1199e-127">Un modificateur de type de variable de classe.</span><span class="sxs-lookup"><span data-stu-id="1199e-127">A class variable type modifier.</span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="1199e-128">Un modificateur de type tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="1199e-128">A multi-dimensional array type modifier.</span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="1199e-129">Un modificateur de type pour les types génériques.</span><span class="sxs-lookup"><span data-stu-id="1199e-129">A type modifier for generic types.</span></span>|  
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="1199e-130">Référence typée.</span><span class="sxs-lookup"><span data-stu-id="1199e-130">A typed reference.</span></span>|  
|`ELEMENT_TYPE_I`|<span data-ttu-id="1199e-131">Taille d’un entier natif.</span><span class="sxs-lookup"><span data-stu-id="1199e-131">Size of a native integer.</span></span>|  
|`ELEMENT_TYPE_U`|<span data-ttu-id="1199e-132">Taille d’un entier natif non signé.</span><span class="sxs-lookup"><span data-stu-id="1199e-132">Size of an unsigned native integer.</span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="1199e-133">Pointeur vers une fonction.</span><span class="sxs-lookup"><span data-stu-id="1199e-133">A pointer to a function.</span></span>|  
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="1199e-134">Un type System.Object.</span><span class="sxs-lookup"><span data-stu-id="1199e-134">A System.Object type.</span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="1199e-135">Une seule dimension, aucun modificateur de type tableau de limite inférieure.</span><span class="sxs-lookup"><span data-stu-id="1199e-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="1199e-136">Un modificateur de type variable (méthode)</span><span class="sxs-lookup"><span data-stu-id="1199e-136">A method variable type modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="1199e-137">Modificateur de langage C requis.</span><span class="sxs-lookup"><span data-stu-id="1199e-137">A C language required modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="1199e-138">Un modificateur facultatif de langage C.</span><span class="sxs-lookup"><span data-stu-id="1199e-138">A C language optional modifier.</span></span>|  
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="1199e-139">Utilisé en interne.</span><span class="sxs-lookup"><span data-stu-id="1199e-139">Used internally.</span></span>|  
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="1199e-140">Type non valide.</span><span class="sxs-lookup"><span data-stu-id="1199e-140">An invalid type.</span></span>|  
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="1199e-141">Utilisé en interne.</span><span class="sxs-lookup"><span data-stu-id="1199e-141">Used internally.</span></span>|  
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="1199e-142">Un modificateur de type qui est une sentinelle pour obtenir la liste d’un nombre variable de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1199e-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|  
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="1199e-143">Utilisé en interne.</span><span class="sxs-lookup"><span data-stu-id="1199e-143">Used internally.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1199e-144">Remarques</span><span class="sxs-lookup"><span data-stu-id="1199e-144">Remarks</span></span>  
 <span data-ttu-id="1199e-145">Les modificateurs de type constituent la base pour représenter des types plus complexes.</span><span class="sxs-lookup"><span data-stu-id="1199e-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="1199e-146">A `CorElementType` valeur de modificateur de type est appliquée à la valeur qui suit immédiatement dans la signature de type.</span><span class="sxs-lookup"><span data-stu-id="1199e-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="1199e-147">La valeur qui suit le `CorElementType` valeur de modificateur de type peut être un `CorElementType` valeur de type simple, un jeton de métadonnées ou une autre valeur, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1199e-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1199e-148">Tous les nombres (*nombre*, *nombre d’arguments*, *jeton de métadonnées*, *rang*, *nombre*et *liés*) sont stockés sous la forme d’entiers compressés.</span><span class="sxs-lookup"><span data-stu-id="1199e-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="1199e-149">Consultez [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) sur le site Web ECMA pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="1199e-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>  
  
|<span data-ttu-id="1199e-150">Modificateur de type</span><span class="sxs-lookup"><span data-stu-id="1199e-150">Type modifier</span></span>|<span data-ttu-id="1199e-151">Format</span><span class="sxs-lookup"><span data-stu-id="1199e-151">Format</span></span>|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="1199e-152">ELEMENT_TYPE_PTR < un `CorElementType` valeur ></span><span class="sxs-lookup"><span data-stu-id="1199e-152">ELEMENT_TYPE_PTR <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="1199e-153">ELEMENT_TYPE_BYREF < un `CorElementType` valeur ></span><span class="sxs-lookup"><span data-stu-id="1199e-153">ELEMENT_TYPE_BYREF <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="1199e-154">ELEMENT_TYPE_VALUETYPE < un `mdTypeDef` jeton de métadonnées ></span><span class="sxs-lookup"><span data-stu-id="1199e-154">ELEMENT_TYPE_VALUETYPE <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="1199e-155">ELEMENT_TYPE_CLASS < un `mdTypeDef` jeton de métadonnées ></span><span class="sxs-lookup"><span data-stu-id="1199e-155">ELEMENT_TYPE_CLASS <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="1199e-156">ELEMENT_TYPE_VAR \<nombre ></span><span class="sxs-lookup"><span data-stu-id="1199e-156">ELEMENT_TYPE_VAR \<number></span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="1199e-157">ELEMENT_TYPE_ARRAY < un `CorElementType` valeur > \<rang > \<count1 > \<bound1 >... \<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="1199e-157">ELEMENT_TYPE_ARRAY <a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="1199e-158">ELEMENT_TYPE_GENERICINST < un `mdTypeDef` jeton de métadonnées > \<argument Count > \<arg1 >... \<argN ></span><span class="sxs-lookup"><span data-stu-id="1199e-158">ELEMENT_TYPE_GENERICINST <an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="1199e-159">ELEMENT_TYPE_FNPTR \<signature complète de la fonction, y compris la convention d’appel ></span><span class="sxs-lookup"><span data-stu-id="1199e-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="1199e-160">ELEMENT_TYPE_SZARRAY < un `CorElementType` valeur ></span><span class="sxs-lookup"><span data-stu-id="1199e-160">ELEMENT_TYPE_SZARRAY <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="1199e-161">ELEMENT_TYPE_MVAR \<nombre ></span><span class="sxs-lookup"><span data-stu-id="1199e-161">ELEMENT_TYPE_MVAR \<number></span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="1199e-162">ELEMENT_TYPE_ < un `mdTypeRef` ou `mdTypeDef` jeton de métadonnées ></span><span class="sxs-lookup"><span data-stu-id="1199e-162">ELEMENT_TYPE_<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="1199e-163">E_T_CMOD_OPT < un `mdTypeRef` ou `mdTypeDef` jeton de métadonnées ></span><span class="sxs-lookup"><span data-stu-id="1199e-163">E_T_CMOD_OPT <a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1199e-164">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1199e-164">Requirements</span></span>  
 <span data-ttu-id="1199e-165">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1199e-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1199e-166">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1199e-166">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1199e-167">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1199e-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1199e-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1199e-168">See Also</span></span>  
 [<span data-ttu-id="1199e-169">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="1199e-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)