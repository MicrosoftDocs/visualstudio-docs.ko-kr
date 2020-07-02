---
title: 디버거에서 중단점 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2020
ms.topic: how-to
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57b2ea6a0c69387043057bc07957a757ed351f99
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769403"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio 디버거에서 중단점 사용

중단점은 개발자의 도구 상자에서 가장 중요한 디버깅 기술 중 하나입니다. 디버거 실행을 일시 중지하려는 모든 위치에 중단점을 설정합니다. 예를 들어 코드 변수의 상태를 확인하거나 특정 중단점에서 호출 스택을 확인할 수 있습니다.  중단점을 사용하는 동안 경고 또는 문제를 해결하려는 경우 [Visual Studio 디버거의 중단점 문제 해결](../debugger/troubleshooting-breakpoints.md)을 참조하세요.

> [!NOTE]
> 해결하려고 하는 작업 또는 문제를 알고 있지만 사용할 중단점의 종류를 알아야 하는 경우 [디버깅 작업 찾기](../debugger/find-your-debugging-task.md#pause-running-code)를 참조하세요.

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> 소스 코드에서 중단점 설정

실행 코드의 임의의 줄에서 중단점을 설정할 수 있습니다. 예를 들어 다음 C# 코드에서는 변수 할당이 있는 코드 줄(`int testInt = 1`), `for` 루프 또는 `for` 루프 내의 모든 코드에 중단점을 설정할 수 있습니다. 할당 및 getter/setter가 없는 경우, 메서드 시그니처, 네임 스페이스 또는 클래스에 대한 선언, 변수 선언에는 중단점을 설정할 수 없습니다.

소스 코드에서 중단점을 설정하려면 코드 줄 옆에 있는 맨 왼쪽 여백을 클릭합니다. 또한 줄을 선택하고 **F9**를 누르거나 **디버그** > **중단점 설정/해제**를 선택하거나 마우스 오른쪽 단추를 클릭하여 **중단점** > **중단점 삽입**을 선택할 수 있습니다. 중단점이 왼쪽 여백에 빨간 점으로 나타납니다.

C#를 비롯한 대부분의 언어에서 중단점 및 현재 실행 줄은 자동으로 강조 표시됩니다. C++코드를 사용하는 경우 **도구**(또는 **디버그**) > **옵션** > **디버깅** >  **중단점 및 현재 문에 대한 전체 소스 줄을 강조 표시(C++만 해당)** 를 선택하여 중단점 및 현재 줄의 강조 표시를 켤 수 있습니다.

![중단점 설정](../debugger/media/basicbreakpoint.png "기본 중단점")

디버그할 때 해당 줄의 코드가 실행되기 전에 중단점에서 실행이 일시 중지됩니다. 중단점 기호에는 노란색 화살표가 표시됩니다.

다음 예제의 중단점에서 `testInt` 값은 여전히 1입니다. 따라서 노란색의 문이 아직 실행되지 않았기 때문에 변수가 초기화된 후(값 1로 설정됨) 값이 변경되지 않았습니다.

![중단점 실행 중지됨](../debugger/media/breakpointexecution.png "중단점 실행")

디버거가 중단점에서 중지되면 [변수 값](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips)과 [호출 스택](../debugger/how-to-use-the-call-stack-window.md)을 포함하여 앱의 현재 상태를 확인할 수 있습니다.

중단점 사용에 대한 몇 가지 일반적인 지침은 다음과 같습니다.

- 중단점은 토글 키입니다. 이를 클릭하거나 **F9**를 누르거나 **디버그** > **중단점 설정/해제**를 사용하여 삭제하거나 다시 삽입할 수 있습니다.

- 중단점을 삭제하지 않고 사용하지 않도록 설정하려면 해당 중단점을 마우스로 가리키거나 마우스 오른쪽 단추로 클릭한 다음 **중단점 사용 안함**을 선택합니다. 비활성화된 중단점은 왼쪽 여백이나 **중단점** 창에 빈 점으로 표시됩니다. 중단점을 다시 사용하도록 설정하려면 마우스로 가리키거나 마우스 오른쪽 단추를 클릭하고 **중단점 사용**을 선택합니다.

- 조건 및 작업을 설정하고, 레이블을 추가 및 편집하고, 중단점을 마우스 오른쪽 단추로 클릭하고, 적절한 명령을 선택하거나 마우스로 가리키고 **설정** 아이콘을 선택하여 중단점을 내보낼 수 있습니다.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> 중단점 작업 및 추적점

*추적점*은 **출력** 창에 메시지를 인쇄하는 중단점입니다. 추적점은 프로그래밍 언어의 임시 추적 문처럼 작동할 수 있으며 코드 실행을 일시 중지하지 않습니다. **중단점 설정** 창에서 특수 작업을 설정하여 추적점을 만듭니다. 자세한 지침은 [Visual Studio 디버거에서 추적점 사용](../debugger/using-tracepoints.md)을 참조하세요.

## <a name="breakpoint-conditions"></a>중단점 조건

조건을 설정하여 중단점 실행 시점과 위치를 제어할 수 있습니다. 디버거에서 인식하는 모든 유효한 식은 조건이 될 수 있습니다. 유효한 식에 대한 자세한 내용은 [디버거에서 사용하는 식](../debugger/expressions-in-the-debugger.md)을 참조하세요.

**중단점 조건을 설정하려면**

1. 마우스 오른쪽 단추로 중단점 기호를 클릭하고 **조건**을 선택합니다. 또는 중단점 기호 위로 마우스를 이동하고 **설정** 아이콘을 선택한 다음 **중단점 설정** 창에서 **조건**을 선택합니다.

   중단점을 마우스 오른쪽 단추로 클릭하고 **설정**을 선택한 다음 **조건**을 선택하여 **중단점** 창에서 조건을 설정할 수도 있습니다.

   ![중단점 설정](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. 드롭다운에서 **조건 식**, **적중 횟수** 또는 **필터**를 선택하고 적절한 값을 설정합니다.

3. **닫기**를 선택하거나 **Ctrl**+**Enter 키**를 눌러 **중단점 설정** 창을 닫습니다. 또는 **중단점** 창에서 **확인**을 선택하여 대화 상자를 닫습니다.

조건이 설정된 중단점이 소스 코드 및 **중단점** 창에 **+** 기호와 함께 표시됩니다.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>조건 식 만들기

**조건 식**을 선택하는 경우 다음 두 조건 중에서 선택할 수 있습니다. **Is true** 또는 **When changed**입니다. 식을 만족할 때 중단하려면 **Is true**를 선택하고 식의 값이 변경되었을 때 중단하려면 **When changed**를 선택합니다.

다음 예제에서는 `testInt`의 값이 **4**일 때만 중단점이 적중됩니다.

![중단점 조건이 true 임](../debugger/media/breakpointconditionistrue.png "중단점이 true임")

다음 예제에서는 `testInt`의 값이 변경될 때만 중단점이 적중됩니다.

![변경 시 중단점](../debugger/media/breakpointwhenchanged.png "변경 시 중단점")

잘못된 구문을 사용하여 중단점 조건을 설정하면 경고 메시지가 나타납니다. 올바르지만 의미가 잘못된 구문을 사용하여 중단점 조건을 지정하면 중단점이 처음 적중될 때 경고 메시지가 나타납니다. 두 경우 모두 잘못된 중단점이 적중되면 디버거에서 실행을 중단합니다. 조건이 올바르고 `false`가 되는 경우에만 중단점을 건너뜁니다.

>[!NOTE]
>**변경된 경우** 필드의 동작은 프로그래밍 언어별로 서로 다릅니다.
>- 네이티브 코드의 경우 디버거는 조건의 첫 번째 계산을 변경으로 간주하지 않으므로 첫 번째 계산에서는 중단점이 적중되지 않습니다.
>- 관리 코드의 경우 **변경 시**를 선택하면 디버거가 첫 번째 계산에서 중단점이 적중됩니다.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>조건 식에만 개체 ID 사용(C# 및 F#만 해당)

 특정 개체의 동작을 관찰하려는 경우가 있습니다. 예를 들어 개체가 컬렉션에 두 번 이상 삽입된 이유를 확인하고자 할 수 있습니다. C# 및 F#에서 [참조 형식](/dotnet/csharp/language-reference/keywords/reference-types) 의 특정 인스턴스에 대한 개체 ID를 만들고 중단점 조건에서 사용할 수 있습니다. 개체 ID는 CLR(공용 언어 런타임) 디버깅 서비스에 의해 생성되고 개체와 연결됩니다.

**개체 ID를 만들려면**

1. 개체를 만든 후 코드에서 중단점을 설정합니다.

2. 디버깅을 시작하고 중단점에서 실행이 일시 중지된 경우 **디버그** > **Windows** > **지역** 또는 **Alt**+**4**를 선택해 **지역** 창을 엽니다.

   **지역** 창에서 특정 개체 인스턴스를 찾아 마우스 오른쪽 단추로 클릭하고 **개체 ID 만들기**를 선택합니다.

   **$** 창에 **지역** 창을 닫습니다. 이는 개체 ID입니다.

3. 조사하려는 지점(예: 컬렉션에 개체를 추가해야 하는 경우)에 새 중단점을 추가합니다. 마우스 오른쪽 단추로 중단점을 클릭하고 **조건**을 선택합니다.

4. **조건부 식** 필드에 개체 ID를 사용합니다. 예를 들어 `item` 변수가 컬렉션에 추가될 개체이면 **Is true**를 선택하고 **항목 == $\<n>** 을 입력합니다. 여기서 \<n>은 개체 ID 번호입니다.

   컬렉션에 개체를 추가해야 하는 지점에서 실행이 중단됩니다.

   개체 ID를 삭제하려면 **지역** 창에서 변수를 마우스 오른쪽 단추로 클릭하고 **개체 ID 삭제**를 선택합니다.

> [!NOTE]
> 개체 ID는 약한 참조를 만들고 개체가 가비지 수집되지 않도록 차단하지 않습니다. 현재 디버깅 세션에 대해서만 유효합니다.

### <a name="set-a-hit-count-condition"></a>적중 횟수 조건 설정

코드의 루프가 특정 횟수를 반복한 후 잘못된 동작을 시작하는 것으로 의심되는 경우, 반복적으로 **F5** 키를 눌러 반복 수준에 도달해야 하는 대신 해당 횟수만큼 적중된 후 실행을 중지하도록 중단점을 설정할 수 있습니다.

**중단점 설정** 창의 **조건**에 따라 **적중 횟수**를 선택한 다음 반복 횟수를 지정합니다. 다음 예제에서는 반복 2회당 한 번 중단점이 적중하도록 설정됩니다.

![중단점 적중 횟수](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>필터 조건 설정

지정된 디바이스에서만 발생하거나 지정된 프로세스 및 스레드에서만 발생하도록 중단점을 제한할 수 있습니다.

**중단점 설정** 창의 **조건**에 따라 **필터**를 선택한 다음 식 중 하나 이상을 입력합니다.

- MachineName = "이름"
- ProcessId = 값
- ProcessName = "이름"
- ThreadId = 값
- ThreadName = "이름"

문자열 값은 큰따옴표로 묶습니다. `&` (AND), `||` (OR), `!` (NOT), 괄호를 사용하여 절을 결합할 수 있습니다.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> 함수 중단점 설정

함수가 호출될 때 실행을 중단할 수 있습니다. 이는 예를 들어 함수 이름을 알고 있지만 위치를 알 수 없는 경우에 유용합니다. 동일한 이름을 가진 함수가 있고 이러한 함수를 모두 중단하려는 경우에도 유용합니다(예: 오버로드된 함수 또는 다른 프로젝트의 함수).

**함수 중단점을 설정하려면**

1. **디버그** > **새 중단점** > **함수 중단점**를 선택하거나 **Alt**+**F9** > **Ctrl**+**B**를 누릅니다.

   또한 **중단점** 창에서 **새** > **함수 중단점**을 선택할 수 있습니다.

1. **새 함수 중단점** 대화 상자에서 **함수 이름** 상자에 함수 이름을 입력합니다.

   함수 사양을 좁히려면

   - 정규화된 함수 이름을 사용합니다.

     예제: `Namespace1.ClassX.MethodA()`

   - 오버로드된 함수의 매개 변수 유형을 추가합니다.

     예제: `MethodA(int, string)`

   - '!' 기호를 사용하여 모듈을 지정합니다.

     예: `App1.dll!MethodA`

   - 네이티브 C++에서 컨텍스트 연산자를 사용합니다.

     `{function, , [module]} [+<line offset from start of method>]`

     예: `{MethodA, , App1.dll}+2`

1. **언어** 드롭다운에서 함수의 언어를 선택합니다.

1. **확인**을 선택합니다.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>메모리 주소를 사용하여 함수 중단점 설정(네이티브 C++에만 해당)
 개체의 주소를 사용하여 클래스의 특정 인스턴스에서 호출되는 메서드에 함수 중단점을 설정할 수 있습니다.  예를 들어 `my_class` 형식의 주소 지정 가능한 개체가 지정된 경우 인스턴스가 호출하는 `my_method` 메서드에 함수 중단점을 설정할 수 있습니다.

1. 클래스의 해당 인스턴스가 인스턴스화된 후 어딘가에 중단점을 설정합니다.

2. 인스턴스의 주소를 찾습니다(예: `0xcccccccc`).

3. **디버그** > **새 중단점** > **함수 중단점**를 선택하거나 **Alt**+**F9** > **Ctrl**+**B**를 누릅니다.

4. **함수 이름** 상자에 다음을 추가하고 **C++** 언어를 선택합니다.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>데이터 중단점 설정(.NET Core 3.0 이상)

데이터 중단점은 특정 개체의 속성이 변경될 때 실행을 중단합니다.

**데이터 중단점을 설정하려면**

1. .NET Core 프로젝트에서 디버깅을 시작하고 중단점에 도달할 때까지 기다립니다.

2. **자동**, **조사식** 또는 **지역** 창에서 속성을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **값이 변경되면 중단**을 선택합니다.

    ![관리되는 데이터 중단점](../debugger/media/managed-data-breakpoint.png "관리되는 데이터 중단점")

.NET Core의 데이터 중단점은 다음에 대해 작동하지 않습니다.

- 도구 설명, 지역, 자동 또는 조사식 창에서 확장할 수 없는 속성
- 정적 변수
- DebuggerTypeProxy 특성이 있는 클래스
- 구조체 내의 필드

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>데이터 중단점 설정(네이티브 C++에만 해당)

 데이터 중단점은 지정된 메모리 주소에 저장된 값이 변경되면 실행을 중단합니다. 값을 읽기만 하고 변경하지는 않을 때는 실행이 중단되지 않습니다.

**데이터 중단점을 설정하려면**

1. C++ 프로젝트에서 디버깅을 시작하고 중단점에 도달할 때까지 기다립니다. **디버그** 메뉴에서 **새 중단점** > **데이터 중단점**을 선택합니다.

    **중단점 창**에서 **새로 만들기** > **데이터 중단점**을 선택하거나, **자동**, **조사식** 또는 **지역** 창의 항목을 마우스 오른쪽 단추로 클릭해 바로 가기 메뉴에서 **값이 변경되면 중단**을 선택할 수도 있습니다.

2. **주소** 상자에 메모리 주소를 입력하거나 메모리 주소로 계산되는 식을 입력합니다. 예를 들어, 변수 `&avar` 의 내용이 변경되면 중단하려면 `avar` 을 입력합니다.

3. 디버거에서 조사할 바이트 수를 **바이트 계산** 드롭다운에서 선택합니다. 예를 들어, **4**를 선택하면 디버거가 `&avar` 에서 시작되는 4바이트를 조사하여 해당 바이트의 값이 변경되면 중단됩니다.

다음 조건에서는 데이터 중단점이 작동하지 않습니다.
- 디버깅되지 않는 프로세스는 메모리 위치에 기록합니다.
- 메모리 위치는 둘 이상의 프로세스 간에 공유됩니다.
- 커널 내에서 메모리 위치가 업데이트되는 경우. 예를 들어 32비트 Windows `ReadFile` 함수에 메모리가 전달된 경우 커널 모드에서 메모리가 업데이트되므로 업데이트에서 디버거는 실행을 중단하지 않습니다.
- 여기서 조사식 식은 32비트 하드웨어에서 4바이트보다 크고 64비트 하드웨어에서는 8바이트보다 큽니다. 이는 x86 아키텍처의 제한 사항입니다.

> [!NOTE]
> - 데이터 중단점은 특정 메모리 주소에 따라 달라집니다. 변수의 주소는 디버깅 세션 간에 변경되므로 데이터 중단점은 각 디버깅 세션이 끝날 때 자동으로 해제됩니다.
>
> - 데이터 중단점을 지역 변수에 설정한 경우에는 함수가 종료되어도 중단점이 설정된 상태로 유지되지만 메모리 주소는 더 이상 적용되지 않으므로 중단점의 동작을 예측할 수 없습니다. 데이터 중단점을 지역 변수에 설정한 경우에는 함수가 종료되기 전에 중단점을 삭제하거나 사용하지 않도록 설정해야 합니다.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> 중단점 창에서 중단점 관리

 **중단점** 창을 사용하여 솔루션의 모든 중단점을 보고 관리할 수 있습니다. 이 중앙 위치는 특히 큰 솔루션에서 또는 중단점이 중요한 복잡한 디버깅 시나리오에서 유용합니다.

**중단점** 창에서 중단점을 검색, 정렬, 필터링, 활성화/비활성화하거나 삭제할 수 있습니다. 조건 및 동작을 설정하거나 새 함수 또는 데이터 중단점을 추가할 수도 있습니다.

**중단점** 창을 열려면 **디버그** > **Windows** > **중단점**을 선택하거나 **Alt**+**F9** 또는 **Ctrl**+**Alt**+**B**를 누릅니다.

![중단점 창](../debugger/media/breakpointswindow.png "중단점 창")

**중단점** 창에 표시할 열을 선택하려면 **열 표시**를 선택합니다. 해당 열을 기준으로 중단점 목록을 정렬하려면 열 헤더를 선택합니다.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> 중단점 레이블
레이블을 사용하여 **중단점** 창에서 중단점 목록을 정렬 및 필터링할 수 있습니다.

1. 중단점에 레이블을 추가하려면 소스 코드 또는 **중단점** 창에서 중단점을 마우스 오른쪽 단추로 클릭한 다음 **레이블 편집**을 선택합니다. 새 레이블을 추가하거나 기존 레이블을 선택한 다음 **확인**을 선택합니다.
2. **레이블**, **조건** 또는 다른 열 헤더를 선택하여 **중단점** 창에서 중단점 목록을 정렬합니다. 도구 모음에서 **열 표시**를 선택하여 표시할 열을 선택할 수 있습니다.

### <a name="export-and-import-breakpoints"></a>중단점 내보내기 및 가져오기
 중단점의 상태 및 위치를 저장하거나 공유하기 위해 중단점을 내보내거나 가져올 수 있습니다.

- 단일 중단점을 XML 파일로 내보내려면 소스 코드 또는 **중단점** 창에서 중단점을 마우스 오른쪽 단추로 클릭하고 **내보내기** 또는 **선택하여 내보내기**를 선택합니다. 내보내기 위치를 선택한 다음 **저장**을 선택합니다. 기본 위치는 솔루션 폴더입니다.
- 여러 중단점을 내보내려면 **중단점** 창에서 중단점 옆의 상자를 선택하거나 **검색** 필드에 검색 조건을 입력합니다. **현재 검색 조건과 일치하는 모든 중단점 내보내기** 아이콘을 선택하고 파일을 저장합니다.
- 모든 중단점을 내보내려면 모든 상자의 선택을 취소하고 **검색** 필드를 비워 둡니다. **현재 검색 조건과 일치하는 모든 중단점 내보내기** 아이콘을 선택하고 파일을 저장합니다.
- 중단점을 가져오려면 **중단점** 창에서 **파일에서 중단점 가져오기** 아이콘을 선택하고 XML 파일 위치로 이동한 다음 **열기**를 선택합니다.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>디버거 창에서 중단점 설정

**호출 스택** 및 **디스어셈블리** 디버거 창에서도 중단점을 설정할 수 있습니다.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>호출 스택 창에서 중단점 설정

 호출 함수가 반환하는 명령 또는 줄에서 중단하려면 **호출 스택** 창에서 중단점을 설정할 수 있습니다.

**호출 스택 창에서 중단점을 설정하려면**

1. **호출 스택** 창을 열려면 디버그하는 동안 일시 중지해야 합니다. **디버그** > **Windows** > **호출 스택**를 선택하거나 **Ctrl**+**Alt**+**C**를 누릅니다.

2. **호출 스택** 창에서 호출 함수를 마우스 오른쪽 단추로 클릭하고 **중단점** > **중단점 삽입**을 선택하거나 **F9**를 누릅니다.

   호출 스택의 왼쪽 여백에서 함수 호출 이름 옆에 중단점 기호가 표시됩니다.

호출 스택 중단점은 함수의 다음 실행 명령에 해당하는 메모리 위치가 포함된 주소로 **중단점** 창에서 나타납니다.

디버거는 해당 명령에서 중단됩니다.

호출 스택에 대한 자세한 내용은 [ 호출 스택 창 사용 방법](../debugger/how-to-use-the-call-stack-window.md)을 참조하세요.

코드 실행 중에 중단점을 시각적으로 추적하려면 [디버그하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조하세요.

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>디스어셈블리 창에서 중단점 설정

1. **디스어셈블리** 창을 열려면 디버그하는 동안 일시 중지해야 합니다. **디버그** > **Windows** > **디스어셈블리**를 선택하거나 **Alt**+**8**을 누릅니다.

2. **디스어셈블리** 창에서 중단하려는 명령의 왼쪽 여백을 클릭합니다. 또한 줄을 선택하고 **F9**를 누르거나 마우스 오른쪽 단추를 클릭하고 **중단점** > **중단점 삽입**을 선택할 수도 있습니다.

## <a name="see-also"></a>참조

- [디버깅이란?](../debugger/what-is-debugging.md)
- [Visual Studio를 사용하여 더 나은 C# 코드 작성](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
- [Visual Studio 디버거에서 중단점 문제 해결](../debugger/troubleshooting-breakpoints.md)
