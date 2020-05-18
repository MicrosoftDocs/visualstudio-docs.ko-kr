---
title: 디버깅 작업 찾기
description: 앱을 디버그하는 데 도움이 되는 디버거 기능을 파악합니다.
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301148"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Visual Studio에서 디버깅 작업 찾기

디버깅 작업을 Visual Studio 디버거의 관련된 기능에 매핑하는 데 도움이 필요한 경우 이 문서에 제공된 링크를 사용하세요. 여기에는 디버그를 위해 코드를 일시 중단하고, 변수를 검사하고, 메시지를 **출력** 창에 보내는 등의 일반적인 작업이 포함됩니다. 디버거 기능 개요가 필요한 경우 [디버거 소개](debugger-feature-tour.md)를 참조하세요.

## <a name="pause-running-code"></a>실행 코드 일시 중지

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>버그를 포함할 수 있는 코드 줄을 검사하기 위해 실행 중인 코드를 일시 중지

중단점을 설정합니다. 자세한 내용은 [중단점 사용](using-breakpoints.md)을 참조하세요.

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>앱이 특정 상태에 도달할 때 앱 일시 중지 및 검사

조건부 논리를 사용하여 중단점이 활성화되는 위치 및 시기를 제어합니다. 자세한 내용은 [중단점 조건](using-breakpoints.md#breakpoint-conditions)을 참조하세요.

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>특정 개체의 속성 또는 값이 변경되는 경우에만 코드를 일시 중지

C++의 경우 [데이터 중단점](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)을 설정합니다. 
::: moniker range=">= vs-2019"
.NET Core 3을 사용하는 앱의 경우에도 [데이터 중단점](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)을 설정할 수 있습니다.
::: moniker-end

또는 C# 및 F#의 경우에만 [조건부 중단점을 사용하여 개체 ID를 추적](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)할 수 있습니다.

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>특정 반복에서 루프 내의 코드 일시 중지

**적중 횟수**를 조건으로 사용하여 중단점을 설정합니다. 자세한 내용은 [적중 횟수](using-breakpoints.md#set-a-hit-count-condition)를 참조하세요.

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>함수의 이름을 알지만 위치를 모르는 경우 함수 시작 부분에서 코드 일시 중지

함수 중단점을 사용하여 이 작업을 수행할 수 있습니다. 자세한 내용은 [함수 중단점 설정](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)을 참조하세요.

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>이름이 같은 여러 함수의 시작 부분에서 코드 일시 중지

동일한 이름을 가진 여러 함수가 있는 경우(오버로드된 함수 또는 다른 프로젝트의 함수) [함수 중단점](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)을 사용할 수 있습니다.

### <a name="manage-and-keep-track-of-your-breakpoints"></a>중단점 관리 및 추적

**중단점** 창을 사용합니다. 자세한 내용은 [중단점 관리](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)를 참조하세요.

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>특정 처리된 또는 처리되지 않은 예외가 throw될 때 코드 일시 중지 및 디버그

예외 도우미가 오류 발생 위치를 표시하지만 특정 오류를 일시 중지하고 디버그하려는 경우 [디버거에서 예외가 throw되면 중단하도록 지시](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)할 수 있습니다.

### <a name="set-a-breakpoint-from-the-call-stack"></a>호출 스택에서 중단점 설정

**호출 스택** 창에서 실행 흐름을 검사하거나 함수를 보는 동안 코드를 일시 중지하고 디버그하려면 [호출 스택 창에서 중단점 설정](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)을 참조하세요.

### <a name="pause-code-at-a-specific-assembly-instruction"></a>특정 어셈블리 명령에서 코드 일시 중지

[디스어셈블리 창에서 중단점을 설정](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)하여 이 작업을 수행할 수 있습니다.

## <a name="execute-code"></a>코드 실행

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>디버그하는 동안 코드를 단계별로 실행하는 명령에 대해 알아봅니다.

자세한 내용은 [디버거로 코드 탐색](navigating-through-code-with-the-debugger.md)을 참조하세요.

## <a name="inspect-data"></a>데이터 검사

### <a name="check-the-value-of-variables-while-running-your-app"></a>앱을 실행하는 동안 변수 값을 확인

[데이터 팁](view-data-values-in-data-tips-in-the-code-editor.md)을 사용하여 변수를 마우스로 가리키거나 [자동 및 지역 창에서 변수를 검사](autos-and-locals-windows.md)합니다.

### <a name="observe-the-changing-value-of-a-specific-variable"></a>특정 변수의 값 변화를 관찰

변수에 조사식을 설정합니다. 자세한 내용은 [변수에 조사식 설정](watch-and-quickwatch-windows.md)을 참조하세요.

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>디버거 창에 너무 긴 문자열 보기

디버그하는 동안 기본 제공 [문자열 시각화 도우미](view-strings-visualizer.md)를 엽니다.

## <a name="configure-debugging"></a>디버깅 구성

### <a name="customize-information-shown-in-the-debugger"></a>디버거에 표시되는 정보를 사용자 지정

다른 디버거 창에서 개체 형식 이외의 정보를 값으로 표시해야 할 수 있습니다. C#, Visual Basic, F# 및 C++/CLI 코드의 경우 [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) 특성을 사용합니다. 더 많은 고급 옵션을 위해 [사용자 지정 시각화 도우미](create-custom-visualizers-of-data.md)를 만들어 UI를 사용자 지정할 수도 있습니다.

네이티브 C++의 경우 [NatVis 프레임워크](create-custom-views-of-native-objects.md)를 사용합니다.

### <a name="configure-debugger-settings"></a>디버거 설정 구성

디버거 옵션 및 디버거 프로젝트 설정을 구성하려면 [디버거 설정 및 준비](debugger-settings-and-preparation.md)를 참조하세요.

## <a name="additional-tasks"></a>추가 작업

### <a name="fix-an-exception"></a>예외 수정

[예외 수정](write-better-code-with-visual-studio.md#fix-an-exception)을 참조하세요.

### <a name="edit-code-during-a-debugging-session"></a>디버깅 세션 중에 코드 편집

[편집하며 계속하기](edit-and-continue.md)를 사용합니다. XAML의 경우 [XAML 핫 다시 로드](../xaml-tools/xaml-hot-reload.md)를 사용합니다.

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>코드를 수정하지 않고 출력 창에 메시지 보내기

추적점을 설정합니다. 자세한 내용은 [추적점 사용](using-tracepoints.md)을 참조하세요.

## <a name="view-the-order-in-which-functions-are-called"></a>함수가 호출되는 순서 보기

[호출 스택을 보는 방법](how-to-use-the-call-stack-window.md)을 참조하세요.

### <a name="debug-on-remote-machines"></a>원격 컴퓨터에서 디버그

[원격 디버깅](remote-debugging.md)을 참조하세요.

### <a name="debug-an-app-that-is-already-running"></a>이미 실행 중인 앱 디버그

[실행 중인 프로세스에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

### <a name="debug-multithreaded-applications"></a>다중 스레드 애플리케이션 디버그

[다중 스레드 애플리케이션 디버그](debug-multithreaded-applications-in-visual-studio.md)를 참조하세요.

### <a name="fix-performance-issues"></a>성능 문제 해결

[프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)를 참조하세요.