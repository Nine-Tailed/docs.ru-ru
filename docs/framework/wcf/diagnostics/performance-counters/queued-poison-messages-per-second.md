---
title: Количество подозрительных сообщений из очереди в секунду
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509343"
---
# <a name="queued-poison-messages-per-second"></a>Количество подозрительных сообщений из очереди в секунду
Имя счетчика: Queued Poison Messages Per Second.  
  
## <a name="description"></a>Описание  
 Количество сообщений, отмеченных как подозрительные транспортом очередей в этой службе в секунду.  
  
 Этот счетчик является счетчиком производительности типа [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), значение которого вычисляется по следующей формуле.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
