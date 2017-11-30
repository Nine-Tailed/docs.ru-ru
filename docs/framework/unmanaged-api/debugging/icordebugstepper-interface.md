---
title: "ICorDebugStepper интерфейс1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper
helpviewer_keywords: ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83d394669270eb26b33e084b20a621e18b5b14aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper-interface1"></a><span data-ttu-id="59d26-102">ICorDebugStepper интерфейс1</span><span class="sxs-lookup"><span data-stu-id="59d26-102">ICorDebugStepper Interface1</span></span>
<span data-ttu-id="59d26-103">Представляет предпринимаемый отладчиком шаг при выполнении кода, служащий идентификатором на промежутке между подачей команды и ее завершением, а также предоставляет возможность отмены шага.</span><span class="sxs-lookup"><span data-stu-id="59d26-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59d26-104">Методы</span><span class="sxs-lookup"><span data-stu-id="59d26-104">Methods</span></span>  
  
|<span data-ttu-id="59d26-105">Метод</span><span class="sxs-lookup"><span data-stu-id="59d26-105">Method</span></span>|<span data-ttu-id="59d26-106">Описание</span><span class="sxs-lookup"><span data-stu-id="59d26-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59d26-107">Deactivate-метод</span><span class="sxs-lookup"><span data-stu-id="59d26-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="59d26-108">В результате `ICorDebugStepper` для отмены последней команды шага, оно получено.</span><span class="sxs-lookup"><span data-stu-id="59d26-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="59d26-109">IsActive-метод</span><span class="sxs-lookup"><span data-stu-id="59d26-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="59d26-110">Возвращает значение, указывающее, является ли это `ICorDebugStepper` в данный момент выполняет этап.</span><span class="sxs-lookup"><span data-stu-id="59d26-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="59d26-111">Метод SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="59d26-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="59d26-112">Задает CorDebugIntercept значение, указывающее типы кода, для которого осуществляется пошаговое.</span><span class="sxs-lookup"><span data-stu-id="59d26-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="59d26-113">Метод SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="59d26-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="59d26-114">Задает значение, указывающее, является ли вызовы [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) значения аргументов относительно машинный код или код на промежуточном языке (MSIL) метода, который является в настоящее время шаг.</span><span class="sxs-lookup"><span data-stu-id="59d26-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="59d26-115">Метод SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="59d26-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="59d26-116">Задает значение CorDebugUnmappedStop, которое указывает тип несопоставимого кода, в котором выполнение будет остановлено.</span><span class="sxs-lookup"><span data-stu-id="59d26-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="59d26-117">Step-метод</span><span class="sxs-lookup"><span data-stu-id="59d26-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="59d26-118">В результате `ICorDebugStepper` на один шаг через содержащую и, при необходимости, чтобы продолжить, при пошаговом выполнении функций, которые вызываются в потоке.</span><span class="sxs-lookup"><span data-stu-id="59d26-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="59d26-119">Метод StepOut</span><span class="sxs-lookup"><span data-stu-id="59d26-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="59d26-120">В результате `ICorDebugStepper` один шаг через содержащую и завершается, когда текущий кадр возвращает управление в вызывающий кадр.</span><span class="sxs-lookup"><span data-stu-id="59d26-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="59d26-121">Метод StepRange</span><span class="sxs-lookup"><span data-stu-id="59d26-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="59d26-122">В результате `ICorDebugStepper` на один шаг через содержащую и возвратить при достижении кода за последним из указанных диапазонов.</span><span class="sxs-lookup"><span data-stu-id="59d26-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d26-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="59d26-123">Remarks</span></span>  
 <span data-ttu-id="59d26-124">`ICorDebugStepper` Интерфейс выполняет следующие функции:</span><span class="sxs-lookup"><span data-stu-id="59d26-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="59d26-125">Он служит идентификатором на промежутке между выданный командой шага и завершением этой команды.</span><span class="sxs-lookup"><span data-stu-id="59d26-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="59d26-126">Он обеспечивает центральный интерфейс для инкапсулирования всех шагов, которое может быть выполнено.</span><span class="sxs-lookup"><span data-stu-id="59d26-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="59d26-127">Он предоставляет способ преждевременно отменить пошагового выполнения операции.</span><span class="sxs-lookup"><span data-stu-id="59d26-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="59d26-128">Может существовать несколько шагов на поток.</span><span class="sxs-lookup"><span data-stu-id="59d26-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="59d26-129">Например может быть достигнута точка останова при шаг с обходом функции и пользователь может потребоваться запустить новую операцию пошагового выполнения внутри этой функции.</span><span class="sxs-lookup"><span data-stu-id="59d26-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="59d26-130">Именно отладчика для определения способа обработки этой ситуации.</span><span class="sxs-lookup"><span data-stu-id="59d26-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="59d26-131">Отладчик может потребоваться отменить исходную шаговую операцию или вложить две операции.</span><span class="sxs-lookup"><span data-stu-id="59d26-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="59d26-132">`ICorDebugStepper` Интерфейс поддерживает две возможности.</span><span class="sxs-lookup"><span data-stu-id="59d26-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="59d26-133">Шаг может мигрировать между потоками, если общеязыковая среда выполнения (CLR) вызывает между потоками, упакованы.</span><span class="sxs-lookup"><span data-stu-id="59d26-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59d26-134">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="59d26-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59d26-135">Требования</span><span class="sxs-lookup"><span data-stu-id="59d26-135">Requirements</span></span>  
 <span data-ttu-id="59d26-136">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59d26-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59d26-137">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59d26-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59d26-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59d26-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59d26-139">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59d26-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d26-140">См. также</span><span class="sxs-lookup"><span data-stu-id="59d26-140">See Also</span></span>  
 [<span data-ttu-id="59d26-141">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="59d26-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)