---
title: 디버깅 작업 찾기
description: 앱을 디버깅하는 데 도움이 되는 디버거 기능 식별
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301148"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>비주얼 스튜디오에서 디버깅 작업 찾기

디버깅 작업을 관련있는 Visual Studio 디버거의 올바른 기능에 매핑하는 데 도움이 필요한 경우 이 문서에 제공된 링크를 사용하십시오. 여기에 있는 작업 목록에는 디버깅을 위해 코드를 일시 중지하고, 변수를 검사하고, **출력** 창으로 메시지를 보내는 등의 일반적인 작업이 포함됩니다. 디버거 기능에 대한 개요가 필요한 경우 [디버거를 먼저 확인하십시오.](debugger-feature-tour.md)

## <a name="pause-running-code"></a>실행 중인 코드 일시 중지

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>실행 중인 코드를 일시 중지하여 버그가 포함될 수 있는 코드 줄을 검사합니다.

중단점을 설정합니다. 자세한 내용은 [중단점 사용을](using-breakpoints.md)참조하십시오.

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>특정 상태에 도달하면 앱을 일시 중지하고 검사합니다.

조건부 중단점을 사용하여 중단점이 활성화되는 위치와 시기를 제어합니다. 자세한 내용은 [중단점 조건을](using-breakpoints.md#breakpoint-conditions)참조하십시오.

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>특정 개체의 속성 또는 값이 변경되는 경우에만 코드 일시 중지

C++의 경우 [데이터 중단점을](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)설정합니다. 
::: moniker range=">= vs-2019"
.NET Core 3을 사용하는 앱의 경우 [데이터 중단점을](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)설정할 수도 있습니다.
::: moniker-end

그렇지 않으면 C# 및 F#만의 [경우 조건부 중단점을 가진 개체 ID를 추적할](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)수 있습니다.

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>특정 반복에서 루프 내부의 코드 일시 중지

**적중 횟수를** 조건으로 사용하여 중단점을 설정합니다. 자세한 내용은 [적중 횟수를](using-breakpoints.md#set-a-hit-count-condition)참조하십시오.

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>함수 이름을 알고 있지만 해당 위치를 알지 못하는 경우 함수 시작 시 코드를 일시 중지합니다.

함수 중단점으로 이 작업을 수행할 수 있습니다. 자세한 내용은 [함수 중단점 설정](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)을 참조하십시오.

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>같은 이름의 여러 함수가 시작될 때 코드 일시 중지

이름이 같은 여러 함수(다른 프로젝트의 오버로드된 함수 또는 함수)가 있는 경우 [함수 중단점을](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)사용할 수 있습니다.

### <a name="manage-and-keep-track-of-your-breakpoints"></a>중단점 관리 및 추적

**중단점** 창을 사용합니다. 자세한 내용은 [중단점 관리를](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)참조하십시오.

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>특정 처리 되거나 처리 되지 않은 예외가 throw 될 때 코드를 일시 중지 하 고 디버그

예외 도우미는 오류가 발생한 위치를 보여 주지만 특정 오류를 일시 중지하고 디버깅하려는 경우 [예외가 throw될 때 디버거에 중단을 알릴](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)수 있습니다.

### <a name="set-a-breakpoint-from-the-call-stack"></a>호출 스택에서 중단점 설정

실행 흐름을 검사하거나 **호출 스택** 창에서 함수를 보는 동안 코드를 일시 중지하고 디버깅하려면 호출 [스택 창에서 중단점 설정을](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)참조하십시오.

### <a name="pause-code-at-a-specific-assembly-instruction"></a>특정 어셈블리 명령에서 코드 일시 중지

[디스어셈블리 창에서 중단점을 설정하여](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)이 작업을 수행할 수 있습니다.

## <a name="execute-code"></a>코드 실행

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>디버깅하는 동안 코드를 단계별로 단계별로 안내하는 명령에 대해 알아보십시오.

자세한 내용은 [디버거를 통해 코드 탐색을](navigating-through-code-with-the-debugger.md)참조하십시오.

## <a name="inspect-data"></a>데이터 검사

### <a name="check-the-value-of-variables-while-running-your-app"></a>앱을 실행하는 동안 변수 값 확인

[데이터 팁을](view-data-values-in-data-tips-in-the-code-editor.md) 사용하여 변수 위로 마우스를 가져가거나 자동 및 [지역 창에서 변수를 검사합니다.](autos-and-locals-windows.md)

### <a name="observe-the-changing-value-of-a-specific-variable"></a>특정 변수의 변화 값 관찰

변수에 시계를 설정합니다. 자세한 내용은 [변수에 대한 시계 설정을](watch-and-quickwatch-windows.md)참조하십시오.

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>디버거 창에 너무 긴 문자열 보기

디버깅하는 동안 기본 제공 [문자열 시각화 도우미를](view-strings-visualizer.md) 엽니다.

## <a name="configure-debugging"></a>디버깅 구성

### <a name="customize-information-shown-in-the-debugger"></a>디버거에 표시된 정보 사용자 지정

개체 유형 이외의 정보를 다른 디버거 창의 값으로 표시할 수 있습니다. C#, 비주얼 베이직, F#및 C++/CLI 코드의 경우 [디버거디스플레이](using-the-debuggerdisplay-attribute.md) 특성을 사용합니다. 고급 옵션의 경우 [사용자 지정 시각화 도우미를](create-custom-visualizers-of-data.md)만들어 UI를 사용자 지정할 수도 있습니다.

네이티브 C++의 경우 [NatVis 프레임워크를](create-custom-views-of-native-objects.md)사용합니다.

### <a name="configure-debugger-settings"></a>디버거 설정 구성

디버거 옵션 및 디버거 프로젝트 설정을 구성하려면 [디버거 설정 및 준비를](debugger-settings-and-preparation.md)참조하십시오.

## <a name="additional-tasks"></a>추가 작업

### <a name="fix-an-exception"></a>예외 수정

[예외 수정을](write-better-code-with-visual-studio.md#fix-an-exception)참조하십시오.

### <a name="edit-code-during-a-debugging-session"></a>디버깅 세션 중 코드 편집

[편집을 사용하고 계속합니다.](edit-and-continue.md) XAML의 경우 [XAML 핫 다시로드](../xaml-tools/xaml-hot-reload.md)를 사용합니다.

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>코드를 수정하지 않고 출력 창으로 메시지 보내기

추적점을 설정합니다. 자세한 내용은 [추적점 사용을](using-tracepoints.md)참조하십시오.

## <a name="view-the-order-in-which-functions-are-called"></a>함수가 호출되는 순서 보기

[호출 스택을 보는 방법을](how-to-use-the-call-stack-window.md)참조하십시오.

### <a name="debug-on-remote-machines"></a>원격 컴퓨터에서 디버그

[원격 디버깅](remote-debugging.md)을 참조하십시오.

### <a name="debug-an-app-that-is-already-running"></a>이미 실행 중인 앱 디버그

[실행 중인 프로세스에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하십시오.

### <a name="debug-multithreaded-applications"></a>다중 스레드 애플리케이션 디버그

[디버그 다중 스레드 응용 프로그램을](debug-multithreaded-applications-in-visual-studio.md)참조하십시오.

### <a name="fix-performance-issues"></a>성능 문제 해결

[프로파일링 도구 에서 첫 번째 보기](../profiling/profiling-feature-tour.md) 보기