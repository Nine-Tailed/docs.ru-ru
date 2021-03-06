---
title: Метод IMetaDataImport2::GetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ded6b4e0ac8f3e70fd0145ab6e2410c3b38e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448678"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>Метод IMetaDataImport2::GetGenericParamProps
Возвращает метаданные, связанные с универсальным параметром, представленного указанным токеном.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `gp`  
 [in] Токен, представляющий универсальный параметр, для которого возвращаются метаданные.  
  
 `pulParamSeq`  
 [out] Порядковый номер `Type` параметра в родительский конструктор или метод.  
  
 `pdwParamFlags`  
 [out] Значение [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) перечисление, описывающее `Type` универсального параметра.  
  
 `ptOwner`  
 [out] Токен TypeDef или MethodDef, представляющий владельца параметра.  
  
 `reserved`  
 [out] Зарезервировано для будущего расширения.  
  
 `wzName`  
 [out] Имя универсального параметра.  
  
 `cchName`  
 [in] Размер `wzName` буфера.  
  
 `pchName`  
 [out] Возвращаемый размер имя в расширенных символов.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** Cor.h  
  
 **Библиотека:** используется как ресурс в MsCorEE.dll  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [Интерфейс IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
