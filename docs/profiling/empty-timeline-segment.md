---
title: 빈 시간 표시 막대 세그먼트 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96cdc7ae4edc7ea7193d5b95dfc73fa1747c1fb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970111"
---
# <a name="empty-timeline-segment"></a>빈 시간 표시 막대 세그먼트
동시성 시각화 도우미에서 타임라인의 섹션이 비어 있는 이유(흰색 배경)는 채널 종류에 따라 달라집니다.

- CPU 스레드 채널의 경우에는 이 타임라인 부분에서 스레드가 존재하지 않았음을 의미합니다. 스레드를 조사하면 확대/축소 컨트롤을 사용하거나 가로로 스크롤해서 실행 중인 섹션을 찾을 수 있습니다.

- I/O 채널의 경우에는 해당 시점에서 대상 프로세스를 대신해서 디스크 액세스가 발생하지 않았음을 의미합니다.

- DirectX 채널의 경우, 이 타임라인 부분에서 대상 프로세스를 대신해서 GPU 작업이 수행되지 않았음을 의미합니다.

- 표식 채널의 경우에는 표식이 생성되지 않았음을 의미합니다.

## <a name="see-also"></a>참고 항목
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)
- [확대/축소 컨트롤(스레드 뷰)](../profiling/zoom-control-threads-view.md)