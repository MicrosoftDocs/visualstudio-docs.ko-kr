---
title: 스레드 정보 뷰 - 경합 데이터 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 679fd9fd039fa903f5df5a479fa4f0e119bb7a9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778169"
---
# <a name="thread-details-view---contention-data"></a>스레드 정보 뷰 - 경합 데이터
스레드 정보 뷰에는 리소스 간의 경합으로 인해 프로파일링 실행의 선택한 스레드에서 발생한 차단 이벤트의 시간 표시 막대 그래프가 표시됩니다. 다른 스레드가 리소스에 대한 액세스를 잠가 스레드가 실행을 일시 중단해야 했던 경우 차단 이벤트가 발생합니다.

 이 뷰는 스레드의 실행 시간 표시 막대를 가로 막대로, 차단 이벤트를 스레드에 대한 가로 시간 표시 막대의 세로 막대로 나타냅니다. 필요한 경우 시간 표시 막대의 섹션을 확대하여 개별 이벤트를 확인할 수 있습니다. 이벤트를 발생시킨 함수의 실행 경로를 확인하려면 이벤트 막대를 클릭합니다. 그러면 **호출 스택** 창에 함수가 표시됩니다. 함수의 소스 코드를 사용할 수 있는 경우, 함수 이름을 클릭하여 Visual Studio IDE에서 소스 파일을 편집할 수 있습니다.

## <a name="navigate-the-timeline"></a>타임라인 탐색

#### <a name="to-zoom-in-on-a-timeline-segment"></a>시간 표시 막대 세그먼트를 확대하려면

- 마우스 포인터를 클릭한 다음 끌어 시간 표시 막대의 영역을 선택합니다.

     마우스를 놓으면 뷰가 선택한 시간 세그먼트로 확대됩니다. 이 프로세스를 반복하여 더 자세한 내용이 표시되도록 확대할 수 있습니다. 시간 스크롤 막대의 스크롤 상자는 뷰에 표시되는 시간 세그먼트의 상대 크기를 나타냅니다.

#### <a name="to-zoom-out-on-a-timeline"></a>시간 표시 막대를 축소하려면

- **축소**를 클릭하여 이전 확대/축소 수준으로 돌아갑니다.

- **확대/축소 다시 설정**을 클릭하여 뷰의 전체 시간 표시 막대를 표시합니다.

#### <a name="to-view-the-call-stack-of-an-event"></a>이벤트의 호출 스택을 보려면

- 타임라인 그래프에서 이벤트를 나타내는 세로 막대를 클릭합니다.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>호출 스택의 함수 소스 코드를 보거나 편집하려면

- **호출 스택** 창에서 함수 이름을 클릭합니다.

  함수 소스 코드는 현재 프로젝트의 일부여야 합니다.

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>프로파일링 실행에서 모든 스레드에 포함된 리소스의 경합 이벤트를 확인하려면

- 타임라인 그래프에서 리소스의 이름이나 ID를 클릭합니다.

     선택한 리소스의 [리소스 정보 뷰](../profiling/resource-details-view-contention-data.md)가 나타납니다.

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>프로세스 창에서 스레드 경합 데이터를 보려면

- 시간 표시 막대 그래프에서 **전체**를 클릭합니다.

     [프로세스 뷰](../profiling/process-view-contention-data.md)가 선택한 스레드와 함께 나타납니다.
