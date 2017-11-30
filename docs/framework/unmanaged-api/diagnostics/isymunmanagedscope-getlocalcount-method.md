---
title: "Метод ISymUnmanagedScope::GetLocalCount"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetLocalCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de8f0ee3e2a1cc13a9bdb0f59aaecd4592ea7fdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="1d20d-102">Метод ISymUnmanagedScope::GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="1d20d-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="1d20d-103">Возвращает количество локальных переменных, определенных в данной области.</span><span class="sxs-lookup"><span data-stu-id="1d20d-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d20d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1d20d-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d20d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="1d20d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1d20d-106">[out] Указатель на `ULONG32` , который получает количество локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="1d20d-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d20d-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1d20d-107">Return Value</span></span>  
 <span data-ttu-id="1d20d-108">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="1d20d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d20d-109">Требования</span><span class="sxs-lookup"><span data-stu-id="1d20d-109">Requirements</span></span>  
 <span data-ttu-id="1d20d-110">**Заголовок:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1d20d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d20d-111">См. также</span><span class="sxs-lookup"><span data-stu-id="1d20d-111">See Also</span></span>  
 [<span data-ttu-id="1d20d-112">ISymUnmanagedScope-интерфейс</span><span class="sxs-lookup"><span data-stu-id="1d20d-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)