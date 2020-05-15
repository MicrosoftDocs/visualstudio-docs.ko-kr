title: 디버거를 사용하여 코드 탐색 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301094"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio 디버거를 사용하여 코드 탐색

Visual Studio 디버거는 코드를 탐색하여 앱의 상태를 검사하고 실행 흐름을 표시하는 데 도움이 될 수 있습니다. 바로 가기 키, 디버그 명령, 중단점 및 기타 기능을 사용하여 검사하려는 코드를 신속하게 가져올 수 있습니다. 디버거 탐색 명령 및 바로 가기에 익숙해지면 앱 문제를 더 빠르고 쉽게 찾고 해결할 수 있습니다.  코드를 처음으로 디버깅하는 경우 이 문서를 진행하기 전에 먼저 [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md) 및 [디버깅 기술과 도구](../debugger/write-better-code-with-visual-studio.md)를 읽어보는 것이 좋습니다.

## <a name="get-into-break-mode"></a>"중단 모드"로 가져오기

*중단 모드*에서는 함수, 변수 및 개체가 메모리에 있는 동안 앱 실행이 일시 중단됩니다. 디버거가 중단 모드에 있으면 코드를 탐색할 수 있습니다. 중단 모드로 신속하게 전환하는 가장 일반적인 방법은 다음 중 하나입니다.

- **F10** 또는 **F11**를 눌러 코드 단계를 시작합니다. 이렇게 하면 앱의 진입점을 빠르게 찾은 다음, 단계 명령을 계속 눌러 코드를 탐색할 수 있습니다.

- 예를 들어, [중단점을 설정하고](using-breakpoints.md) 앱을 시작하여 [특정 위치 또는 함수까지 실행합니다](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).

   예를 들어, Visual Studio의 코드 편집기에서 **커서까지 실행** 명령을 사용하여 앱을 시작하고, 디버거를 연결하고, 중단 모드로 전환한 다음, **F11**를 눌러 코드를 탐색할 수 있습니다.

   ![커서까지 실행 및 한 단계씩 코드 실행](../debugger/media/navigate-code-code-stepping.gif "커서까지 실행 및 한 단계씩 코드 실행")

중단 모드에서는 다양한 명령을 사용하여 코드를 탐색할 수 있습니다. 중단 모드에서는 변수 값을 검사하여 위반 또는 버그를 찾을 수 있습니다. 일부 프로젝트 형식의 경우 중단 모드에 있는 동안 애플리케이션을 조정할 수도 있습니다.

**모듈** 및 **조사식** 창과 같은 대부분의 디버거 창은 디버거가 앱에 연결되어 있는 동안에만 사용할 수 있습니다. **지역** 창에서 변수 값 보기 또는 **조사식** 창에서 식 계산과 같은 일부 디버거 기능은 중단 모드에서만 사용할 수 있습니다.

> [!NOTE]
> 소스 또는 기호( *.pdb*) 파일이 로드되지 않은 코드 실행을 중단하는 경우 디버거는 적절한 파일을 찾아 로드하는 데 도움이 될 수 있는 **원본 파일을 찾을 수 없음** 또는 **기호를 찾을 수 없음** 페이지를 표시합니다. [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요. 기호 또는 원본 파일을 로드할 수 없는 경우에도 **디스어셈블리** 창에서 어셈블리 명령을 디버깅할 수 있습니다.

## <a name="step-through-code"></a>단계별 코드 실행

디버거 단계 명령은 앱 상태를 검사하거나 실행 흐름에 대한 자세한 정보를 확인하는 데 도움이 됩니다.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> 한 줄씩 한 단계씩 코드 실행

디버깅하는 동안 각 문에서 중지하려면 **디버그** > **한 단계씩 코드 실행**를 사용한 다음, **F11**를 누릅니다.

디버거는 실제 줄이 아닌 코드 문을 단계별로 실행합니다. 예를 들어 한 줄에 `if` 절을 작성할 수 있습니다.

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

하지만 이 줄을 한 단계씩 실행하면 디버거는 조건을 한 단계로 처리하고 결과를 다른 단계로 처리합니다. 위의 예제에서 조건은 true입니다.

중첩된 함수 호출인 경우 **한 단계씩 코드 실행** 명령은 가장 안쪽에 중첩된 함수를 한 단계씩 실행합니다. 예를 들어, `Func1(Func2())`와 같은 호출에서 **한 단계씩 코드 실행**을 사용하면 디버거는 함수 `Func2`를 한 단계씩 실행합니다.

>[!TIP]
>각 코드 줄을 실행할 때 변수를 마우스로 가리켜서 값을 확인하거나 [지역](autos-and-locals-windows.md) 및 [조사식](watch-and-quickwatch-windows.md) 창을 사용하여 값 변경 내용을 볼 수 있습니다. 또한 함수를 한 단계씩 실행하는 동안 [호출 스택](how-to-use-the-call-stack-window.md)을 시각적으로 추적할 수 있습니다. (Visual Studio Enterprise를 사용하는 경우에만 [디버깅하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조하세요).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> 단계별 코드 실행 및 일부 함수 건너뛰기

잘 테스트된 라이브러리 코드처럼 작동한다는 것을 알고 있기 때문에 디버깅하는 동안 함수를 신경 쓸 필요가 없습니다. 다음 명령을 사용하여 코드를 단계별로 실행하는 동안 코드를 건너뛸 수 있습니다. 함수는 계속 실행되지만 디버거는 이를 건너뜁니다.

|키보드 명령|디버그 메뉴 명령|설명|
|----------------------|------------------|-----------------|
|**F10**|**프로시저 단위 실행**|현재 줄에 함수 호출이 포함되어 있으면 **프로시저 단위 실행**이 코드를 실행한 다음, 호출된 함수가 반환된 후 코드 첫 번째 줄에서 실행을 일시 중단합니다.|
|**Shift**+**F11**|**프로시저 나가기**|**프로시저 나가기**는 코드를 계속 실행하고 현재 함수가 반환될 때 실행을 일시 중단합니다. 디버거가 현재 함수를 건너뜁니다.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 특정 위치 또는 함수까지 실행

검사할 코드를 정확히 알고 있거나 디버깅을 시작할 위치를 알고 있는 경우 특정 위치 또는 함수까지 직접 실행하는 것이 좋습니다.

### <a name="run-to-a-breakpoint-in-code"></a>코드의 중단점까지 실행

코드에 간단한 중단점을 설정하려면 실행을 일시 중단하려는 코드 줄 옆에 있는 맨 왼쪽 여백을 클릭합니다. 또한 줄을 선택하고 **F9**를 누르거나 **디버그** > **중단점 설정/해제**를 선택하거나 마우스 오른쪽 단추를 클릭하여 **중단점** > **중단점 삽입**을 선택할 수 있습니다. 중단점이 코드 줄 옆의 왼쪽 여백에 빨간 점으로 나타납니다. 디버거는 줄이 실행되기 직전에 실행을 일시 중단합니다.

![중단점 설정](../debugger/media/dbg_basics_setbreakpoint.png "중단점 설정")

Visual Studio에서 중단점은 조건부 중단점 및 추적점과 같은 다양한 추가 기능을 제공합니다. 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md)을 참조하세요.

### <a name="run-to-a-function-breakpoint"></a>함수 중단점까지 실행

지정한 함수에 도달할 때까지 실행하도록 디버거에 지시할 수 있습니다. 함수 이름을 지정하거나 호출 스택에서 함수를 선택할 수 있습니다.

**이름으로 함수 중단점을 지정하려면**

1. **디버그** > **새 중단점** > **함수 중단점**을 선택합니다.

1. **새 함수 중단점** 대화 상자에서 함수 이름을 입력하고 언어를 선택합니다.

   ![새 함수 중단점 대화 상자](../debugger/media/dbg_execution_newbreakpoint.png "새 함수 중단점")

1. **확인**을 선택합니다.

함수가 오버로드되거나 둘 이상의 네임스페이스에 있는 경우 **중단점** 창에서 원하는 것을 선택할 수 있습니다.

![오버로드된 함수 중단점](../debugger/media/dbg_execution_overloadedbreakpoints.png "오버로드된 함수 중단점")

**호출 스택에서 함수 중단점 선택하려면**

1. 디버깅하는 동안 **디버그** > **Windows** > **호출 스택**을 선택하여 **호출 스택** 창을 엽니다.

1. **호출 스택** 창에서 함수를 마우스 오른쪽 단추로 클릭하고 **커서까지 실행**를 선택 하거나 **Ctrl**+**F10**을 누릅니다.

호출 스택을 시각적으로 추적하려면 [디버깅하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조하세요.

### <a name="run-to-a-cursor-location"></a>커서 위치까지 실행

커서 위치까지 실행하려면 소스 코드 또는 **호출 스택** 창에서 중단하려는 줄을 선택하고 마우스 오른쪽 단추를 클릭하여 **커서까지 실행**을 선택하거나 **Ctrl**+**F10**을 누릅니다. **커서까지 실행**을 선택하는 것은 임시 중단점을 설정하는 것과 같습니다.

### <a name="run-to-click"></a>클릭한 줄까지 실행

디버거에서 일시 중지된 동안 소스 코드 또는 **디스어셈블리** 창의 문을 마우스로 가리키고 **여기까지 실행** 녹색 화살표 아이콘을 선택할 수 있습니다. **클릭한 줄까지 실행**을 사용하면 임시 중단점을 설정하지 않아도 됩니다.

![클릭한 줄까지 실행](../debugger/media/dbg-run-to-click.png "클릭한 줄까지 실행")

> [!NOTE]
> **클릭한 줄까지 실행**은 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]에서 사용할 수 있습니다.

### <a name="manually-break-into-code"></a>수동으로 코드 중단

실행 중인 앱에서 사용 가능한 다음 코드 줄에서 중단하려면 **디버그** > **모두 중단**을 선택하거나 **Ctrl**+**Alt**+**중단**을 누릅니다.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> 포인터를 이동하여 실행 흐름 변경

디버거에서 일시 중지된 동안 소스 코드 또는 **디스어셈블리** 창의 여백에 있는 노란색 화살표는 다음에 실행할 문의 위치를 나타냅니다. 이 화살표를 이동하여 다음 명령문을 실행하도록 변경할 수 있습니다. 코드의 일부를 건너뛰거나 이전 줄로 돌아갈 수 있습니다. 알려진 버그를 포함하는 코드 섹션을 건너뛰려는 경우에는 포인터 이동이 유용합니다.

 ![포인터 이동](../debugger/media/dbg_basics_example3.gif "포인터 이동")

실행할 다음 명령문을 설정하려면 디버거는 중단 모드에 있어야 합니다. 소스 코드 또는 **디스어셈블리** 창에서 노란색 화살표를 다른 줄로 끌거나 다음에 실행할 줄을 마우스 오른쪽 단추로 클릭하고 **다음 명령문 설정**을 선택합니다.

프로그램 카운터는 새 위치로 바로 이동하고 이전 실행 지점과 새 실행 위치 간의 명령이 실행되지 않습니다. 그러나 실행 지점을 뒤로 이동해도 간섭 명령이 실행 취소되지 않습니다.

>[!CAUTION]
>- 다음 문을 다른 함수나 범위로 이동하면 호출 스택이 손상되어 런타임 오류나 예외가 발생할 수 있습니다. 다음 문을 다른 범위로 이동하려고 하면 디버거에서 대화 상자가 열리고 여기서 작업을 취소할 수 있습니다.
>- Visual Basic의 경우 다음 문을 다른 범위나 함수로 이동할 수 없습니다.
>- 네이티브 C++에서 런타임 검사를 활성화한 경우 다음 문을 설정하면 실행이 메서드의 끝에 도달할 때 예외가 throw될 수 있습니다.
>- 편집하며 계속하기를 활성화한 경우 편집하며 계속하기에서 즉시 다시 매핑할 수 없는 종류의 편집을 수행하면 **다음 문 설정** 이 실패합니다. 예를 들어 catch 블록 내의 코드를 편집하면 이 문제가 발생합니다. 이 경우 작업이 지원되지 않음을 알리는 오류 메시지가 나타납니다.
>- 관리 코드의 경우 다음과 같은 조건에서는 다음 명령문을 이동할 수 없습니다.
>   - 다음 문이 현재 문과 다른 메서드에 있는 경우
>   - Just-In-Time 디버깅으로 디버깅을 시작한 경우
>   - 호출 스택 해제가 진행 중인 경우
>   - System.StackOverflowException 또는 System.Threading.ThreadAbortException 예외가 throw된 경우

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>사용자 코드가 아닌 코드 디버깅

기본적으로 디버거는 *내 코드만*이라고 하는 설정을 사용하여 앱 코드만 디버깅하려고 합니다. 이 기능이 다양한 프로젝트 형식 및 언어에 대해 작동하는 방식과 이를 사용자 지정할 수 있는 방법에 대한 자세한 내용은 [내 코드만](../debugger/just-my-code.md)를 참조하세요.

디버깅하는 동안 프레임워크 코드, 타사 라이브러리 코드 또는 시스템 호출을 보려면 내 코드만을 사용하지 않을 수 있습니다. **도구**(또는 **디버그**) > **옵션** > **디버깅**에서 **내 코드만 사용** 확인란의 선택을 취소합니다. 내 코드만을 사용하지 않는 경우 디버거 창에 사용자 코드가 아닌 코드가 표시되고 디버거가 사용자가 아닌 코드를 한 단계씩 실행할 수 있습니다.

> [!NOTE]
> 디바이스 프로젝트에 대해서는 내 코드만 옵션이 지원되지 않습니다.

### <a name="debug-system-code"></a>시스템 코드 디버깅

Microsoft 시스템 코드에 대한 디버깅 기호를 로드했고 내 코드만을 사용하지 않은 경우, 다른 모든 호출과 마찬가지로 시스템 호출을 한 단계씩 실행할 수 있습니다.

Microsoft 기호를 로드하려면 [기호 위치 및 로딩 옵션 구성](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)을 참조하세요.

**특정 시스템 구성 요소에 대한 기호를 로드하려면**

1. 디버깅하는 동안 **디버그** > **Windows** > **모듈**을 선택하거나 **Ctrl**+**Alt**+**U**를 눌러 **모듈** 창을 엽니다.

1. **모듈** 창에서 어떤 모듈이 **기호 상태** 열에 기호를 로드했는지 알 수 있습니다. 기호를 로드하려는 모듈을 마우스 오른쪽 단추로 클릭하고 **기호 로드**를 선택합니다.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 한 단계씩 관리 코드의 속성 및 연산자 실행
 기본적으로 디버거는 관리 코드의 속성과 연산자를 건너뜁니다. 대부분의 경우 이렇게 하면 더 나은 디버깅 환경이 제공됩니다. 속성이나 연산자를 한 단계씩 실행하려면 **디버그** > **옵션**을 선택합니다. **디버깅** > **일반** 페이지에서 **속성 및 연산자 건너뛰기(관리 전용)** 확인란의 선택을 취소합니다.

## <a name="see-also"></a>참조
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [디버깅 소개](../debugger/debugger-feature-tour.md)
