---
title: Метод ICorDebugThread3::GetActiveInternalFrames
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ac87de35478e5eabdc8cdc3568baf2086923e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423027"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>Метод ICorDebugThread3::GetActiveInternalFrames
Возвращает массив внутренних кадрах ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) объектов) в стеке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a>Параметры  
 `cInternalFrames`  
 [in] Количество внутренних кадрах, ожидаемая в `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Указатель на `ULONG32` , содержащее количество внутренних кадров в стеке.  
  
 `ppInternalFrames`  
 [in, out] Указатель на адрес массива внутренних кадров в стеке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) объект был успешно создан.|  
|E_INVALIDARG|`cInternalFrames` не равно нулю и `ppInternalFrames` — `null`, или `pcInternalFrames` — `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` меньше количество внутренних кадрах.|  
  
## <a name="exceptions"></a>Исключения  
  
## <a name="remarks"></a>Примечания  
 Внутренние кадры — это структуры данных, переданные в стек средой выполнения для хранения временных данных.  
  
 При первом вызове `GetActiveInternalFrames`, следует задать `cInternalFrames` в значение 0 (ноль) и `ppInternalFrames` параметр в значение null. Когда `GetActiveInternalFrames` сначала возвращает `pcInternalFrames` содержит количество внутренних кадров в стеке.  
  
 `GetActiveInternalFrames` затем вызывать следует еще раз. Необходимо передать правильное значение (`pcInternalFrames`) в `cInternalFrames` параметра, и задать указатель на массив подходящего размера в `ppInternalFrames`.  
  
 Используйте [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) метод для возврата фактическое фреймов стека.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Отладка](../../../../docs/framework/unmanaged-api/debugging/index.md)
