---
title: Метод IGCThreadControl::ThreadIsBlockingForSuspension
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f4b767fe7134833ee2e404be30bb51bf1385ec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437041"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a>Метод IGCThreadControl::ThreadIsBlockingForSuspension
Уведомляет узел, что поток, который выполняет вызов заблокирован, возможно, для сборки мусора или по другой причине.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a>Примечания  
 Выбрать узел в `ThreadIsBlockingForSuspension` обратного вызова необходимость повторного планирования в потоке.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** включена как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
