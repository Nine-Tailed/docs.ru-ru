---
title: "Метод IMetaDataAssemblyEmit::SetManifestResourceProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3cc447b18ac6ccabd642ab0a1fb5b887fb4fbe4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="bdd38-102">Метод IMetaDataAssemblyEmit::SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="bdd38-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="bdd38-103">Изменяет указанную структуру метаданных `ManifestResource`.</span><span class="sxs-lookup"><span data-stu-id="bdd38-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd38-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bdd38-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdd38-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="bdd38-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="bdd38-106">[in] Маркер, который указывает `ManifestResource` изменение структуры метаданных.</span><span class="sxs-lookup"><span data-stu-id="bdd38-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="bdd38-107">[in] Маркер типа `File` или `AssemblyRef`, который сопоставляется с поставщиком ресурсов.</span><span class="sxs-lookup"><span data-stu-id="bdd38-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="bdd38-108">[in] Смещение в начало ресурса в файле.</span><span class="sxs-lookup"><span data-stu-id="bdd38-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="bdd38-109">[in] Побитовое сочетание значения флагов, определяющих атрибуты ресурса.</span><span class="sxs-lookup"><span data-stu-id="bdd38-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdd38-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="bdd38-110">Remarks</span></span>  
 <span data-ttu-id="bdd38-111">Для создания `ManifestResource` структуру метаданных, используйте [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="bdd38-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd38-112">Требования</span><span class="sxs-lookup"><span data-stu-id="bdd38-112">Requirements</span></span>  
 <span data-ttu-id="bdd38-113">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdd38-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd38-114">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bdd38-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bdd38-115">**Библиотека:** используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bdd38-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdd38-116">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd38-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd38-117">См. также</span><span class="sxs-lookup"><span data-stu-id="bdd38-117">See Also</span></span>  
 [<span data-ttu-id="bdd38-118">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="bdd38-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)