---
title: 호출 트리 뷰 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b932d5f9e4a178c94f3e490c66cec64648ce4f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773337"
---
# <a name="call-tree-view"></a>호출 트리 뷰
호출 트리 뷰는 프로파일링된 애플리케이션에서 트래버스된 함수 실행 경로를 표시합니다. 트리의 루트는 애플리케이션 또는 구성 요소에 대한 진입점입니다. 각 함수 노드에는 호출한 모든 함수 및 이러한 함수 호출에 대한 성능 데이터가 나열됩니다.

 호출 트리 뷰를 확장하여 시간을 가장 많이 사용했거나 가장 자주 샘플링된 함수의 실행 경로를 강조 표시할 수도 있습니다. 가장 성능 비용이 높은 경로를 표시하려면 함수를 마우스 오른쪽 단추로 클릭한 다음 **실행 부하 과다 경로 확장**을 클릭합니다.

 프로파일링 실행 시 각 프로세스는 루트 노드로 표시됩니다. 시작 노드로 설정하려는 노드를 마우스 오른쪽 단추로 클릭한 다음 **루트 설정**을 선택하여 호출 트리 뷰의 시작 노드를 설정할 수 있습니다.

 루트 노드를 설정하면 선택한 노드의 하위 트리를 제외한 다른 모든 항목이 뷰에서 제거됩니다. 루트 노드를 보고 있던 노드로 다시 설정할 수 있습니다. 호출 트리 뷰 창에서 **루트 다시 설정**을 마우스 오른쪽 단추로 클릭한 다음 선택합니다.

 열을 추가하거나 제거하도록 호출 트리 뷰를 사용자 지정할 수 있습니다. **열 이름 제목 표시줄**을 마우스 오른쪽 단추로 클릭한 다음 **열 추가/제거**를 선택합니다.

 제공되는 데이터 양을 제한하여 노이즈 감소를 위한 호출 트리 뷰를 구성할 수 있습니다. 노이즈 감소를 사용하면 뷰에서 성능 문제가 더 두드러집니다. 성능 문제를 쉽게 구분할 수 있을 때 분석이 더 쉽습니다. 자세한 내용은 [방법: 보고서 뷰에서 노이즈 감소 구성](../profiling/how-to-configure-noise-reduction-in-report-views.md)을 참조하세요.

> [!NOTE]
> 노이즈 감소가 활성화된 경고를 표시하도록 구성된 경우 알림 표시줄이 보고서에 표시됩니다.

 호출 트리 뷰에서 열의 정의에 대한 자세한 내용은 다음을 참조하세요.

- [호출 트리 뷰](../profiling/call-tree-view-sampling-data.md)

- [호출 트리 뷰](../profiling/call-tree-view-instrumentation-data.md)

- [호출 트리 뷰 - 샘플링](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [호출 트리 뷰](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>참고 항목
- [성능 보고서 뷰](../profiling/performance-report-views.md)
- [계측 데이터 값 이해](../profiling/understanding-instrumentation-data-values.md)
- [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)
