﻿---
title: 디버거의 팁과 요령
description: Visual Studio 디버거에서 지 원하는 몇 가지 덜 알려진 기능에 대해 알아봅니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301178"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>비주얼 스튜디오에서 디버거를 위한 생산성 팁과 트릭 알아보기

이 항목을 읽고 Visual Studio 디버거에 대한 몇 가지 생산성 팁과 요령을 알아보십시오. 디버거의 기본 기능에 대한 자세한 내용은 [디버거](../debugger/debugger-feature-tour.md)를 먼저 참조하십시오. 이 항목에서는 기능 투어에 포함되지 않은 일부 영역을 다룹니다.

## <a name="pin-data-tips"></a>데이터 팁 핀

디버깅하는 동안 데이터 팁 위로 자주 마우스를 가져가는 경우 변수에 대한 데이터 팁을 고정하여 빠르게 액세스할 수 있습니다. 변수는 다시 시작한 후에도 고정된 상태로 유지됩니다. 데이터 팁을 고정하려면 핀 아이콘을 마우스로 가리키면서 클릭합니다. 여러 변수를 고정할 수 있습니다.

![데이터 팁 고정](../debugger/media/dbg-tips-data-tips-pinned.png "피닝데이터팁")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>코드를 편집하고 디버깅을 계속합니다(C#, VB, C++)

Visual Studio에서 지원되는 대부분의 언어에서 디버깅 세션 중에 코드를 편집하고 디버깅을 계속할 수 있습니다. 이 기능을 사용하려면 디버거에서 일시 중지된 동안 커서를 사용하여 코드를 클릭하고 편집을 수행한 후 **F5**, **F10** 또는 **F11**을 눌러 디버깅을 계속합니다.

![디버깅 편집하며 계속하기](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

기능 사용 및 기능 제한에 대한 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML 코드 편집 및 디버깅 계속

디버깅 세션 중 XAML 코드를 수정하려면 [XAML 핫 다시 로드를 사용하여 코드 작성 및 실행 중인 XAML 코드 디버그](../xaml-tools/xaml-hot-reload.md)를 참조하세요.

## <a name="debug-issues-that-are-hard-to-reproduce"></a>재현하기 어려운 디버그 문제

앱에서 특정 상태를 다시 만드는 것이 어렵거나 시간이 많이 걸리는 경우 조건부 중단점을 사용하는 것이 도움이 될 수 있는지 고려합니다. [조건부 중단점과](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) 필터 중단점을 사용하여 앱이 원하는 상태(예: 변수가 잘못된 데이터를 저장하는 상태)에 들어갈 때까지 앱 코드가 중단되지 않도록 할 수 있습니다. 식, 필터, 적중 횟수 등을 사용하여 조건을 설정할 수 있습니다.

#### <a name="to-create-a-conditional-breakpoint"></a>조건부 중단점을 만들려면

1. 중단점 아이콘(빨간색 공)을 마우스 오른쪽 단추로 클릭하고 **조건을**선택합니다.

2. **중단점 설정** 창에서 식을 입력합니다.

    ![조건부 중단점](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "조건부 중단점")

3. 다른 유형의 조건에 관심이 있는 경우 **중단점 설정** 대화 상자에서 **조건부 식** 대신 **필터를** 선택한 다음 필터 팁을 따릅니다.

## <a name="configure-the-data-to-show-in-the-debugger"></a>디버거에 표시할 데이터 구성

C#, Visual Basic 및 C++(C++/CLI 코드만 해당)의 경우 디버거에게 [디버거디스플레이](../debugger/using-the-debuggerdisplay-attribute.md) 특성을 사용하여 표시할 정보를 알려줄 수 있습니다. C++ 코드의 경우 [Natvis 시각화를](create-custom-views-of-native-objects.md)사용하여 동일한 작업을 수행할 수 있습니다.

## <a name="change-the-execution-flow"></a>실행 흐름 변경

디버거가 코드 줄에서 일시 중지된 경우 마우스를 사용하여 왼쪽에 있는 노란색 화살표 포인터를 잡습니다. 노란색 화살표 포인터를 코드 실행 경로의 다른 지점으로 이동합니다. 그런 다음 F5 또는 단계 명령을 사용하여 앱을 계속 실행합니다.

![실행 포인터 이동](../debugger/media/dbg-tour-move-the-execution-pointer.gif "실행 포인터 이동")

실행 흐름을 변경하면 디버거를 다시 시작하지 않고도 다른 코드 실행 경로를 테스트하거나 코드를 다시 실행하는 등의 작업을 수행할 수 있습니다.

> [!WARNING]
> 이 기능을 주의 깊게 사용해야 하는 경우가 많으며 도구 설명에 경고가 표시됩니다. 다른 경고도 표시될 수 있습니다. 포인터를 이동하면 앱을 이전 응용 프로그램 상태로 되돌릴 수 없습니다.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>범위를 벗어난 개체 추적(C#, 시각적 기본)

**Watch** 창과 같은 디버거 창을 사용하여 변수를 쉽게 볼 수 있습니다. 그러나 **Watch** 창에서 변수가 범위를 벗어나면 변수가 회색으로 표시될 수 있습니다. 일부 앱 시나리오에서는 변수가 범위를 벗어난 경우에도 변수 값이 변경될 수 있으며 변수가 가비지 수집될 수 있습니다. **보기** 창에서 변수에 대한 개체 ID를 만들어 변수를 추적할 수 있습니다.

#### <a name="to-create-an-object-id"></a>개체 ID를 만들려면

1. 추적할 변수 근처에 중단점을 설정합니다.

2. **디버거(F5)를**시작하고 중단점에서 중지합니다.

3. **지역** 변수 창(Windows > > 지역 >**디버그)에서**변수를 찾아 변수를 마우스 오른쪽 단추로 클릭하고 **개체 ID 만들기를**선택합니다.

    ![개체 ID 만들기](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. **Locals** 창에 **$** 숫자와 더하기가 표시됩니다. 이 변수는 개체 ID입니다.

5. 개체 ID 변수를 마우스 오른쪽 단추로 클릭하고 **감시 추가를**선택합니다.

자세한 내용은 [개체 ID 만들기](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)를 참조하십시오.

## <a name="view-return-values-for-functions"></a>함수에 대한 반환 값 보기

함수에 대한 반환 값을 보려면 코드를 단계적 단계적으로 하는 동안 **자동** 창에 나타나는 함수를 확인합니다. 함수에 대한 반환 값을 보려면 관심 있는 함수가 이미 실행되었는지 확인하십시오(현재 함수 호출에서 중지된 경우 **F10을** 한 번 누르십시오). 창이 닫혀 있으면 **Windows > > 자동 > 사용하여** 자동 창을 **엽니다.**

![자동 창](../debugger/media/dbg-tips-autos-window.png "오토스윈도우")

또한 **즉시** 창에 함수를 입력하여 반환 값을 볼 수 있습니다. (즉시 **> 윈도우 > 디버그를**사용하여 엽니 > 다 .)

![즉각적인 창](../debugger/media/dbg-tips-immediate-window.png "즉각적인 창")

**시계** 및 **즉시** 창에서 와 같은 `$ReturnValue`의사 [변수를](../debugger/pseudovariables.md) 사용할 수도 있습니다.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>시각화 도우미에서 문자열 검사

문자열로 작업할 때 형식이 지정된 전체 문자열을 보는 것이 유용할 수 있습니다. 일반 텍스트, XML, HTML 또는 JSON 문자열을 보려면 현 값이 포함된 변수 위로 마우스를 가져가면서 돋보기 아이콘 ![VisualizerIcon을](../debugger/media/dbg-tips-visualizer-icon.png "시각화 도우미 아이콘") 클릭합니다.

![문자열 시각화 도우미 열기](../debugger/media/dbg-tips-string-visualizers.png "오픈스트링 비주얼라이저")

문자열 시각화 도우미는 문자열 유형에 따라 문자열이 잘못된 지 여부를 확인하는 데 도움이 될 수 있습니다. 예를 들어 빈 **값** 필드는 시각화 도우미 형식에서 문자열이 인식되지 않음을 나타냅니다. 자세한 내용은 [문자열 시각화 도우미 대화 상자를](../debugger/string-visualizer-dialog-box.md)참조하십시오.

![JSON 문자열 시각화 도우미](../debugger/media/dbg-tips-string-visualizer-json.png "JSON스트링 비주얼라이저")

디버거 창에 나타나는 DataSet 및 DataTable 개체와 같은 몇 가지 다른 형식의 경우 기본 제공 시각화 도우미를 열 수도 있습니다.

## <a name="break-into-code-on-handled-exceptions"></a>처리된 예외에 대한 코드 나누기

디버거가 처리되지 않은 예외에 대해 코드를 침입합니다. 그러나 처리된 예외(예: `try/catch` 블록 내에서 발생하는 예외)는 버그의 원인이 될 수 있으며 버그가 발생할 때 조사할 수도 있습니다. **예외 설정** 대화 상자에서 옵션을 구성하여 처리된 예외에 대한 코드에 침입하도록 디버거를 구성할 수 있습니다. **> Windows > 예외 설정 > 디버그를**선택하여 이 대화 상자를 엽니다.

**예외 설정** 대화 상자를 사용하면 디버거에게 특정 예외에 대한 코드에 침입하도록 알릴 수 있습니다. 아래 그림에서 디버거가 발생할 때마다 코드에 `System.NullReferenceException` 침입합니다. 자세한 내용은 [예외 관리를](../debugger/managing-exceptions-with-the-debugger.md)참조하십시오.

![예외 설정 대화 상자](../debugger/media/dbg-tips-exception-settings.png "예외설정디아로그박스")

## <a name="debug-deadlocks-and-race-conditions"></a>교착 상태 및 경합 조건 디버그

다중 스레드 앱에 공통적인 문제의 종류를 디버깅해야 하는 경우 디버깅하는 동안 스레드 위치를 보는 데 도움이 되는 경우가 많습니다. **소스의 스레드 표시 단추를** 사용하여 쉽게 이 작업을 수행할 수 있습니다.

#### <a name="to-show-threads-in-your-source-code"></a>소스 코드에 스레드를 표시하려면

1. 디버깅하는 동안 **디버그** 도구 모음의 ![소스에서](../debugger/media/dbg-multithreaded-show-threads.png "스레드 마커") 스레드 표시 단추에서 **스레드 표시를** 클릭합니다.

2. 창 왼쪽의 여백을 확인합니다. 이 줄에는 두 개의 천 나사와 유사한 *스레드 마커* 아이콘스레드 ![마커가](../debugger/media/dbg-thread-marker.png "스레드 마커") 표시됩니다. 스레드 마커는 이 위치에서 스레드가 중지되었음을 나타냅니다.

    스레드 마커는 중단점에 의해 부분적으로 숨길 수 있습니다.

3. 스레드 마커에 포인터를 올려 놓습니다. DataTips가 나타납니다. DataTip을 통해 중지된 각 스레드의 이름과 스레드 ID 번호를 알 수 있습니다.

    [병렬 스택 창에서](../debugger/get-started-debugging-multithreaded-apps.md)스레드의 위치를 볼 수도 있습니다.

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>웹 서비스 및 네트워크 리소스(UWP)에 대한 페이로드 검사

UWP 앱에서 API를 사용하여 수행된 `Windows.Web.Http` 네트워크 작업을 분석할 수 있습니다. 이 도구를 사용하여 웹 서비스 및 네트워크 리소스를 디버깅할 수 있습니다. 이 도구를 사용하려면 **성능 프로파일러 > 디버그를**선택합니다. **네트워크**를 선택한 다음 **시작을**선택합니다. 앱에서 `Windows.Web.Http`를 사용하는 시나리오를 확인한 다음 **컬렉션 중지**를 선택하여 보고서를 생성합니다.

![네트워크 사용량 프로파일링 도구](../profiling/media/prof-tour-network-usage.png "네트워크 사용법ProfTool")

요약 뷰에서 작업을 선택하여 세부 정보를 확인할 수 있습니다.

![네트워크 사용량 도구의 세부 정보](../profiling/media/prof-tour-network-usage-details.png "상세뷰네트워크사용법")

자세한 내용은 [네트워크 사용량](../profiling/network-usage.md)을 참조하세요.
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>디버거가 앱에 연결하는 방법(C#, C++, 비주얼 베이직, F#)에 대해 더 잘 알고 있습니다.

실행 중인 앱에 연결하기 위해 디버거는 디버깅하려는 앱의 동일한 빌드에 대해 생성된 기호(.pdb) 파일을 로드합니다. 일부 시나리오에서는 기호 파일에 대한 약간의 지식이 도움이 될 수 있습니다. Visual Studio가 모듈 창을 사용하여 기호 파일을 로드하는 방법을 검사할 수 **있습니다.**

디버깅하는 동안 **모듈** 창을 열면 **Windows > 모듈에서 디버그 > 선택합니다.** **모듈** 창에서는 디버거가 사용자 코드 또는 [*내 코드로*](../debugger/just-my-code.md)취급하는 모듈과 모듈의 기호 로드 상태를 알 수 있습니다. 대부분의 시나리오에서 디버거는 사용자 코드에 대한 기호 파일을 자동으로 찾지만 .NET 코드, 시스템 코드 또는 타사 라이브러리 코드를 단계별로 입력(또는 디버깅)하려면 올바른 심볼 파일을 얻으려면 추가 단계가 필요합니다.

![모듈 창에서 기호 정보 보기](../debugger/media/dbg-tips-modules-window.png "기호 보기정보")

마우스 오른쪽 단추를 클릭하고 **기호 로드를**선택하여 **모듈** 창에서 직접 기호 정보를 로드할 수 있습니다.

경우에 따라 앱 개발자는 일치하는 심볼 파일없이 앱을 제공하지만(발자국을 줄이기 위해) 나중에 릴리스된 버전을 디버깅할 수 있도록 빌드에 일치하는 기호 파일의 복사본을 유지합니다.

디버거가 코드를 사용자 코드로 분류하는 방법을 알아보려면 [내 코드 만](../debugger/just-my-code.md)을 참조하십시오. 기호 파일에 대한 자세한 내용은 [Visual Studio 디버거에서 기호(.pdb) 및 소스 파일 지정을](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)참조하십시오.

## <a name="learn-more"></a>자세한 정보

추가 팁과 요령 및 자세한 내용은 다음 블로그 게시물을 참조하세요.

- [비주얼 스튜디오에서 디버깅에 대한 7 덜 알려진 해킹](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [비주얼 스튜디오에서 7 숨겨진 보석](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>참고 항목

[키보드 단축키](../ide/productivity-shortcuts.md)
