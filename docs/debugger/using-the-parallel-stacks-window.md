---
title: 병렬 스택 창의 스레드 뷰 | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9728346bc4c6d805bb0febd3a0d5bef0ed809a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62902423"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>병렬 스택 창에서 스레드 및 작업 뷰(C#, Visual Basic, C++)

**병렬 스택** 창은 다중 스레드 애플리케이션을 디버깅할 때 유용합니다. 다음과 같은 여러 뷰가 있습니다.

- [스레드 뷰](#threads-view)는 앱의 모든 스레드에 대한 호출 스택 정보를 표시합니다. 따라서 스레드와 스레드 스택 프레임 간을 탐색할 수 있습니다.

- [작업 뷰](#tasks-view)는 작업 중심의 호출 스택 정보를 표시합니다.
  - 관리되는 코드에서 **작업** 뷰는 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 개체의 호출 스택이 표시됩니다.
  - 네이티브 코드에서 **작업** 뷰는 [작업 그룹](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [병렬 알고리즘](/cpp/parallel/concrt/parallel-algorithms), [비동기 에이전트](/cpp/parallel/concrt/asynchronous-agents) 및 [간단한 작업](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)의 호출 스택이 표시됩니다.

- [메서드 뷰](#method-view)는 선택한 메서드에서 호출 스택을 회전합니다.

## <a name="use-the-parallel-stacks-window"></a>병렬 스택 창 사용

**병렬 스택** 창을 열려면 디버깅 세션에 있어야 합니다. **디버그** > **창** > **병렬 스택**을 선택합니다.

### <a name="toolbar-controls"></a>도구 모음 컨트롤

**병렬 스택** 창에는 다음과 같은 도구 모음 컨트롤이 있습니다.

![병렬 스택 창의 도구 모음](../debugger/media/parallel_stackstoolbar.png "병렬 스택 도구 모음")

|아이콘|컨트롤|설명|
|-|-|-|
|![스레드/작업 콤보 상자](media/parallel_toolbar1.png "스레드/작업 콤보 상자")|**스레드**/**작업** 콤보 상자|스레드의 호출 스택과 작업의 호출 스택 간에 뷰를 전환합니다. 자세한 내용은 [작업 뷰](#tasks-view)와 [스레드 뷰](#threads-view)를 참조하세요.|
|![플래그가 지정된 항목만 표시 아이콘](media/parallel_toolbar2.png "플래그가 지정된 항목만 표시 아이콘")|플래그가 지정된 항목만 표시|**GPU 스레드** 창, **병렬 조사식** 창 등의 다른 디버거 창에서 플래그가 지정된 스레드에 대해서만 호출 스택을 표시합니다.|
|![메서드 뷰 설정/해제 아이콘](media/parallel_toolbar3.png "메서드 뷰 설정/해제 아이콘")|**메서드 뷰** 설정/해제|호출 스택 뷰와 **메서드 뷰** 사이를 전환합니다. 자세한 내용은 [메서드 뷰](#method-view)를 참조하세요.|
|![현재로 자동 스크롤 아이콘](media/parallel_toolbar4.png "현재로 자동 스크롤 아이콘")|현재 스택 프레임으로 자동 스크롤|현재 스택 프레임이 뷰에 표시되도록 그래프를 자동 스크롤합니다. 이 기능은 다른 창에서 현재 스택 프레임을 변경하거나 큰 그래프에서 새 중단점을 적중할 때 유용합니다.|
|![확대/축소 설정/해제 아이콘](media/parallel_toolbar5.png "확대/축소 설정/해제 아이콘")|확대/축소 컨트롤 설정/해제|창 왼쪽에 있는 확대/축소 컨트롤을 표시하거나 숨깁니다. <br /><br />확대/축소 컨트롤의 표시 여부와 관계없이 **Ctrl**을 누르면서 마우스 휠을 돌려서 확대 축소하거나 **Ctrl**+**Shift**+ **+** 를 눌러 확대하고 **Ctrl**+**Shift**+ **-** 를 눌러 축소할 수 있습니다. |

### <a name="stack-frame-icons"></a>스택 프레임 아이콘
다음 아이콘은 모든 뷰의 활성 및 현재 스택 프레임에 대한 정보를 제공합니다.

|아이콘|설명|
|-|-|
|![노란색 화살표](media/icon_parallelyellowarrow.gif)|현재 스레드의 현재 위치(활성 스택 프레임)를 나타냅니다.|
|![스레드 아이콘](media/icon_parallelthreads.gif)|현재가 아닌 스레드의 현재 위치(활성 스택 프레임)를 나타냅니다.|
|![녹색 화살표](media/icon_parallelgreenarrow.gif)|현재 스택 프레임(현재 디버거 컨텍스트)을 나타냅니다. 메서드 이름은 표시되는 위치와 관계없이 굵게 표시됩니다.|

### <a name="context-menu-items"></a>컨텍스트 메뉴 항목
**스레드** 뷰 또는 **작업** 뷰에서 메서드를 마우스 오른쪽 단추로 클릭하면 다음과 같은 바로 가기 메뉴 항목을 사용할 수 있습니다. 마지막 6개 항목은 [호출 스택 창](how-to-use-the-call-stack-window.md)과 동일합니다.

![병렬 스택 창의 바로 가기 메뉴](../debugger/media/parallel_contmenu.png "병렬 스택 창의 바로 가기 메뉴")

|Menu item|설명|
|-|-|
|**플래그**|선택한 항목에 플래그를 지정합니다.|
|**플래그 해제**|선택한 항목의 플래그를 해제합니다.|
|**중지**|선택한 항목을 중지합니다.|
|**재개**|선택한 항목을 재개합니다.|
|**프레임으로 전환**|**호출 스택** 창의 해당 메뉴 명령과 동일합니다. 그러나 **병렬 스택** 창에서는 하나의 메서드가 여러 프레임에 있을 수 있습니다. 이 항목에 대한 하위 메뉴에서 원하는 프레임을 선택할 수 있습니다. 스택 프레임 중 하나가 현재 스레드에 있는 경우 해당 프레임은 하위 메뉴에서 기본적으로 선택됩니다.|
|**작업으로 이동** 또는 **스레드로 이동**|**작업** 또는 **스레드** 뷰로 전환하고 동일한 스택 프레임을 계속 강조 표시합니다.|
|**소스 코드로 이동**|소스 코드 창의 해당 위치로 이동합니다. |
|**디스어셈블리로 이동**|**디스어셈블리** 창의 해당 위치로 이동합니다.|
|**외부 코드 표시**|외부 코드를 표시하거나 숨깁니다.|
|**16진수 표시**|10진수 표시와 16진수 표시 간을 전환합니다.|
|**소스의 스레드 표시**|소스 코드 창에서 스레드의 위치에 플래그를 지정합니다. |
|**기호 로드 정보**|**기호 로드 정보** 대화 상자를 엽니다.|
|**기호 설정**|**기호 설정** 대화 상자를 엽니다. |

## <a name="threads-view"></a>스레드 뷰

**스레드** 뷰에서 현재 스레드의 스택 프레임 및 호출 경로가 파란색으로 강조 표시됩니다. 스레드의 현재 위치는 노란색 화살표로 표시됩니다.

현재 스택 프레임을 변경하려면 다른 메서드를 두 번 클릭합니다. 이렇게 하면 선택한 메서드가 현재 스레드의 일부인지 아니면 다른 스레드의 일부인지에 따라 현재 스레드가 전환될 수도 있습니다.

**스레드** 뷰 그래프가 너무 커서 창에 맞지 않는 경우 창에 **개요 보기** 컨트롤이 나타납니다. 컨트롤에서 프레임을 이동하여 그래프의 다른 부분으로 이동할 수 있습니다.

다음 그림에서는 메인에서 관리-네이티브 코드 전환으로 이동하는 하나의 스레드를 보여 줍니다. 6개의 스레드가 현재 메서드에 있습니다. 하나는 Thread.Sleep으로 계속하고 다른 하나는 Console.WriteLine에서 SyncTextWriter.WriteLine으로 계속합니다.

 ![병렬 스택 창의 스레드 뷰](../debugger/media/parallel_stack1.png "병렬 스택 창의 스레드 뷰")

다음 표에서는 **스레드** 보기의 주요 기능에 대해 설명합니다.

|설명선|요소 이름|설명|
|-|-|-|
|1|호출 스택 세그먼트 또는 노드|하나 이상의 스레드에 대한 일련의 메서드를 포함합니다. 프레임에 연결된 화살표 선이 없으면 스레드에 대한 전체 호출 경로를 나타냅니다.|
|2|파란색 강조 표시|현재 스레드의 호출 경로를 나타냅니다.|
|3|화살표 선|노드를 연결하여 스레드에 대한 전체 호출 경로를 구성합니다.|
|4|노드 헤더|노드에 대한 프로세스 및 스레드 수를 표시합니다.|
|5|메서드|동일한 메서드에 있는 하나 이상의 스택 프레임을 나타냅니다.|
|6|메서드에 대한 도구 설명|메서드를 가리키면 표시됩니다. **스레드** 뷰에서 도구 모음은 **스레드** 창과 유사한 표에 모든 스레드를 표시합니다. |

## <a name="tasks-view"></a>작업 보기
앱이 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 개체(관리 코드) 또는 `task_handle` 개체(네이티브 코드)를 사용하여 병렬 처리를 표현하는 경우 **작업** 뷰를 사용할 수 있습니다. **작업** 보기에는 스레드 대신 작업의 호출 스택이 표시됩니다.

**작업 뷰**:

- 작업을 실행하고 있지 않은 스레드의 호출 스택은 표시되지 않습니다.
- 작업을 실행 중인 스레드의 호출 스택은 맨 위와 맨 아래에서 시각적으로 잘려 작업에 대해 관련성이 가장 높은 프레임을 표시합니다.
- 여러 작업이 한 스레드에 있으면 이러한 작업의 호출 스택이 개별 노드에 표시됩니다.

전체 호출 스택을 보려면 스택 프레임을 마우스 오른쪽 단추로 클릭하고 **스레드로 이동**을 클릭하여 **스레드** 뷰로 전환하면 됩니다.

다음 그림은 상단의 **스레드** 뷰와 하단의 **작업** 뷰를 보여 줍니다.

![스레드 및 작업 뷰](../debugger/media/parallel_threads-tasks.png "스레드 및 작업 뷰")

메서드를 마우스로 가리키면 추가 정보가 포함된 도구 설명이 표시됩니다. **작업** 뷰에서 도구 설명에는 **작업** 창과 유사한 테이블에 모든 작업이 표시됩니다.

다음 이미지는 상단에 **스레드** 뷰의 메서드에 대한 도구 설명 및 하단에 해당하는 **작업** 뷰를 보여 줍니다.

![스레드 및 작업 도구 설명](../debugger/media/parallel_threads-tasks-tooltips.png "스레드 및 작업 도구 설명")

## <a name="method-view"></a>메서드 뷰
**스레드** 뷰나 **작업** 뷰에서 도구 모음의 **메서드 뷰 토글** 아이콘을 선택하여 현재 메서드를 축으로 그래프를 회전할 수 있습니다. **메서드 **뷰에서는 현재 메서드를 호출하거나 현재 메서드에 의해 호출되는 모든 스레드에 대한 메서드를 모두 한눈에 볼 수 있습니다. 다음 그림에서는 왼쪽의 **스레드** 뷰와 오른쪽의 **메서드** 뷰에서 동일한 정보를 표시하는 방법을 보여 줍니다.

![스레드 뷰 및 메서드 뷰](../debugger/media/parallel_methodview.png "스레드 뷰 및 메서드 뷰")

새 스택 프레임으로 전환하는 경우 해당 메서드는 현재 메서드가 되고 **메서드 뷰**는 새 메서드에 대한 모든 호출자 및 호출 수신자를 표시합니다. 이렇게 하면 메서드가 호출 스택에 표시되는지 여부에 따라 일부 스레드가 뷰에 나타나거나 사라집니다. 호출 스택 뷰로 돌아가려면 **메서드 뷰** 도구 모음 아이콘을 다시 선택합니다.

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)
- [연습: 병렬 애플리케이션 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [관리 코드 디버깅](../debugger/debugging-managed-code.md)
- [병렬 프로그래밍](/dotnet/standard/parallel-programming/index)
- [작업 창 사용](../debugger/using-the-tasks-window.md)
- [Task 클래스](../extensibility/debugger/task-class-internal-members.md)
