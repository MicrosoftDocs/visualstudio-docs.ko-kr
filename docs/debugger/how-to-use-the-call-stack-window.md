---
title: 디버거에서 호출 스택 보기 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21573f1f8bd49782739027f7dfc2034bb7501a2f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535982"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>디버거에서 호출 스택 보기 및 호출 스택 창 사용

**호출 스택** 창에서 현재 스택에 있는 함수 또는 프로시저 호출을 볼 수 있습니다. **호출 스택** 창에는 메서드와 함수가 호출되는 순서가 표시됩니다. 호출 스택은 앱의 실행 흐름을 검사하고 파악할 수 있는 좋은 방법입니다.

호출 스택의 일부에 대해 [디버그 기호](#bkmk_symbols)를 사용할 수 없는 경우 **호출 스택** 창에는 호출 스택의 해당 부분에 대한 올바른 정보가 표시되지 않고 대신 다음과 같이 표시될 수 있습니다.

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> **호출 스택** 창은 Eclipse와 같은 일부 IDE의 디버그 관점과 비슷합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 여기서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택합니다.  [설정 다시 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="view-the-call-stack-while-in-the-debugger"></a>디버거에서 호출 스택 보기

- 디버그하는 동안 **디버그** 메뉴에서 **창 > 호출 스택**을 선택합니다.

  ![호출 스택 창](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

노란색 화살표는 현재 실행 포인터가 있는 스택 프레임을 나타냅니다. 기본적으로 이 스택 프레임의 정보는 소스, **로컬**, **자동**, **조사식** **디스어셈블리** 창에 표시됩니다. 디버거 컨텍스트를 스택의 다른 프레임으로 변경하려면 [다른 스택 프레임으로 전환](#bkmk_switch)합니다.

## <a name="display-non-user-code-in-the-call-stack-window"></a>사용자 코드가 아닌 코드를 호출 스택 창에 표시

- **호출 스택** 창에서 마우스 오른쪽 단추를 클릭하고 **외부 코드 표시**를 선택합니다.

사용자 코드가 아닌 코드는 [내 코드만](../debugger/just-my-code.md)을 사용하도록 설정했을 때 표시되지 않는 모든 코드입니다. 사용자 코드가 아닌 코드 프레임은 관리 코드에서 기본적으로 숨겨집니다. 사용자 코드가 아닌 코드 프레임 대신 다음과 같은 표기법이 표시됩니다.

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> 다른 스택 프레임으로 전환(디버거 컨텍스트 변경)

1. **호출 스택** 창에서, 보려는 코드와 데이터가 포함된 스택 프레임을 마우스 오른쪽 단추로 클릭합니다.

    또는 **호출 스택** 창에서 프레임을 두 번 클릭하여 해당 프레임으로 전환할 수 있습니다.

2. **프레임으로 전환**을 선택합니다.

     선택한 스택 프레임 옆에 끝이 굽은 녹색 화살표가 나타납니다. 실행 포인터는 여전히 노란색 화살표로 표시되어 있는 원래 프레임에 그대로 있습니다. **디버그** 메뉴에서 **한 단계 실행** 또는 **계속**을 선택하면 선택한 프레임이 아닌 원래 프레임에서 실행이 계속됩니다.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>호출 스택에 있는 함수의 소스 코드 보기

- **호출 스택** 창에서 소스 코드를 보려는 함수를 마우스 오른쪽 단추로 클릭하고 **소스 코드로 이동**을 선택합니다.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>호출 스택 창에서 특정 함수까지 실행

- **호출 스택** 창에서 함수를 선택하고 마우스 오른쪽 단추를 클릭한 다음, **커서까지 실행**을 선택합니다.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>함수 호출의 종료 지점에 중단점 설정

- [Set a breakpoint at a call stack function](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)(호출 스택 함수에서 중단점 설정)을 참조하세요.

## <a name="display-calls-to-or-from-another-thread"></a>다른 스레드에서의 호출 또는 다른 스레드로의 호출 표시

- **호출 스택** 창을 마우스 오른쪽 단추로 클릭하고 **다른 스레드로 호출/다른 스레드에서 호출 포함**을 선택합니다.

## <a name="visually-trace-the-call-stack"></a>시각적으로 호출 스택 추적

디버그하는 동안 Visual Studio Enterprise(에만 해당)에서 호출 스택의 코드 맵을 볼 수 있습니다.

- **호출 스택** 창에서 바로 가기 메뉴를 엽니다. **코드 맵에 호출 스택 표시**(**Ctrl** + **Shift** +  **`** )를 선택합니다.

    자세한 내용은 [디버그하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조하세요.

![코드 맵에 호출 스택 표시](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>호출 스택에 있는 함수의 디스어셈블리 코드 보기(C#, C++, Visual Basic, F#)

- **호출 스택** 창에서 디스어셈블리 코드를 보려는 함수를 마우스 오른쪽 단추로 클릭하고 **디스어셈블리로 이동**을 선택합니다.

## <a name="change-the-optional-information-displayed"></a>표시되는 선택적 정보 변경

- **호출 스택** 창에서 마우스 오른쪽 단추를 클릭하고 **\<** 원하는 정보 **> 표시**를 설정하거나 선택 취소합니다.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> 모듈의 기호 로드(C#, C++, Visual Basic, F#)

**호출 스택** 창에서 현재 기호가 로드되어 있지 않은 코드에 대한 디버깅 기호를 로드할 수 있습니다. 이러한 기호는 Microsoft 공용 기호 서버에서 다운로드한 .NET 또는 시스템 기호일 수도 있고 디버깅 중인 컴퓨터의 기호 경로에 있는 기호일 수도 있습니다.

[기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

### <a name="to-load-symbols"></a>기호를 로드하려면

1. **호출 스택** 창에서 기호가 로드되지 않은 스택 프레임을 마우스 오른쪽 단추로 클릭합니다. 프레임이 흐리게 표시됩니다.

2. **기호 로드**를 가리킨 다음, **Microsoft 기호 서버**(사용 가능한 경우)를 선택하거나 기호 경로로 이동합니다.

### <a name="to-set-the-symbol-path"></a>기호 경로를 설정하려면

1. **호출 스택** 창의 바로 가기 메뉴에서 **기호 설정**을 선택합니다.

     **옵션** 대화 상자가 열리고 **기호** 페이지가 표시됩니다.

2. **기호 설정**을 선택합니다.

3. **옵션** 대화 상자에서 폴더 아이콘을 클릭합니다.

     **기호 파일(.pdb) 위치** 상자에 커서가 표시됩니다.

4. 디버그 중인 컴퓨터의 기호 위치에 대한 디렉터리 경로 이름을 입력합니다. 로컬 및 원격 디버깅의 경우 이 경로는 로컬 컴퓨터의 경로입니다.

5. **확인**을 선택하여 **옵션** 대화 상자를 닫습니다.

## <a name="see-also"></a>참조

- [호출 스택 창의 혼합 코드 및 누락된 정보](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [중단점 사용](../debugger/using-breakpoints.md)