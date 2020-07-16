---
title: Visual Studio 2015에서 디버깅 시작 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca3f3806f9097082d71dd80e74ccf48cd78c951b
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386890"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Visual Studio 2015에서 디버그 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015에서는 프로젝트 빌드 및 디버깅 도구의 강력한 통합 집합을 제공합니다. 이 항목에서는 가장 기본적인 디버깅 UI 기능 집합을 사용하여 시작하는 방법을 알아봅니다.

 참고: 이 페이지의 아래쪽에 더 많은 고급 기능과 플랫폼 또는 기능별 항목의 링크가 있습니다.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>내 코드는 작동하지 않습니다. Visual Studio 2015 도움말!
 지금까지 편집기를 살펴보고 일부 코드를 만들었습니다. 이제 해당 코드의 디버그를 시작하려고 합니다. Visual Studio 2015에서는 대부분의 IDE와 마찬가지로 디버깅이 두 단계로 이루어집니다. 먼저 프로젝트 및 컴파일러 오류를 catch하고 해결하는 코드를 빌드한 다음 환경에서 해당 코드를 실행하여 런타임 및 동적 오류를 catch하고 해결합니다.

### <a name="configuring-a-build"></a>빌드 구성
 빌드 구성에는 **디버그** 및 **릴리스**의 두 가지 기본 유형이 있습니다. 첫 번째 구성은 보다 풍부한 대화형 런타임 디버깅 환경을 허용하지만 배송하면 안 되는 더 느리고 큰 실행 파일을 생성합니다. 두 번째 구성은 적어도 컴파일러의 관점에서 배송하기에 적합한 더 빠르고 최적화된 실행 파일을 빌드합니다.

 기본 빌드 구성은 **디버그**입니다.

 ![Visual Studio 디버그 빌드 단추](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 **x86**(32비트 Intel CPU), **x64**(64비트 Intel CPU) 및 **ARM**(ARM CPU, 특정 앱 형식에서만 지원됨)과 같은 특정 빌드 플랫폼을 대상으로 지정할 수도 있습니다. 관리되는 프로젝트 및 네이티브 프로젝트에 대한 기본값은 **x86**입니다. 변경 하려면 빌드 플랫폼 드롭다운을 클릭 하 고 다른 플랫폼을 선택 하거나 **Configuration Manager** ...

 ![Visual Studio 구성 파일 관리자 창](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 **구성 관리자**를 사용하여 대상 빌드 구성을 지정할 수 있습니다. 실행하고 **구성** 또는 **CPU** 드롭다운을 클릭한 다음 **새로 만들기...** 를 선택하여 새 빌드 또는 플랫폼을 만듭니다.

 ![Visual Studio 구성 관리자 창](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 처음에는 빌드 구성 및 플랫폼으로 각각 **디버그** 및 **x86**을 사용합니다. 코딩 및 디버깅이 완료 되 면 구성을 **릴리스** 로 변경 하 고 특정 플랫폼을 대상으로 지정 합니다. 이전 버전의 Visual Studio에서는 .NET 코드 프로젝트에 대해 **AnyCPU** 기본 플랫폼을 제공했습니다.

 참고: 프로젝트를 빌드할 때 구성 및 플랫폼 값을 사용하여 실행 파일을 저장하기 위해 만들 프로젝트 디렉터리 경로도 결정합니다. 일반적으로이는 ** \<path-to-project> \\<프로젝트 이름 \> \\<구성 \> \\<플랫폼 \> **입니다. 예를 들어 구성이 `Debug`이고 플랫폼이 `x86`인 프로젝트는 `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86` 아래에 있습니다. 이 기능은 빌드된 실행 파일을 관리하는 고유한 도구나 스크립트가 있는 경우에 유용할 수 있습니다.

### <a name="building-your-code"></a>코드 빌드
 빌드를 구성했으면 이제 실제로 프로젝트를 빌드해야 합니다. 가장 쉬운 방법은 F7 키를 누르는 것이지만 주 메뉴에서 **빌드->솔루션 빌드**를 선택하여 빌드를 시작할 수도 있습니다.

 ![Visual Studio 빌드 프로젝트 메뉴 선택](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Visual Studio UI 아래쪽의 **출력** 상태 창에서 빌드 프로세스를 관찰할 수 있습니다. 오류, 경고 및 빌드 작업이 여기에 표시됩니다. 오류가 있는 경우(또는 구성된 수준 위의 경고가 있는 경우) 빌드가 실패합니다. 오류 및 경고를 클릭하여 발생한 줄로 이동할 수 있습니다. **F7** 키를 다시 누르거나(오류가 있는 파일만 다시 컴파일) **Ctrl+Alt+F7**을 눌러(새로운 전체 다시 빌드) 프로젝트를 다시 빌드합니다.

 편집기 아래의 결과 창에는 두 개의 빌드 탭 창이 있습니다. **출력** 창에는 원시 컴파일러 출력(오류 메시지 포함)이 포함되고 **오류 목록** 창은 모든 오류 및 경고의 정렬 및 필터링 가능한 목록을 제공합니다.

 성공하면 **출력** 창에 다음과 같은 결과가 표시됩니다.

 ![Visual Studio 성공적인 빌드 출력](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>오류 목록 검토
 이전에 성공적으로 컴파일한 코드를 수정했다면 오류가 있을 수 있습니다. 처음 코딩하는 경우 많은 오류가 있을 것입니다. 오류는 간단한 구문 오류나 잘못된 변수 이름과 같이 명확한 경우도 있고, 암호화 코드만 제공되어 이해하기 어려운 경우도 있습니다. 문제를 더 자세히 보려면 빌드 **출력** 창의 아래쪽으로 이동 하 여 **오류 목록** 탭을 클릭 합니다. 그러면 프로젝트에 대 한 오류 및 경고를 보다 체계적으로 볼 수 있으며 몇 가지 추가 옵션도 제공 됩니다.

 ![Visual Studio 2015 출력 및 오류 목록](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 **오류 목록** 창에서 오류 코드 줄을 클릭하여 오류가 발생한 줄로 이동합니다. 또는 오른쪽 위에서 **빠른 실행** 표시줄을 클릭 하 고 "줄 번호"를 입력 한 다음 enter 키를 눌러 줄 번호를 설정 합니다. 이는 줄 번호를 설정할 수 있는 **옵션** 창 항목에 액세스하는 가장 빠른 방법입니다. **빠른 실행** 표시줄을 사용하여 UI 클릭 수를 줄이는 방법을 알아봅니다.

 ![줄 번호가 있는 Visual Studio 편집기](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Visual Studio 줄 번호 옵션](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Ctrl+G를 사용하여 오류가 발생한 줄 번호로 빠르게 이동합니다.

 오류는 빨간색 "오류 표시선" 밑줄로 식별됩니다. 자세한 내용을 보려면 마우스를 위로 가져갑니다. 수정 작업에서 새 오류가 도입될 수도 있지만 수정하면 오류가 사라집니다. 이를 "재발"이라고 합니다.

 ![Visual Studio 오류 가리키기](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 오류 목록을 통해 코드의 모든 오류를 해결합니다.

 ![Visual Studio 디버그 오류 창](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>오류 세부 정보 검토
 대부분의 오류는 컴파일러 용어로 표현되므로 이해하기 어려울 수 있습니다. 이러한 경우 추가 정보가 필요합니다. **오류 목록** 창에서 해당 항목 줄을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **오류 도움말 표시**를 선택하여 자동 Bing 검색을 통해 오류(또는 경고)에 대한 자세한 정보를 찾을 수 있습니다.

 ![Visual Studio 오류 목록 Bing 검색](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 이 경우 오류 코드 및 텍스트에 대한 Bing 검색 결과를 호스트하는 탭이 Visual Studio 2015 내에서 실행됩니다. 결과는 인터넷의 다양한 소스에서 가져온 것이며 모두 유용한 것은 아닙니다.

 또는 **오류 목록**의 **코드** 열에서 하이퍼링크로 연결된 오류 코드 값을 클릭할 수 있습니다. 이 경우 오류 코드에 대한 Bing 검색이 시작됩니다.

### <a name="performing-static-code-analysis"></a>정적 코드 분석 수행
 "정적 코드 분석"은 "코드 관리에서 런타임 오류 또는 문제를 일으킬 수 있는 일반적인 문제가 있는지 내 코드를 자동으로 검사"하는 유용한 방법입니다. 빌드할 수 없게 하는 명백한 오류를 정리하고 나면 항상 이 분석을 실행하고 시간을 할애하여 생성되는 경고도 해결합니다. 몇 가지 코드 스타일 기술을 배울 수 있을 뿐 아니라 잠재적인 문제를 줄일 수 있습니다.

 Alt + F11 키를 누르거나, 왼쪽 메뉴에서 **분석-솔루션에서 코드 분석 실행 >** 선택 하 여 정적 코드 분석을 시작 합니다. 코드가 많은 경우 이 작업은 시간이 걸릴 수 있습니다.

 ![Visual Studio 2015 코드 분석 메뉴 항목](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 IDE 아래쪽에 있는 **오류 목록** 탭에 새로운 경고나 업데이트된 경고가 표시됩니다. 경고를 클릭하여 이동합니다.

 ![경고가 포함된 Visual Studio 2015 오류 목록](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 경고는 빨간색이 아니라 밝은 노랑-녹색 오류 표시선으로 식별됩니다. 경고 위로 마우스를 가져가서 자세한 내용을 보고, 마우스 오른쪽 단추로 클릭하여 수정 작업이나 리팩터링 옵션을 지원하는 상황에 맞는 메뉴를 표시합니다.

 ![Visual Studio 코드 분석 경고 가리키기](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>전구를 사용하여 코드 수정 또는 리팩터링
 전구는 인라인에서 코드를 리팩터링할 수 있게 해주는 Visual Studio 2015의 새로운 기능입니다. 전구를 통해 일반적인 경고를 빠르고 효율적으로 수정할 수 있습니다. 액세스하려면 경고 물결선을 마우스 오른쪽 단추로 클릭하거나 물결선을 마우스로 가리킨 다음 Ctrl+. 를 누르고 **빠른 작업**을 선택합니다.

 ![Visual Studio 2015 전구 빠른 옵션](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 해당 코드 줄에 적용할 수 있는 가능한 수정 또는 리팩터링 목록이 표시됩니다.

 ![Visual Studio 2015 전구 미리 보기](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 코드 분석기에서 수정, 리팩터링 또는 코드 개선 기회가 있다고 결정하는 위치마다 전구를 사용할 수 있습니다. 코드 줄을 클릭하고 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 연 다음 **빠른 옵션**을 선택합니다(또는 효율성을 원하는 경우 Ctrl+.를 누름). 사용할 수 있는 영역 리팩터링 또는 개선 옵션이 있으면 표시됩니다. 없는 경우 IDE의 왼쪽 아래 베젤에 `No quick options available here`라는 메시지가 표시됩니다.

 ![Visual Studio 2015 전구 ‘옵션 없음’ 텍스트](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 경험을 바탕으로 화살표 키와 Ctrl+. 를 빠르게 사용하여 빠른 옵션 리팩터링 기회를 확인하고 코드를 정리할 수 있습니다.

 전구에 대한 자세한 내용은 [전구를 사용하여 빠른 작업 수행](../ide/perform-quick-actions-with-light-bulbs.md)을 참조하세요.

### <a name="debugging-your-running-code"></a>실행 중인 코드 디버그
 성공적으로 코드를 빌드하고 약간의 정리 작업을 수행 했으므로 이제 F5 키를 누르거나 **디버그->디버깅 시작**을 선택 하 여 실행 합니다. 그러면 디버그 환경에서 앱이 시작되므로 해당 동작을 자세히 관찰할 수 있습니다. Visual Studio 2015 IDE는 앱이 실행되는 동안 변경됩니다. 기본 창 구성에서는 **출력** 창이 **자동/지역/모듈/조사식** 탭 창과 **호출 스택/중단점/예외 설정/출력** 탭 창이라는 새로운 두 개의 창으로 대체됩니다. 이러한 창에는 실행 시 앱의 변수, 스레드, 호출 스택 및 기타 다양한 동작을 검사 및 평가할 수 있게 해주는 여러 탭이 있습니다.

 ![VS2015 자동 및 호출 스택 창](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 앱에서 다양한 작업을 시도하고 변경 내용을 관찰합니다. 비정상적인 동작이 나타나면 Ctrl+Alt+Break를 누르거나 **일시 중지** 단추를 클릭하여 앱을 일시 중지합니다.

 ![Visual Studio 모두 중단 단추](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 F5 키를 누르거나 **계속** 단추를 클릭하여 앱을 계속 실행합니다.

 ![Visual Studio 디버그 계속 단추](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Shift+F5를 누르거나 **중지** 단추를 클릭하여 앱을 중지할 수 있습니다. 또는 단순히 앱의 주 창(또는 명령줄 대화 상자)을 닫을 수 있습니다.

 코드가 예상대로 정확히 완벽하게 실행되면 성공한 것입니다. 빌드 구성을 **릴리스**로 변경하고 배포를 위해 다시 빌드합니다. (전문가는 끝에 있는 단위 테스트에 대 한 비트로 점프할 수 있습니다.) 그러나 응답 하지 않거나 작동이 중단 되거나 이상한 결과를 제공 하는 경우 해당 문제의 소스를 찾아 버그를 수정 해야 합니다.

### <a name="setting-simple-breakpoints"></a>간단한 중단점 설정
 중단점은 신뢰할 수 있는 디버깅의 가장 기본적이고 필수적인 기능입니다. 중단점은 변수의 값, 메모리의 동작 또는 코드 분기의 실행 여부를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타냅니다. 중단점을 설정 및 제거한 후 프로젝트를 다시 빌드할 필요는 없습니다.

 중단하려는 줄의 끝 여백을 클릭하여 중단점을 설정하거나 코드 줄을 선택하고 F9 키를 누릅니다. 코드를 실행하면 이 코드 줄에 대한 명령이 실행되기 전에 중지됩니다.

 ![Visual Studio 중단점](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 코드가 중단될 때 표시된 코드 줄은 아직 실행되지 않았습니다. 이때 중단점으로 표시된 코드 줄에 대한 명령을 실행하고 변경된 값을 검사하는 것이 좋습니다. 이를 "한 단계씩 코드 실행"이라고 합니다. 표시된 코드가 메서드 호출인 경우 F11 키를 눌러 한 단계씩 코드를 실행할 수 있습니다. F10 키를 눌러 코드 줄을 "프로시저 단위로 실행"할 수도 있습니다. 중단점 단계 동작에 대한 자세한 내용은 [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)을 참조하세요.

 중단점의 일반적인 용도는 다음과 같습니다.

1. 크래시 또는 프로그램의 소스 범위를 좁히려면 실패를 유발 하는 메서드 호출의 코드를 통해 분산 합니다. 한 단계씩 코드를 실행하면서 위반하는 코드 줄을 찾을 때까지 중단점을 제거하고 더 가깝게 중단점을 다시 설정합니다.

2. 새 코드를 도입하는 경우 시작 부분에 중단점을 설정하고 한 단계씩 코드를 실행하여 예상대로 작동하는지 확인합니다.

3. 복잡한 동작을 구현한 경우 프로그램이 중단될 때 변수 및 데이터의 값을 검사할 수 있도록 알고리즘 코드에 대한 중단점을 설정합니다.

4. C 또는 C++ 코드를 작성하는 경우 메모리 관련 오류를 디버그할 때 주소 값(NULL 검색) 및 참조 횟수를 검사할 수 있도록 중단점을 사용하여 코드를 중지합니다.

   중단점 사용에 대 한 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md) 을 참조 하세요.

### <a name="setting-conditional-breakpoints"></a>조건부 중단점 설정
 루프 또는 재귀에 중단점이 있는 경우 또는 자주 한 단계씩 실행하는 많은 중단점이 있는 경우 조건부 중단점을 사용하여 특정 조건이 충족되는 경우에만 코드가 일시 중단되도록 합니다. 그렇지 않으면 F11 키를 많이 누르게 됩니다.

 조건부 중단점을 설정하고 변수가 특정 값으로 설정된 경우 또는 특정 임계값을 초과할 경우 코드를 일시 중단하려면 여백을 클릭하여 중단점을 설정한 다음 나타나는 호버 메뉴에서 "코그"를 선택합니다.

 ![Visual Studio 2015 중단점 설정](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 중단점 발생에 대한 특정 조건을 설정할 수 있는 다음과 같은 대화 상자가 나타납니다.

 ![Visual Studio 2015 조건부 중단점](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 조건부 중단점 평가에 사용되는 식을 선언하는 방법에 대한 자세한 내용은 Channel9 동영상 [Visual Studio 2015의 중단점 구성 환경](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)을 참조하세요.

### <a name="inspecting-your-code-at-run-time"></a>런타임에 코드 검사
 실행 중인 코드가 중단점을 적중하고 중단되는 경우 변수 및 호출 스택을 검사하여 문제를 확인할 수 있습니다. 값이 예상 범위 내에 있나요? 호출이 올바른 순서로 수행되나요?

 ![Visual Studio 2015&#45;시간 값 검사 실행](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 변수 위로 마우스를 가져가서 현재 포함된 값 및 참조를 확인합니다. 예상하지 않은 값이 표시되는 경우 이전 또는 호출하는 코드 줄에 버그가 있을 가능성이 큽니다. 중단점을 위로 이동하거나 기존 중단점에 조건을 추가하여 검색 범위를 더욱 좁힙니다.

 또한 Visual Studio 2015에서는 앱의 시간별 CPU 및 메모리 사용량을 관찰할 수 있는 진단 도구 창을 표시합니다. 이 창에서 예기치 않은 높은 CPU 사용량 또는 메모리 할당을 찾습니다. **조사식** 창 및 중단점과 함께 사용 하 여 예기치 않은 과도 한 사용 또는 릴리스되지 않은 리소스의 원인을 확인 합니다.

 ![Visual Studio 2015 진단 도구 창](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>단위 테스트 실행
 유닛 테스트는 앱이나 서비스에서 코드 경로를 실행하는 프로그램입니다. Visual Studio 2015에서는 관리 코드 및 네이티브 코드에 대한 Microsoft 유닛 테스트 프레임워크를 설치합니다. 유닛 테스트 프레임워크를 사용하여 유닛 테스트를 만들고, 실행하고, 이러한 테스트 결과를 보고합니다. 변경 시 단위 테스트를 다시 실행하여 코드가 여전히 제대로 작동하는지 테스트합니다. Visual Studio 2015 Enterprise를 사용하는 경우 빌드할 때마다 테스트를 자동으로 실행할 수 있습니다.

 시작하려면 [IntelliTest를 사용하여 코드에 대한 단위 테스트 생성](../test/generate-unit-tests-for-your-code-with-intellitest.md)을 참조하세요.

 Visual Studio 2015의 단위 테스트 및 단위 테스트를 통해 더 나은 품질의 코드를 만드는 방법에 대한 자세한 내용은 [단위 테스트 기본 사항](../test/unit-test-basics.md)을 참조하세요.

## <a name="see-also"></a>참고 항목
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md) [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md) [디버그 64 비트 응용 프로그램](../debugger/debug-64-bit-applications.md) [디버거 기본 사항](../debugger/debugger-basics.md)
