---
title: I/O 시간(스레드 뷰) | Microsoft Docs
description: I/O 시간 세그먼트를 I/O로 분류되는 차단 시간과 연결하여 I/O 작업이 완료될 때까지 스레드가 대기하고 있음을 나타내는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915ab6aef595fba7e13321d4e23c08bdd2eadaf3
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721634"
---
# <a name="io-time-threads-view"></a>I/O 시간(스레드 뷰)
타임라인의 이러한 세그먼트는 I/O로 분류되는 차단 시간과 관련이 있습니다. 즉, 스레드는 I/O 작업이 끝나기를 대기하고 있습니다. 스레드는 API에서 차단되거나 동시성 시각화 도우미가 I/O로 계산하는 I/O 관련 커널 대기에 의해 차단되었을 수 있습니다. `CreateFile()`, `ReadFile()` 및 `WSARecv()` 등의 API는 이 그룹에 속합니다.

## <a name="see-also"></a>참조
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)