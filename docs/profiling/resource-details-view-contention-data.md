---
title: 리소스 정보 뷰 - 경합 데이터 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e66432fd2f5d8b1532bece9d76e7dfc2a261e4b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771605"
---
# <a name="resource-details-view---contention-data"></a>리소스 정보 뷰 - 경합 데이터
리소스 정보 뷰에는 선택한 리소스에 대한 경합으로 인해 발생한 차단 이벤트의 시간 표시 막대 그래프가 표시됩니다. 다른 스레드가 리소스에 대한 액세스를 잠가 스레드가 실행을 일시 중단해야 했던 경우 차단 이벤트가 발생합니다.

 이 뷰는 각 스레드의 실행 시간 표시 막대를 가로 막대로, 각 차단 이벤트를 스레드 시간 표시 막대의 세로 막대로 나타냅니다. 필요한 경우 시간 표시 막대의 섹션을 확대하여 개별 이벤트를 확인할 수 있습니다. 이벤트를 발생시킨 함수의 실행 경로(호출 스택)를 확인하려면 이벤트 막대를 클릭합니다. 그러면 **호출 스택** 창에 함수가 표시됩니다. 함수의 소스 코드를 사용할 수 있는 경우, 함수 이름을 클릭하여 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 인터페이스에서 소스 파일을 편집할 수 있습니다.

## <a name="procedures"></a>프로시저

#### <a name="to-magnify-a-timeline-segment"></a>시간 표시 막대 세그먼트를 확대하려면

- 시간 표시 막대의 영역 위로 마우스 포인터를 끕니다.

     마우스 단추를 놓으면 뷰가 선택한 시간 세그먼트로 확대됩니다. 이 프로세스를 반복하여 세그먼트를 추가로 확대할 수 있습니다. 시간 스크롤 막대의 스크롤 상자는 뷰에 표시되는 시간 세그먼트의 상대 크기를 나타냅니다.

#### <a name="to-zoom-out-on-a-timeline"></a>시간 표시 막대를 축소하려면

- 다음 단계 중 하나를 수행합니다.

  - **축소**를 클릭하여 이전 확대/축소 수준으로 돌아갑니다.

  - **확대/축소 다시 설정**을 클릭하여 뷰의 전체 시간 표시 막대를 표시합니다.

#### <a name="to-view-the-call-stack-of-an-event"></a>이벤트의 호출 스택을 보려면

- 시간 표시 막대 그래프에서 이벤트 막대를 클릭합니다.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>호출 스택의 함수 소스 코드를 보거나 편집하려면

- **호출 스택** 창에서 함수 이름을 클릭합니다.

  함수 소스 코드는 현재 프로젝트의 일부여야 합니다.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>리소스에 대한 경합 이벤트 호출 트리를 보려면

- 시간 표시 막대 그래프에서 **전체**를 클릭합니다.

     리소스에 대한 리소스 경합 뷰가 표시됩니다. 자세한 내용은 [리소스 경합 뷰](../profiling/resource-contentions-view-contention-data.md)를 참조하세요.

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>스레드의 모든 경합 이벤트를 보려면

- 시간 표시 막대 그래프에서 스레드의 이름이나 ID를 클릭합니다.

     선택한 스레드의 스레드 정보 뷰가 나타납니다. 자세한 내용은 [스레드 정보 뷰](../profiling/thread-details-view-contention-data.md)를 참조하세요.
