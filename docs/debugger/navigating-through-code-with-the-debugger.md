﻿---
title: 디버거를 사용 하 여 코드 탐색 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301094"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio 디버거를 통해 코드 탐색

Visual Studio 디버거는 코드를 탐색하여 앱의 상태를 검사하고 실행 흐름을 표시하는 데 도움이 될 수 있습니다. 바로 가기 키, 디버그 명령, 중단점 및 기타 기능을 사용 하여 검사하려는 코드로 신속하게 이동할 수 있습니다. 디버거 탐색 명령 및 바로 가기에 익숙하면 앱 문제를 보다 쉽고 빠르게 찾고 해결할 수 있습니다. 처음으로 코드를 디버깅하는 경우 이 문서를 진행하기 전에 [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)과 [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)을 읽고 오는 것을 추천합니다.

## <a name="get-into-break-mode"></a>"브레이크 모드"로 전환

*중단 모드에서는*함수, 변수 및 개체가 메모리에 남아 있는 동안 앱 실행이 일시 중단됩니다. 디버거가 중단 모드에 있으면 코드를 탐색할 수 있습니다. 브레이크 모드에 빠르게 들어가는 가장 일반적인 방법은 다음 중 하나를 참조하십시오.

- **F10** 또는 **F11을**눌러 코드 단계적 단계적 을 시작합니다. 이렇게 하면 앱의 진입점을 빠르게 찾을 수 있으며 단계 명령을 계속 눌러 코드를 탐색할 수 있습니다.

- 예를 들어 [중단점을 설정하고](using-breakpoints.md) 앱을 시작하여 특정 위치 또는 [함수로 실행합니다.](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)

    예를 들어 Visual Studio의 코드 편집기에서 **커서까지 실행** 명령을 사용하여 앱을 시작하고 디버거를 연결하여 중단 모드로 전환하고 **F11** 키를 눌러 코드를 탐색할 수 있습니다.

   ![커서에 실행 및 코드로 단계](../debugger/media/navigate-code-code-stepping.gif "커서에 실행 및 코드로 단계")

브레이크 모드가 되면 다양한 명령을 사용하여 코드를 탐색할 수 있습니다. 중단 모드에서는 변수 값을 검사하여 위반 또는 버그를 찾을 수 있습니다. 일부 프로젝트 유형의 경우 중단 모드에서 앱을 조정할 수도 있습니다.

**모듈** 및 **Watch** 창과 같은 대부분의 디버거 창은 디버거가 앱에 연결된 경우에만 사용할 수 있습니다. **Locals** 창에서 변수 값을 보거나 **Watch** 창에서 표현식을 평가하는 것과 같은 일부 디버거 기능은 디버거가 일시 중지된 동안(즉, 중단 모드)에만 사용할 수 있습니다.

> [!NOTE]
> 소스 또는*기호(.pdb)* 파일이 로드되지 않은 코드에 침입하면 디버거에 파일을 찾고 로드하는 데 도움이 되는 **소스 파일을 찾을 수 없거나** 찾을 수 없는 **기호** 페이지가 표시됩니다. [기호(.pdb) 및 소스 파일 지정을](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)참조하십시오. 기호 또는 원본 파일을 로드할 수 없는 경우에도 **디스어셈블리** 해제 창에서 어셈블리 명령을 디버깅할 수 있습니다.

## <a name="step-through-code"></a>단계별 코드 실행

디버거 단계 명령은 앱 상태를 검사하거나 실행 흐름에 대해 자세히 알아보는 데 도움이 됩니다.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>코드 줄에 한 줄씩 단계

디버깅하는 동안 각 문을 중지하려면 **디버그** > **단계 입력을**사용하거나 **F11을**누릅니다.

디버거는 실제 줄이 아닌 코드 문을 단계합니다. 예를 들어 한 줄에 `if` 절을 작성할 수 있습니다.

  ```csharp
  int x = 42;
  string s = "Not answered";
  if( int x == 42) s = "Answered!";
  ```

  ```vb
  Dim x As Integer = 42
  Dim s As String = "Not answered"
  If x = 42 Then s = "Answered!"
  ```

그러나 이 줄에 들어서면 디버거는 조건을 한 단계로 처리하고 그 결과는 다른 단계로 처리합니다. 앞의 예제에서 조건은 true입니다.

중첩된 함수 호출인 경우 **한 단계씩 코드 실행** 명령은 가장 안쪽에 중첩된 함수를 한 단계씩 실행합니다. 예를 들어, 같은 `Func1(Func2())`호출에서 **Step Into를** 사용하는 경우 디버거는 함수에 `Func2`단계합니다.

>[!TIP]
>각 코드 줄을 실행하면 변수 위로 마우스를 가져가서 해당 값을 보거나 [지역 변수](autos-and-locals-windows.md) 및 [Watch](watch-and-quickwatch-windows.md) 창을 사용하여 값이 변경되는 것을 볼 수 있습니다. 함수를 단계적화하는 동안 [호출 스택을](how-to-use-the-call-stack-window.md) 시각적으로 추적할 수도 있습니다. (Visual Studio Enterprise전용의 경우 [디버깅하는 동안 호출 스택의 맵 메서드를](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)참조하십시오.)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>코드를 단계별로 단계별로 살펴보고 일부 기능을 건너뛰기

디버깅하는 동안 함수에 대해 신경 쓰지 않거나 잘 테스트된 라이브러리 코드와 같이 함수가 작동한다는 것을 알고 있을 수 있습니다. 다음 명령을 사용하여 코드 단계적 단계적 동안 코드를 건너뛸 수 있습니다. 함수는 계속 실행되지만 디버거는 함수를 건너뜁니다.

|키보드 명령|디버그 메뉴 명령|Description|
|----------------------|------------------|-----------------|
|**F10**|**프로시저 단위 실행**|현재 줄에 함수 호출이 포함된 경우 **Step Over는** 코드를 실행한 다음 호출된 함수가 반환된 후 코드의 첫 번째 줄에서 실행을 일시 중단합니다.|
|**시프트**+**F11**|**프로시저 나가기**|**Step Out은** 코드를 계속 실행하고 현재 함수가 반환될 때 실행을 일시 중단합니다. 디버거는 현재 함수를 건너뜁니다.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>특정 위치 또는 기능으로 실행

검사할 코드를 정확히 알고 있거나 디버깅을 시작할 위치를 알고 있을 때 특정 위치 또는 함수로 직접 실행하는 것이 좋습니다.

### <a name="run-to-a-breakpoint-in-code"></a>코드의 중단점으로 실행

코드에서 간단한 중단점을 설정하려면 실행을 일시 중단하려는 코드 줄 옆의 맨 왼쪽 여백을 클릭합니다. 선을 선택하고 **F9을**누르거나 **디버그** > **토글 중단점을**선택하거나 마우스 오른쪽 단추를 클릭하고 **중단점** > **삽입 중단점을**선택할 수도 있습니다. 중단점은 코드 줄 옆에 왼쪽 여백에 빨간색 점으로 나타납니다. 디버거는 줄이 실행되기 직전에 실행을 일시 중단합니다.

![중단점 설정](../debugger/media/dbg_basics_setbreakpoint.png "중단점 설정")

Visual Studio에서 중단점은 조건부 중단점 및 추적점과 같은 다양한 추가 기능을 제공합니다. 자세한 내용은 [중단점 사용을](../debugger/using-breakpoints.md)참조하십시오.

### <a name="run-to-a-function-breakpoint"></a>함수 중단점으로 실행

지정된 함수에 도달할 때까지 디버거에 실행하도록 지시할 수 있습니다. 함수 이름을 지정하거나 호출 스택에서 함수를 선택할 수 있습니다.

**함수 중단점을 이름으로 지정하려면**

1. **새 중단점** > **함수 중단점** **디버그** > 선택

1. 새 **함수 중단점** 대화 상자에서 함수 이름을 입력하고 해당 언어를 선택합니다.

   ![새 기능 중단점 대화 상자](../debugger/media/dbg_execution_newbreakpoint.png "새 기능 중단점")

1. **확인**을 선택합니다.

함수가 오버로드되었거나 두 개 이상의 네임스페이스에 있는 경우 **중단점** 창에서 원하는 함수를 선택할 수 있습니다.

![오버로드된 함수 중단점](../debugger/media/dbg_execution_overloadedbreakpoints.png "오버로드된 함수 중단점")

**호출 스택에서 함수 중단점을 선택하려면**

1. 디버깅하는 동안 **Windows 호출** **Windows** > **스택** **디버그를** > 선택하여 호출 스택 창을 엽니다.

1. 호출 **스택** 창에서 함수를 마우스 오른쪽 단추로 클릭하고 **커서실행을**선택하거나 **Ctrl**+**F10을**누릅니다.

호출 스택을 시각적으로 추적하려면 [디버깅하는 동안 호출 스택의 Map 메서드를](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)참조하십시오.

### <a name="run-to-a-cursor-location"></a>커서 위치로 실행

소스 코드 또는 **통화 스택** 창에서 커서 위치로 실행하려면 끊으려는 줄을 마우스 오른쪽 단추로 클릭하고 **커서실행을**선택하거나 **Ctrl**+**F10을**누릅니다. **커서로 실행을** 선택하는 것은 임시 중단점을 설정하는 것과 같습니다.

### <a name="run-to-click"></a>실행하려면 클릭

디버거에서 일시 중지하는 동안 소스 코드 또는 **디스어셈블리** 창에서 문 위로 마우스를 가져가고 **실행 실행을 선택하여 녹색** 화살표 아이콘으로 선택할 수 있습니다. **Run to Click을** 사용하면 임시 중단점을 설정할 필요가 없습니다.

![실행하려면 클릭](../debugger/media/dbg-run-to-click.png "실행하려면 클릭")

> [!NOTE]
> **클릭으로 실행은** 에서 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]부터 사용할 수 있습니다.

### <a name="manually-break-into-code"></a>수동으로 코드 중단

실행 중인 앱에서 사용 가능한 다음 코드 줄을 끊려면 **모두 디버그** > **를**선택하거나 **Ctrl**+**Alt**+Break 를**누릅니다.**

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>포인터를 이동하여 실행 흐름을 변경합니다.

디버거가 일시 중지되는 동안 소스 코드 또는 **디스어셈블리** 창의 여백에 노란색 화살표촉이 실행될 다음 문의 위치를 표시합니다. 이 화살촉을 이동하여 실행하도록 다음 문을 변경할 수 있습니다. 코드의 일부를 건너뛰거나 이전 줄로 돌아갈 수 있습니다. 포인터를 이동하는 것은 알려진 버그가 포함된 코드 섹션을 건너뛰는 등의 경우에 유용합니다.

 ![포인터 이동](../debugger/media/dbg_basics_example3.gif "포인터 이동")

실행하도록 다음 문을 변경하려면 디버거가 중단 모드여야 합니다. 소스 코드 또는 **디스어셈블리 해제** 창에서 노란색 화살표를 다른 선으로 드래그하거나 다음에 실행할 줄을 마우스 오른쪽 단추로 클릭하고 **다음 명령문 설정을**선택합니다.

프로그램 카운터는 새 위치로 직접 이동하며 이전 실행 지점과 새 실행 지점 간의 명령은 실행되지 않습니다. 그러나 실행 지점을 뒤로 이동하면 중간 명령이 실행 취소되지 않습니다.

>[!CAUTION]
>- 다음 문을 다른 함수나 범위로 이동하면 호출 스택이 손상되어 런타임 오류나 예외가 발생할 수 있습니다. 다음 문을 다른 범위로 이동하려고 하면 디버거에서 대화 상자가 열리고 여기서 작업을 취소할 수 있습니다.
>- Visual Basic의 경우 다음 문을 다른 범위나 함수로 이동할 수 없습니다.
>- 네이티브 C++에서 런타임 검사를 활성화한 경우 다음 문을 설정하면 실행이 메서드의 끝에 도달할 때 예외가 throw될 수 있습니다.
>- 편집하며 계속하기를 활성화한 경우 편집하며 계속하기에서 즉시 다시 매핑할 수 없는 종류의 편집을 수행하면 **다음 문 설정** 이 실패합니다. 예를 들어 catch 블록 내의 코드를 편집하면 이 문제가 발생합니다. 이 경우 작업지원되지 않는다는 오류 메시지가 표시됩니다.
>- 관리 코드에서 다음과 같은 경우 다음 문을 이동할 수 없습니다.
>   - 다음 문이 현재 문과 다른 메서드에 있는 경우
>   - 디버깅은 Just-In-Time 디버깅에 의해 시작되었습니다.
>   - 호출 스택 해제가 진행 중입니다.
>   - System.StackOverflowException 또는 System.Threading.ThreadAbortException 예외가 throw된 경우

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>비사용자 코드 디버그

기본적으로 디버거는 *내*코드 만이라는 설정을 사용하도록 설정하여 앱 코드만 디버깅하려고 시도합니다. 이 기능이 다양한 프로젝트 유형 및 언어에서 작동하는 방법과 사용자 지정 방법에 대한 자세한 내용은 [내 코드 를](../debugger/just-my-code.md)참조하십시오.

디버깅 하는 동안 프레임 워크 코드 코드, 타사 라이브러리 코드 또는 시스템 호출을 보고, 그냥 내 코드를 사용 하지 않도록 설정할 수 있습니다. **도구(또는** **디버그)**> **옵션** > **디버깅에서** **내 코드 만 사용** 확인란을 선택취소합니다. 내 코드만 비활성화하면 비사용자 코드가 디버거 창에 나타나고 디버거가 비사용자 코드로 들어갈 수 있습니다.

> [!NOTE]
> 디바이스 프로젝트에 대해서는 내 코드만 옵션이 지원되지 않습니다.

### <a name="debug-system-code"></a>시스템 코드 디버그

Microsoft 시스템 코드에 대한 디버깅 기호를 로드하고 내 코드만 사용하지 않도록 설정한 경우 다른 호출과 마찬가지로 시스템 호출에 단계별로 들어갈 수 있습니다.

Microsoft 기호를 로드하려면 [기호 위치 및 로드 옵션 구성을](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)참조하십시오.

**특정 시스템 구성 요소에 대한 기호를 로드하려면 다음을 수행합니다.**

1. 디버깅하는 동안**Windows** > **모듈** **디버그를** > 선택하거나 **Ctrl**+**Alt**+**U를**눌러 **모듈** 창을 엽니다.

1. **모듈** 창에서 기호 **상태** 열에 로드된 기호가 있는 모듈을 알 수 있습니다. 기호를 로드할 모듈을 마우스 오른쪽 단추로 클릭하고 **기호 로드를 선택합니다.**

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 한 단계씩 관리 코드의 속성 및 연산자 실행
 기본적으로 디버거는 관리 코드의 속성과 연산자를 건너뜁니다. 대부분의 경우 이렇게 하면 더 나은 디버깅 환경이 제공됩니다. 속성 또는 연산자를 단계적 해제하려면 **디버그** > **옵션을**선택합니다. 디버깅**일반** 페이지에서 속성 **및 연산자(관리만)** 확인란을 지우고 **클리어합니다.** > 

## <a name="see-also"></a>참고 항목
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [디버깅을 먼저 살펴보십시오.](../debugger/debugger-feature-tour.md)
