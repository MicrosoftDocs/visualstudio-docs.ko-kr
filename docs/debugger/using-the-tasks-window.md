---
title: 작업 창 사용 | Microsoft Docs
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32dc6372a6ce4983e9bd11e05a4a662d0ad44ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62901603"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>작업 창 사용(C#, Visual Basic, C++)

**작업** 창은 **스레드** 창과 비슷하지만, 각 스레드 대신 <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class) 또는 [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10)) 개체에 대한 정보가 표시된다는 점이 다릅니다. 스레드와 마찬가지로, 작업은 동시에 실행할 수 있는 비동기 작업을 나타내지만 여러 작업이 같은 스레드에서 실행될 수도 있습니다.

관리 코드에서 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 개체 또는 **await** 및 **async** 키워드(Visual Basic에서는 **Await** 및 **Async**)로 작업할 때 **작업** 창을 사용할 수 있습니다. 관리 코드에서의 작업에 대한 자세한 내용은 [병렬 프로그래밍](/dotnet/standard/parallel-programming/index)을 참조하세요.

네이티브 코드에서 [작업 그룹](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [병렬 알고리즘](/cpp/parallel/concrt/parallel-algorithms), [비동기 에이전트](/cpp/parallel/concrt/asynchronous-agents) 및 [간단한 작업](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)으로 작업할 때 **작업** 창을 사용할 수 있습니다. 네이티브 코드의 작업에 대한 자세한 내용은 [동시성 런타임](/cpp/parallel/concrt/concurrency-runtime)을 참조하세요.

JavaScript에서 프라미스 `.then` 코드로 작업하는 경우 작업 창을 사용할 수 있습니다. 자세한 내용은 [Asynchronous programming in JavaScript(UWP apps)](/previous-versions/windows/apps/hh700330(v=win.10))(JavaScript의 비동기 프로그래밍(UWP 앱))를 참조하세요.

중단하고 디버거를 시작할 때마다 **작업** 창을 사용할 수 있습니다. **디버그** 메뉴에서 **창**을 클릭하고 **작업**을 클릭하여 작업 창에 액세스할 수 있습니다. 다음 그림에서는 기본 모드의 **작업** 창을 보여 줍니다.

![작업 창](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> 관리 코드에서 상태가 [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>) 또는 [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>)인 <xref:System.Threading.Tasks.Task>는 관리형 스레드가 일시 중지 또는 조인 상태인 경우 **작업** 창에 표시되지 않을 수도 있습니다.

## <a name="tasks-column-information"></a>작업 열 정보

**작업** 창의 열에는 다음 정보가 표시됩니다.

|열 이름|설명|
|-----------------|-----------------|
|**플래그**|플래그 설정된 작업이 표시되며 작업에 플래그를 설정하거나 해제할 수 있습니다.|
|**아이콘**|노란색 화살표는 현재 작업을 나타냅니다. 현재 작업은 현재 스레드의 최상위 작업입니다.<br /><br /> 흰색 화살표는 중단 작업(디버거가 호출된 현재 작업)을 나타냅니다.<br /><br /> 일시 중지 아이콘은 사용자가 중지한 작업을 나타냅니다. 목록에서 작업을 마우스 오른쪽 단추로 클릭하여 작업을 중지하거나 중지된 작업을 해제할 수 있습니다.|
|**ID**|시스템에서 제공한 작업 번호입니다. 네이티브 코드에서는 작업의 주소입니다.|
|**Status**|작업의 현재 상태(예약됨, 활성, 차단됨, 교착 상태, 대기 중 또는 완료됨)입니다. 예약된 작업은 아직 실행되지 않은 작업이므로 호출 스택, 할당된 스레드 또는 관련 작업이 없습니다.<br /><br /> 활성 작업은 디버거를 시작하기 전에 코드를 실행 중이던 작업입니다.<br /><br /> 대기 중이거나 차단된 작업은 이벤트가 신호를 받거나, 잠금이 해제되거나, 다른 작업이 완료되기를 기다리고 있어서 차단된 작업입니다.<br /><br /> 교차 상태의 작업은 해당 스레드와 다른 스레드 간에 교착 상태가 발생한 대기 중인 작업입니다.<br /><br /> 교착 상태의 작업 또는 대기 중인 작업의 **상태** 셀을 가리키면 블록에 대한 자세한 정보를 볼 수 있습니다. **경고:**  **작업** 창에서는 WCT(Wait Chain Traversal)에서 지원되는 동기화 기본 형식을 사용하는 차단된 작업에 대해서만 교착 상태가 보고됩니다. 예를 들어 WCT를 사용하는 <xref:System.Threading.Tasks.Task> 개체에서 교착 상태가 발생한 경우 디버거에서는 **대기 중-교착 상태**를 보고합니다. 동시성 런타임에서 관리되지 않으며 WCT를 사용하지 않는 작업에서 교착 상태가 발생한 경우에는 디버거에서 **대기 중**을 보고합니다. WCT에 대한 자세한 내용은 [Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal)을 참조하세요.|
|**시작 시간**|작업이 활성화된 시간입니다.|
|**기간**|작업이 활성화된 기간(초)입니다.|
|**완료 시간**|작업이 완료된 시간입니다.|
|**위치**|작업의 호출 스택의 현재 위치입니다. 이 셀을 가리키면 작업에 대한 전체 호출 스택을 볼 수 있습니다. 예약된 작업의 이 열에는 값이 없습니다.|
|**Task**|작업이 생성될 때 작업으로 전달된 초기 메서드와 인수입니다.|
|**AsyncState**|관리 코드의 경우 작업 상태입니다. 기본적으로 이 열은 숨겨집니다. 이 열을 표시하려면 열 머리글 중 하나에 대한 상황에 맞는 메뉴를 엽니다. **열**, **AsyncState**를 선택합니다.|
|**부모**|이 작업을 만든 작업의 ID입니다. 비어 있으면 작업에 부모가 없는 것입니다. 관리되는 프로그램에만 적용됩니다.|
|**스레드 할당**|작업이 실행 중인 스레드의 ID 및 이름입니다.|
|**AppDomain**|관리 코드의 경우 작업이 실행되고 있는 애플리케이션 도메인입니다.|
|**task_group**|네이티브 코드의 경우 작업을 예약한 [task_group](/cpp/parallel/concrt/reference/task-group-class) 개체의 주소입니다. 비동기 에이전트 및 간단한 작업의 경우 이 열은 0으로 설정됩니다.|
|**Process**|작업이 실행 중인 프로세스의 ID입니다.|

 열 머리글을 마우스 오른쪽 단추로 클릭하고 원하는 열을 선택하여 뷰에 추가할 수 있습니다. 열을 제거하려면 선택을 취소합니다. 또한 왼쪽이나 오른쪽으로 끌어서 열의 순서를 바꿀 수도 있습니다. 열 바로 가기 메뉴가 다음 그림에 표시됩니다.

 ![작업 창의 바로 가기 뷰 메뉴](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>작업 정렬
 열 조건으로 작업을 정렬하려면 열 머리글을 클릭합니다. 예를 들어 **ID** 열 머리글을 클릭하여 1, 2, 3, 4, 5 등의 작업 ID에 따라 작업을 정렬할 수 있습니다. 정렬 순서를 반대로 바꾸려면 열 머리글을 다시 클릭합니다. 현재 정렬 열과 정렬 순서는 열에 화살표로 표시됩니다.

## <a name="grouping-tasks"></a>작업 그룹화
 목록 뷰에서 열을 기준으로 작업을 그룹화할 수 있습니다. 예를 들어, **상태** 열 머리글을 마우스 오른쪽 단추로 클릭하고 **상태별 그룹** > **[*status*]** 를 클릭하면 동일한 상태의 모든 작업을 그룹화할 수 있습니다. 예를 들어, 대기 중인 작업만 빨리 확인하여 차단된 이유를 살펴볼 수 있습니다. 또한 디버그 세션 중에 관심 없는 그룹을 축소할 수도 있습니다. 동일한 방식으로 다른 열을 기준으로 그룹화할 수 있습니다. 그룹 머리글 옆의 단추를 클릭하여 간단하게 그룹에 플래그를 설정하거나 해제할 수 있습니다. 다음 그림에서는 그룹화된 모드의 **작업** 창을 보여 줍니다.

 ![작업 창의 그룹화된 모드](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>부모 자식 뷰
 이 뷰는 관리 코드에만 사용할 수 있습니다. **상태** 열 머리글을 마우스 오른쪽 단추로 클릭하고 **그룹화 방법** > **부모**를 클릭하여 작업 목록을 계층적 뷰로 변경할 수 있습니다. 계층적 뷰에서 모든 자식 작업은 해당 부모 아래에 표시하거나 숨길 수 있는 하위 노드입니다.

## <a name="flagging-tasks"></a>작업에 플래그 설정
 작업 목록 항목을 선택한 후 상황에 맞는 메뉴에서 **플래그 할당 스레드**를 선택하거나 첫 번째 열에서 플래그 아이콘을 클릭하여 작업이 실행 중인 스레드에 플래그를 지정할 수 있습니다. 여러 작업에 플래그를 설정하는 경우 플래그 설정된 작업에만 초점을 맞출 수 있도록 플래그 설정된 모든 작업을 맨 위로 오게 플래그 열을 정렬할 수 있습니다. **병렬 스택** 창을 사용하여 플래그 설정된 작업만 볼 수도 있습니다. 이렇게 하면 디버깅 중 관심 없는 작업을 필터링할 수 있습니다. 플래그는 디버깅 세션 간에 유지되지 않습니다.

## <a name="freezing-and-thawing-tasks"></a>작업 중지 및 재개
 작업 목록 항목을 마우스 오른쪽 단추로 클릭하고 **할당된 스레드 중지**를 클릭하여 작업이 실행되고 있는 스레드를 중지할 수 있습니다. 작업이 이미 중지되었으면 **할당된 스레드 재개** 명령이 표시됩니다. 스레드를 중지하면 현재 중단점 이후에 코드를 단계별로 실행할 때 해당 스레드가 실행되지 않습니다. **이 스레드를 제외한 모든 스레드 중지** 명령은 작업 목록 항목을 실행 중인 스레드를 제외한 모든 스레드를 중지합니다.

 다음 그림에서는 각 작업에 대한 다른 메뉴 항목을 보여 줍니다.

 ![작업 창의 바로 가기 스레드 메뉴](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>활성 작업 또는 프레임 전환

**작업으로 전환** 명령은 현재 작업이 활성 작업이 되도록 합니다. **프레임으로 전환** 명령은 선택한 스택 프레임이 활성 스택 프레임이 되도록 합니다. 디버거 컨텍스트는 현재 작업 또는 선택한 스택 프레임으로 전환됩니다.

## <a name="see-also"></a>참조

- [디버거 소개](../debugger/debugger-feature-tour.md)
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [병렬 프로그래밍](/dotnet/standard/parallel-programming/index)
- [동시성 런타임](/cpp/parallel/concrt/concurrency-runtime)
- [병렬 스택 창 사용](../debugger/using-the-parallel-stacks-window.md)
- [연습: 병렬 애플리케이션 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md)