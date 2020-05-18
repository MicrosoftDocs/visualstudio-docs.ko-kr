---
title: 디버거 팁과 요령
description: Visual Studio 디버거에서 지원하는 몇 가지 덜 알려진 기능에 대해 알아봅니다.
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301178"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Visual Studio의 디버거 관련 생산성 팁과 요령 배우기

이 항목을 읽고 Visual Studio 디버거에 대한 몇 가지 생산성 팁과 요령을 알아보세요. 디버거의 기본 기능에 대한 자세한 내용은 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요. 이 항목에서는 기능 둘러보기에 포함되지 않은 몇 가지 영역을 다룹니다.

## <a name="pin-data-tips"></a>데이터 고정 팁

디버그하는 동안 데이터 팁을 마우스로 자주 가리키는 경우 변수에 대한 데이터 팁을 고정하여 신속하게 액세스할 수 있습니다. 다시 시작한 후에도 변수는 고정된 상태로 유지됩니다. 데이터 팁을 고정하려면 고정 아이콘을 마우스로 가리킨 상태에서 클릭합니다. 여러 변수를 고정할 수 있습니다.

![데이터 고정 팁](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>코드를 편집하며 디버깅 계속하기(C#, VB, C++)

Visual Studio에서 지원되는 대부분의 언어에서 디버깅 세션 중에 코드를 편집하고 디버깅을 계속할 수 있습니다. 이 기능을 사용하려면 디버거에서 일시 중지된 동안 커서를 사용하여 코드를 클릭하고 편집을 수행한 후 **F5**, **F10** 또는 **F11**을 눌러 디버깅을 계속합니다.

![디버깅 편집하며 계속하기](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

기능 사용 및 기능 제한에 대한 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML 코드를 편집하며 디버깅 계속하기

디버깅 세션 중 XAML 코드를 수정하려면 [XAML 핫 다시 로드를 사용하여 코드 작성 및 실행 중인 XAML 코드 디버그](../xaml-tools/xaml-hot-reload.md)를 참조하세요.

## <a name="debug-issues-that-are-hard-to-reproduce"></a>재현하기 어려운 문제 디버그

앱의 특정 상태를 재현하기 어렵거나 시간이 오래 걸리는 경우 조건부 중단점 사용이 도움이 될 수 있는지 고려해 보세요. 앱이 필요한 상태(예: 변수가 잘못된 데이터를 저장하는 상태)가 될 때까지 앱 코드가 중단되지 않도록 [조건부 중단점](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) 및 필터 중단점을 사용할 수 있습니다. 조건은 식, 필터, 적중 횟수 등을 사용하여 설정할 수 있습니다.

#### <a name="to-create-a-conditional-breakpoint"></a>조건부 중단점을 만들려면

1. 중단점 아이콘(빨간색 공)을 마우스 오른쪽 단추로 클릭하고 **조건**을 선택합니다.

2. **중단점 설정** 창에 식을 입력합니다.

    ![조건부 중단점](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 다른 유형의 조건에 관심이 있는 경우 **중단점 설정** 대화 상자에서 **조건 식** 대신 **필터**를 선택한 다음 필터 팁을 따릅니다.

## <a name="configure-the-data-to-show-in-the-debugger"></a>디버거에 표시할 데이터 구성

C#, Visual Basic 및 C++(C++/CLI 코드만 해당)의 경우 [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) 특성을 사용하여 디버거에 표시할 정보를 지시할 수 있습니다. C++ 코드의 경우에는 [Natvis 시각화](create-custom-views-of-native-objects.md)를 사용하여 동일한 작업을 수행할 수 있습니다.

## <a name="change-the-execution-flow"></a>실행 흐름 변경

디버거가 코드 줄에서 일시 중지된 상태에서 마우스를 사용하여 왼쪽의 노란색 화살표 포인터를 잡습니다. 노란색 화살표 포인터를 코드 실행 경로의 다른 지점으로 이동합니다. 그런 다음 F5 키 또는 step 명령을 사용하여 앱을 계속 실행합니다.

![실행 포인터 이동](../debugger/media/dbg-tour-move-the-execution-pointer.gif "실행 포인터 이동")

실행 흐름을 변경하면 디버거를 다시 시작하지 않고도 다른 코드 실행 경로를 테스트하거나 코드를 다시 실행하는 등의 작업을 수행할 수 있습니다.

> [!WARNING]
> 이 기능을 주의 깊게 사용해야 하는 경우가 많으며 도구 설명에 경고가 표시됩니다. 다른 경고도 표시될 수 있습니다. 포인터를 이동하면 앱을 이전 애플리케이션 상태로 되돌릴 수 없습니다.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>범위를 벗어난 개체 추적(C#, Visual Basic)

**조사식** 창과 같은 디버거 창을 사용하여 변수를 쉽게 볼 수 있습니다. 그러나 **조사식** 창의 범위를 벗어난 변수는 회색으로 표시될 수 있습니다. 일부 애플리케이션 시나리오에서는 변수가 범위를 벗어난 경우에도 변수 값이 변경될 수 있으므로 세밀하게 감시해야 할 수 있습니다(예를 들어 변수가 가비지 수집될 수 있음). **조사식** 창에서 변수에 대한 개체 ID를 만들어 변수를 추적할 수 있습니다.

#### <a name="to-create-an-object-id"></a>개체 ID를 만들려면

1. 추적하려는 변수 근처에 중단점을 설정합니다.

2. 디버거(**F5**)를 시작하고 중단점에서 중지합니다.

3. **지역** 창에서 변수를 찾아(**디버그 > Windows > 지역**) 변수를 마우스 오른쪽 단추로 클릭하고 **개체 ID**를 선택합니다.

    ![개체 ID 만들기](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. **$** 창에 **지역** 창을 닫습니다. 이 변수는 개체 ID입니다.

5. 개체 ID 변수를 마우스 오른쪽 단추로 클릭하고 **조사식 추가**를 선택합니다.

자세한 내용은 [개체 ID 만들기](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)를 참조하세요.

## <a name="view-return-values-for-functions"></a>함수의 반환 값 보기

함수의 반환 값을 보려면 코드를 단계별로 실행하는 동안 **자동** 창에 표시되는 함수를 확인합니다. 함수의 반환 값을 보려면 관심 있는 함수가 이미 실행되었는지 확인합니다(현재 함수 호출에서 중지된 경우 **F10** 키를 누름). 창이 닫히면 **디버그 > Windows > 자동**을 사용하여 **자동** 창을 엽니다.

![자동 창](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

또한 **직접 실행** 창에 함수를 입력하여 반환 값을 볼 수 있습니다. (**디버그 > Windows > 직접 실행**을 사용하여 엽니다.)

![직접 실행 창](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

**조사식** 및 **즉시 실행** 창에서 `$ReturnValue`와 같은 [의사 변수](../debugger/pseudovariables.md)를 사용할 수도 있습니다.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>시각화 도우미에서 문자열 검사

문자열로 작업할 때 서식이 지정된 전체 문자열을 보는 것이 도움이 될 수 있습니다. 일반 텍스트, XML, HTML 또는 JSON 문자열을 보려면 문자열 값을 포함하는 변수를 마우스로 가리킨 상태에서 돋보기 아이콘 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 도우미 아이콘")을 클릭합니다.

![문자열 시각화 도우미 열기](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

문자열 시각화 도우미는 문자열 형식에 따라 문자열 형식이 잘못되었는지 여부를 확인하는 데 도움이 될 수 있습니다. 예를 들어 빈 **값** 필드는 시각화 도우미 형식이 해당 문자열을 인식하지 않음을 나타냅니다. 자세한 내용은 [문자열 시각화 도우미 대화 상자](../debugger/string-visualizer-dialog-box.md)를 참조하세요.

![JSON 문자열 시각화 도우미](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

디버거 창에 표시되는 DataSet 및 DataTable 개체와 같은 몇 가지 다른 형식의 경우 기본 제공 시각화 도우미를 열 수도 있습니다.

## <a name="break-into-code-on-handled-exceptions"></a>처리된 예외에서 코드 중단

디버거는 처리되지 않은 예외에서 코드를 중단합니다. 그러나 처리된 예외(예: `try/catch` 블록 내에서 발생하는 예외)는 버그의 소스가 될 수도 있으므로 발생 시기를 조사해야 할 수 있습니다. **예외 설정** 대화 상자에서 옵션을 구성하여 처리된 예외에서도 코드를 중단하도록 디버거를 구성할 수 있습니다. **디버그 > Windows > 예외 설정**을 선택하여 이 대화 상자를 엽니다.

**예외 설정** 대화 상자를 사용하면 디버거에 특정 예외에서 코드를 중단하도록 지시할 수 있습니다. 아래 그림에서는 `System.NullReferenceException`이 발생할 때마다 디버거가 코드를 중단합니다. 자세한 내용은 [예외 관리](../debugger/managing-exceptions-with-the-debugger.md)를 참조하세요.

![예외 설정 대화 상자](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>교착 상태 및 경합 상태 디버그

다중 스레드 앱에 공통적인 문제 유형을 디버그해야 하는 경우 디버그하는 동안 스레드의 위치를 확인하는 것이 도움이 되는 경우가 많습니다. **소스의 스레드 표시** 단추를 사용하여 이 작업을 쉽게 수행할 수 있습니다.

#### <a name="to-show-threads-in-your-source-code"></a>소스 코드에서 스레드를 표시하려면

1. 디버그하는 동안 **디버그 도구** 모음에서 **소스의 스레드 표시** 단추 ![소스의 스레드 표시](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")를 클릭합니다.

2. 창 왼쪽의 여백을 확인합니다. 이 줄에는 실 두 가닥 모양의  스레드 마커 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")이 표시됩니다. 스레드 마커는 이 위치에서 스레드가 중지되었음을 나타냅니다.

    스레드 마커는 중단점에 의해 일부가 가려질 수 있습니다.

3. 스레드 마커에 포인터를 올려 놓습니다. DataTips가 나타납니다. DataTip을 통해 중지된 각 스레드의 이름과 스레드 ID 번호를 알 수 있습니다.

    [병렬 스택](../debugger/get-started-debugging-multithreaded-apps.md) 창에서도 스레드 위치를 볼 수 있습니다.

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>웹 서비스 및 네트워크 리소스 페이로드 검사(UWP)

UWP 앱에서 `Windows.Web.Http` API를 사용하여 수행되는 네트워크 작업을 분석할 수 있습니다. 이 도구를 사용하면 웹 서비스 및 네트워크 리소스를 쉽게 디버그할 수 있습니다. 이 도구를 사용하려면 **디버그 > 성능 프로파일러**를 선택합니다. **네트워크**를 선택한 다음 **시작**을 선택합니다. 앱에서 `Windows.Web.Http`를 사용하는 시나리오를 확인한 다음 **컬렉션 중지**를 선택하여 보고서를 생성합니다.

![네트워크 사용량 프로파일링 도구](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

요약 뷰에서 작업을 선택하여 세부 정보를 확인할 수 있습니다.

![네트워크 사용량 도구의 세부 정보](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

자세한 내용은 [네트워크 사용량](../profiling/network-usage.md)을 참조하세요.
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a> 디버거를 앱에 연결하는 방법 자세히 알아보기(C#, C++, Visual Basic, F#)

실행 중인 앱에 연결하기 위해 디버거는 디버그하려는 애플리케이션의 정확히 동일한 빌드에 대해 생성된 기호(.pdb) 파일을 로드합니다. 일부 시나리오에서는 기호 파일에 대한 약간의 지식이 도움이 될 수 있습니다. **모듈** 창을 사용하여 Visual Studio가 기호 파일을 로드하는 방법을 검토할 수 있습니다.

디버그하는 동안 **디버그 > Windows > 모듈**을 선택하여 **모듈** 창을 엽니다. **모듈** 창에서는 디버거가 사용자 코드로 처리하는 모듈, 즉 [  내 코드](../debugger/just-my-code.md)와 모듈에 대한 기호 로드 상태를 확인할 수 있습니다. 대부분의 시나리오에서 디버거는 사용자 코드에 대한 기호 파일을 자동으로 검색하지만 .NET 코드, 시스템 코드 또는 타사 라이브러리 코드를 단계별로 실행(또는 디버그)하려면 올바른 기호 파일을 가져오기 위해 추가 단계가 필요합니다.

![모듈 창에서 기호 정보 보기](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

마우스 오른쪽 단추를 클릭하고 **기호 로드**를 선택하여 **모듈** 창에서 직접 기호 정보를 로드할 수 있습니다.

앱 개발자가 일치하는 기호 파일 없이(공간을 줄이기 위해) 앱을 제공하지만 나중에 릴리스 버전을 디버그할 수 있도록 해당 빌드에 대한 일치하는 기호 파일의 복사본을 유지하는 경우가 있습니다.

디버거가 코드를 사용자 코드로 분류하는 방법을 확인하려면 [내 코드만](../debugger/just-my-code.md)을 참조하세요. 기호 파일에 대한 자세한 내용은 [Visual Studio 디버거에서 기호 파일(.pdb) 및 소스 파일 지정](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="learn-more"></a>자세한 정보

추가 팁과 요령 및 자세한 내용은 다음 블로그 게시물을 참조하세요.

- [7 lesser known hacks for debugging in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 hidden gems in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>참조

[바로 가기 키](../ide/productivity-shortcuts.md)
