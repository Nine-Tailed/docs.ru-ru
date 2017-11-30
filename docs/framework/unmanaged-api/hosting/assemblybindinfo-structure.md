---
title: "Структура AssemblyBindInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="2abaa-102">Структура AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="2abaa-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="2abaa-103">Содержит подробные сведения о сборке, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="2abaa-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2abaa-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2abaa-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="2abaa-105">Члены</span><span class="sxs-lookup"><span data-stu-id="2abaa-105">Members</span></span>  
  
|<span data-ttu-id="2abaa-106">Член</span><span class="sxs-lookup"><span data-stu-id="2abaa-106">Member</span></span>|<span data-ttu-id="2abaa-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2abaa-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="2abaa-108">Уникальный идентификатор для `IStream` возвращается путем вызова [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), из которой сборка будет загружаться.</span><span class="sxs-lookup"><span data-stu-id="2abaa-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="2abaa-109">Уникальный идентификатор для указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="2abaa-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="2abaa-110">Идентификатор для свойства ссылки после применения всех значений политики привязки.</span><span class="sxs-lookup"><span data-stu-id="2abaa-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="2abaa-111">Один из [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) значения, указывающие, какие политики управления версиями, если таковые имеются, должны применяться к ссылочной сборки.</span><span class="sxs-lookup"><span data-stu-id="2abaa-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2abaa-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="2abaa-112">Remarks</span></span>  
 <span data-ttu-id="2abaa-113">Узел предоставляет уникальный идентификатор `dwAppDomainId` для общеязыковой среды выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="2abaa-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="2abaa-114">После вызова `IHostAssemblyStore::ProvideAssembly` возвращает управление, среда выполнения использует идентификатор, чтобы определить, является ли содержимое `IStream` были сопоставлены.</span><span class="sxs-lookup"><span data-stu-id="2abaa-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="2abaa-115">В этом случае среда выполнения загружает имеющуюся копию вместо повторного сопоставления потока.</span><span class="sxs-lookup"><span data-stu-id="2abaa-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="2abaa-116">Среда выполнения также использует этот идентификатор в качестве ключа поиска для потоков, возвращенных из вызовы [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="2abaa-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="2abaa-117">Таким образом идентификатор должен быть уникальным для запросов модулей и запросов сборок.</span><span class="sxs-lookup"><span data-stu-id="2abaa-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2abaa-118">Требования</span><span class="sxs-lookup"><span data-stu-id="2abaa-118">Requirements</span></span>  
 <span data-ttu-id="2abaa-119">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2abaa-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2abaa-120">**Заголовок:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="2abaa-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="2abaa-121">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2abaa-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2abaa-122">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2abaa-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abaa-123">См. также</span><span class="sxs-lookup"><span data-stu-id="2abaa-123">See Also</span></span>  
 [<span data-ttu-id="2abaa-124">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="2abaa-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="2abaa-125">Iclrassemblyidentitymanager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="2abaa-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="2abaa-126">ICLRAssemblyReferenceList-интерфейс</span><span class="sxs-lookup"><span data-stu-id="2abaa-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="2abaa-127">Ihostassemblymanager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="2abaa-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="2abaa-128">IHostAssemblyStore-интерфейс</span><span class="sxs-lookup"><span data-stu-id="2abaa-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="2abaa-129">Modulebindinfo-структура</span><span class="sxs-lookup"><span data-stu-id="2abaa-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)