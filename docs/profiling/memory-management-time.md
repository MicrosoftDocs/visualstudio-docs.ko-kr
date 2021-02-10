---
title: 메모리 관리 시간 | Microsoft 문서
description: 이 시나리오에서 스레드가 페이징 같은 메모리 관리 작업과 연결된 이벤트에 의해 차단됨을 의미하는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad3c913e6c983749e53940f5e75ad3bdba48bf92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873634"
---
# <a name="memory-management-time"></a>메모리 관리 시간
타임라인의 이러한 세그먼트는 메모리 관리로 분류되는 차단 시간과 관련이 있습니다. 이 시나리오는 스레드가 페이징 같은 메모리 관리 작업 관련 이벤트에 의해 차단됨을 의미합니다. 이 시간 동안 스레드는 동시성 시각화 도우미가 메모리 관리로 간주되는 API 또는 커널 상태에서 차단되었습니다. 여기에는 페이징 및 메모리 할당과 같은 이벤트가 포함됩니다.

 연관된 호출 스택 및 프로필 보고서를 조사해서 해당 블록이 메모리 관리로 분류되는 기본 이유를 자세히 이해할 수 있습니다.

## <a name="see-also"></a>참조
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)