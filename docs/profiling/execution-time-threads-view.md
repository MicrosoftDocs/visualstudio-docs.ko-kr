---
title: 실행 시간(스레드 뷰) | Microsoft 문서
description: 동시성 시각화 도우미의 스레드 뷰에서 실행 시간을 검토합니다. 실행 시간은 스레드가 논리 코어에서 활발히 작동하는 경우를 표시하는 세그먼트로 표현됩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f26df8f724d4a17f55ea54c3e7c61e5e1630e635
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801480"
---
# <a name="execution-time-threads-view"></a>실행 시간(스레드 뷰)
스레드가 시스템의 논리 코어에서 활발히 작업을 수행할 경우 스레드 뷰 타임라인의 이러한 세그먼트는 실행 시간을 나타냅니다.

 스레드 상태가 변경되면 커널 컨텍스트 스위치 이벤트를 통해 감지됩니다. ETW(Windows용 이벤트 추적)는 밀리초마다 샘플 스택을 캡처합니다. 매우 짧은 녹색 세그먼트에서는 샘플이 수집되지 않을 수 있습니다. 따라서 일부 짧은 실행 세그먼트는 호출 스택을 표시하지 않을 수 있습니다.

 실행 세그먼트를 클릭하면 동시성 시각화 도우미가 클릭 위치에 가장 가까운 샘플 스택을 표시합니다. 해당 샘플 스택의 위치는 검은색 화살표 또는 캐럿으로 표시되고 샘플 스택이 **현재** 탭에 나타납니다.

 현재 뷰에서 모든 실행 세그먼트에 대한 기존 방식의 샘플링 프로필을 보려면 표시되는 시간 표시 막대 프로필에서 **실행** 을 클릭합니다.

## <a name="see-also"></a>추가 정보
- [실행 프로필 보고서](../profiling/execution-profile-report.md)
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)