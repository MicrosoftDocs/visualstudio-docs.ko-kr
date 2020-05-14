---
title: UI 처리 시간 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "63004456"
---
# <a name="ui-processing-time"></a>UI 처리 시간
타임라인의 이러한 세그먼트는 UI 처리로 분류되는 차단 시간과 관련이 있습니다. 이는 스레드가 Windows 메시지를 펌핑 중이거나 다른 UI(사용자 인터페이스) 작업을 수행 중임을 의미합니다. 이 시간 동안 스레드는 동시성 시각화 도우미가 UI 처리로 간주되는 API에서 차단되었습니다. `GetMessage()` 및 `MsgWaitForMultipleObjects()` 등의 API는 이 그룹에 속합니다.

 미리 정의된 차단 API가 식별되지 않은 경우 호출 스택 및 프로필 보고서를 검토하여 지연의 근본 원인을 확인합니다.

 UI 처리 범주는 GUI 애플리케이션의 응답성을 이해하는 데 도움이 되며 UI 응답성에 종속된 애플리케이션에서 유용합니다. 예를 들어 애플리케이션의 UI 스레드가 UI 처리에서 100% 시간을 달성하는 경우 반응이 빠릅니다. 그러나 UI 스레드가 다른 범주에서 상당한 시간을 소요하는 경우 근본 원인을 찾고 해당 스레드에서 UI가 아닌 범주를 줄이기 위한 옵션을 고려합니다.

## <a name="see-also"></a>참고 항목
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)