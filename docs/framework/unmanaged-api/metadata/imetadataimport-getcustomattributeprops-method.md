---
title: "Метод IMetaDataImport::GetCustomAttributeProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 415b1dc67bd3ae3638edd61558cc9e13ebf03fd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="63781-102">Метод IMetaDataImport::GetCustomAttributeProps</span><span class="sxs-lookup"><span data-stu-id="63781-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="63781-103">Возвращает значение настраиваемого атрибута по указанному токену метаданных.</span><span class="sxs-lookup"><span data-stu-id="63781-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63781-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="63781-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63781-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="63781-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="63781-106">[in] Токен метаданных, который представляет извлекаемый пользовательский атрибут.</span><span class="sxs-lookup"><span data-stu-id="63781-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="63781-107">[out, optional] Токен метаданных, представляющий объект, который изменяет пользовательский атрибут.</span><span class="sxs-lookup"><span data-stu-id="63781-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="63781-108">Это значение может быть любым типом токена метаданных, кроме `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="63781-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="63781-109">[out, optional] Токен метаданных `mdMethodDef` или `mdMemberRef`, представляющий <xref:System.Type> возвращаемого пользовательского атрибута.</span><span class="sxs-lookup"><span data-stu-id="63781-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="63781-110">[out, optional] Указатель на массив данных, который является значением пользовательского атрибута.</span><span class="sxs-lookup"><span data-stu-id="63781-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="63781-111">[out, optional] Размер в байтах данных, возвращаемых в *`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="63781-111">[out, optional] The size in bytes of the data returned in *`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63781-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="63781-112">Remarks</span></span>  
 <span data-ttu-id="63781-113">Пользовательский атрибут хранится в виде массива данных, в формате, который поддерживается подсистемой метаданных.</span><span class="sxs-lookup"><span data-stu-id="63781-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63781-114">Требования</span><span class="sxs-lookup"><span data-stu-id="63781-114">Requirements</span></span>  
 <span data-ttu-id="63781-115">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63781-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63781-116">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="63781-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63781-117">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63781-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63781-118">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63781-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63781-119">См. также</span><span class="sxs-lookup"><span data-stu-id="63781-119">See Also</span></span>  
 [<span data-ttu-id="63781-120">IMetaDataImport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="63781-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="63781-121">IMetaDataImport2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="63781-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)