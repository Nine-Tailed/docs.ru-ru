---
title: "Перечисление WAIT_OPTION"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAIT_OPTION
api_location: mscoree.dll
api_type: COM
f1_keywords: WAIT_OPTION
helpviewer_keywords: WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08bdfc928c56d144f50399814a81795fea74574a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="644f1-102">Перечисление WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="644f1-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="644f1-103">Содержит значения, указывающие, что необходимо выполнить действия узла, если операцию, запрошенную среды выполнения (CLR) блоками выполнения.</span><span class="sxs-lookup"><span data-stu-id="644f1-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="644f1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="644f1-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="644f1-105">Члены</span><span class="sxs-lookup"><span data-stu-id="644f1-105">Members</span></span>  
  
|<span data-ttu-id="644f1-106">Член</span><span class="sxs-lookup"><span data-stu-id="644f1-106">Member</span></span>|<span data-ttu-id="644f1-107">Описание</span><span class="sxs-lookup"><span data-stu-id="644f1-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="644f1-108">Уведомляет основное приложение, задачи должны быть выведены из спящего режима средой CLR [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="644f1-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="644f1-109">Уведомляет узел, что он должен выдавать сообщения в текущем потоке операционной системы, при блокировании.</span><span class="sxs-lookup"><span data-stu-id="644f1-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="644f1-110">Среда выполнения определяет это значение только для <xref:System.Threading.ApartmentState.STA> потока.</span><span class="sxs-lookup"><span data-stu-id="644f1-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="644f1-111">Уведомляет узел, что заданный запрос синхронизации не может быть разбит узел.</span><span class="sxs-lookup"><span data-stu-id="644f1-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="644f1-112">То есть узел не может возвращать `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="644f1-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="644f1-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="644f1-113">Remarks</span></span>  
 <span data-ttu-id="644f1-114">[IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) и [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) оба метода принимают параметр типа.</span><span class="sxs-lookup"><span data-stu-id="644f1-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="644f1-115">Требования</span><span class="sxs-lookup"><span data-stu-id="644f1-115">Requirements</span></span>  
 <span data-ttu-id="644f1-116">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="644f1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="644f1-117">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="644f1-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="644f1-118">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="644f1-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="644f1-119">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="644f1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644f1-120">См. также</span><span class="sxs-lookup"><span data-stu-id="644f1-120">See Also</span></span>  
 [<span data-ttu-id="644f1-121">Перечисления размещения</span><span class="sxs-lookup"><span data-stu-id="644f1-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)