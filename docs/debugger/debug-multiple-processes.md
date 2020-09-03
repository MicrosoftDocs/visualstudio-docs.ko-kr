---
title: 여러 프로세스 디버그 | Microsoft Docs
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a61e0083b17fa095b419a2066a4f8b9c39dfb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350604"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>여러 프로세스 디버그(C#, Visual Basic, C++)

Visual Studio는 여러 프로세스가 있는 솔루션을 디버그할 수 있습니다. 프로세스를 시작 및 전환하고, 소스를 중단, 계속 및 단계별로 실행하고, 디버깅을 중지하고, 개별 프로세스에서 종료하거나 분리할 수 있습니다.

## <a name="start-debugging-with-multiple-processes"></a>여러 프로세스로 디버깅 시작

Visual Studio 솔루션에서 둘 이상의 프로젝트를 독립적으로 실행할 수 있는 경우 디버거가 시작할 프로젝트를 선택할 수 있습니다. 현재 시작 프로젝트는 **솔루션 탐색기**에 굵게 표시됩니다.

시작 프로젝트를 변경하려면 **솔루션 탐색기**에서 다른 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

시작 프로젝트로 설정하지 않고 **솔루션 탐색기**에서 프로젝트 디버깅을 시작하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **디버그** > **새 인스턴스 시작** 또는 **새 인스턴스를 한 단계씩 실행**을 선택합니다.

**솔루션 속성에서 시작 프로젝트 또는 여러 프로젝트를 설정하려면 다음을 수행합니다.**

1. **솔루션 탐색기**에서 솔루션을 선택한 다음, 도구 모음에서 **속성** 아이콘을 선택하거나 솔루션을 마우스 오른쪽 단추로 클릭하여 **속성**을 선택합니다.

1. **속성** 페이지에서 **공용 속성** > **시작 프로젝트**를 선택합니다.

   ![프로젝트의 시작 유형 변경](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. **현재 선택 영역**, **단일 시작 프로젝트** 및 프로젝트 파일을 선택하거나 **다중 시작 프로젝트**를 선택합니다.

   **다중 시작 프로젝트**를 선택하면 각 프로젝트에 대해 수행할 시작 순서와 작업을 변경할 수 있습니다. **시작**, **디버깅하지 않고 시작** 또는 **없음**.

1. **적용** 또는 **확인**을 선택하여 대화 상자를 적용하고 닫습니다.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> 프로세스에 연결

디버거는 원격 디바이스를 비롯하여 Visual Studio 외부의 프로세스에서 실행되는 앱에 *연결*할 수도 있습니다. 앱에 연결한 후에는 Visual Studio 디버거를 사용할 수 있습니다. 디버깅 기능이 제한될 수 있습니다. 앱이 디버그 정보로 빌드되었는지 여부, 앱의 소스 코드에 액세스할 수 있는지 여부 및 JIT 컴파일러에서 디버그 정보를 추적하는지 여부에 따라 달라집니다.

자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

**실행 중인 프로세스에 연결하려면:**

1. 앱이 실행 중인 상태에서 **디버그** > **프로세스에 연결**을 선택합니다.

   ![프로세스에 연결 대화 상자](../debugger/media/dbg_attachtoprocessdlg.png "프로세스에 연결 대화 상자")

1. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 프로세스를 선택한 다음, **연결**을 선택합니다.

>[!NOTE]
>자식 프로젝트가 동일한 솔루션에 있는 경우에도 디버거는 디버깅된 프로세스에서 시작되는 자식 프로세스에 자동으로 연결되지 않습니다. 자식 프로세스를 디버깅하려면 시작 후에 자식 프로세스에 연결하거나 새 디버거 인스턴스에서 자식 프로세스를 시작하도록 Windows 레지스트리 편집기를 구성합니다.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> 레지스트리 편집기를 사용하여 디버거에서 자동으로 프로세스 시작

경우에 따라 다른 프로세스에서 시작하는 앱의 시작 코드를 디버깅해야 할 수도 있습니다. 서비스 및 사용자 지정 설치 작업을 예로 들 수 있습니다. 디버거를 시작하고 앱에 자동으로 연결할 수 있습니다.

1. *regedit.exe*를 실행하여 Windows 레지스트리 편집기를 시작합니다.

1. 레지스트리 편집기에서 **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image 파일 실행 옵션**으로 이동합니다.

1. 디버거에서 시작할 응용 프로그램의 폴더를 선택합니다.

   앱이 자식 폴더로 나열되지 않은 경우 **이미지 파일 실행 옵션**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기** > **키**를 선택하고 앱 이름을 입력합니다. 또는 트리에서 새 키를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택한 다음, 앱 이름을 입력합니다.

1. 트리에서 새 키를 마우스 오른쪽 단추로 클릭하고 **새로 만들기** > **문자열 값**을 선택합니다.

1. 새 값의 이름을 **새 값 #1**에서 `debugger`로 변경합니다.

1. **디버거**를 마우스 오른쪽 단추로 클릭하고 **수정**을 선택합니다.

   ![문자열 편집 대화 상자](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "문자열 편집 대화 상자")

1. **문자열 편집** 대화 상자의 **값 데이터** 상자에 `vsjitdebugger.exe`를 입력한 다음, **확인**을 선택합니다.

   ![regedit.exe의 자동 디버거 시작 항목](../debugger/media/dbg_execution_automaticstart_result.png "regedit.exe의 자동 디버거 시작 항목")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> 여러 프로세스로 디버그
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

여러 프로세스로 애플리케이션을 디버깅하는 경우 중단, 단계별 실행 및 계속 디버거 명령은 기본적으로 모든 프로세스에 영향을 줍니다. 예를 들어 프로세스가 중단점에서 일시 중단되면 다른 모든 프로세스의 실행도 일시 중단됩니다. 이 기본 동작을 변경하여 실행 명령의 대상을 더욱 세부적으로 제어할 수 있습니다.

**한 프로세스가 중단될 때 모든 프로세스가 일시 중단되는지 여부를 변경하려면 다음을 수행합니다.**

- **도구**(또는 **디버그**) > **옵션** > **디버깅** > **일반**에서 **한 프로세스가 중단될 때 모든 프로세스 중단** 확인란을 선택하거나 선택 취소합니다.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> 명령 중단, 단계별 실행 및 계속 실행

다음 표에서는 **한 프로세스가 중단될 때 모든 프로세스 중단** 확인란을 선택하거나 선택 취소될 때 디버깅 명령의 동작에 대해 설명합니다.

|**Command**|선택함|선택 취소됨|
|-|-|-|
|**디버그**  > **모두 중단**|모든 프로세스가 중단됩니다.|모든 프로세스가 중단됩니다.|
|**디버그** > **계속**|모든 프로세스가 다시 시작됩니다.|일시 중단된 모든 프로세스가 다시 시작됩니다.|
|**디버그** > **한 단계씩 코드 실행**, **프로시저 단위 실행** 또는 **프로시저 나가기**|현재 프로세스가 단계별로 실행되는 동안 모든 프로세스가 실행됩니다. <br />그런 다음 모든 프로세스가 중단됩니다.|현재 프로세스가 단계별로 실행됩니다. <br />일시 중단된 프로세스가 다시 시작됩니다. <br />실행 중인 프로세스가 계속 실행됩니다.|
|**디버그** > **현재 프로세스 한 단계씩 코드 실행**, **현재 프로세스 프로시저 단위 실행** 또는 **현재 프로세스 프로시저 나가기**|N/A|현재 프로세스가 단계별로 실행됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|소스 창 **중단점**|모든 프로세스가 중단됩니다.|소스 창 프로세스만 중단됩니다.|
|소스 창 **커서까지 실행**<br />소스 창이 현재 프로세스에 있어야 합니다.|모든 프로세스가 소스 창 프로세스가 커서까지 실행되는 동안 실행되었다가 중단됩니다.<br />그런 다음 다른 모든 프로세스가 중단됩니다.|소스 창 프로세스가 커서까지 실행됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**프로세스** 창 > **프로세스 중단**|N/A|선택한 프로세스가 중단됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**프로세스** 창 > **프로세스 계속 진행**|N/A|선택한 프로세스가 다시 시작됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 소스 및 기호(.pdb) 파일 찾기
프로세스의 소스 코드를 탐색하려면 디버거가 해당 소스 파일과 기호 파일에 액세스할 수 있어야 합니다. 자세한 내용은 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

프로세스의 파일에 액세스할 수 없는 경우 **디스어셈블리** 창을 사용하여 탐색할 수 있습니다. 자세한 내용은 [방법: 디스어셈블리 창 사용](../debugger/how-to-use-the-disassembly-window.md)을 참조하세요.

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> 프로세스 간 전환

디버깅하는 동안 여러 프로세스에 연결할 수 있지만 한 번에 프로세스 하나만 디버거에서 활성화됩니다. **디버그 위치** 도구 모음이나 **프로세스** 창에서 활성 또는 *현재* 프로세스를 설정할 수 있습니다. 프로세스 간에 전환하려면 두 프로세스가 모두 중단 모드여야 합니다.

**디버그 위치 도구 모음에서 현재 프로세스를 설정하려면 다음을 수행합니다.**

1. **디버그 위치** 도구 모음을 열려면 **보기** > **도구 모음** > **디버그 위치**를 선택합니다.

1. 디버깅하는 동안 **디버그 위치** 도구 모음의 **프로세스** 드롭다운에서 현재 프로세스로 설정하려는 프로세스를 선택합니다.

   ![프로세스 간 전환](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**프로세스 창에서 현재 프로세스를 설정하려면 다음을 수행합니다.**

1. 디버깅 중에 **프로세스** 창을 열려면 **디버그** > **Windows** > **프로세스**를 선택합니다.

1. **프로세스** 창에서 현재 프로세스는 노란색 화살표로 표시됩니다. 현재 프로세스로 설정하려는 프로세스를 두 번 클릭합니다.

   ![프로세스 창](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

프로세스로 전환하면 디버깅을 위한 현재 프로세스로 설정됩니다. 디버거 창에는 현재 프로세스의 상태가 표시되며, 단계별 실행 명령은 현재 프로세스에만 영향을 줍니다.

## <a name="stop-debugging-with-multiple-processes"></a>여러 프로세스로 디버깅 중지

기본적으로 **디버그** > **디버깅 중지**를 선택하면 디버거가 종료되거나 모든 프로세스에서 분리됩니다.

- 현재 프로세스가 디버거에서 시작된 경우 프로세스가 종료됩니다.

- 디버거를 현재 프로세스에 연결한 경우 디버거는 프로세스에서 분리되며 프로세스는 계속 실행됩니다.

Visual Studio 솔루션에서 프로세스 디버깅을 시작한 후 이미 실행 중인 다른 프로세스에 연결한 다음, **디버깅 중지**를 선택하면 디버깅 세션이 종료됩니다. 연결된 프로세스가 계속 실행되는 동안 Visual Studio에서 시작된 프로세스가 종료됩니다.

**디버깅 중지**가 개별 프로세스에 영향을 주는 방식을 제어하려면 **프로세스** 창에서 프로세스를 마우스 오른쪽 단추로 클릭한 다음, **디버깅 중지 시 분리** 확인란을 선택하거나 선택 취소합니다.

>[!NOTE]
>**한 프로세스가 중단될 때 모든 프로세스 중단** 디버거 옵션은 프로세스 중지, 종료 또는 분리에 영향을 주지 않습니다.

### <a name="stop-terminate-and-detach-commands"></a>중지, 종료 및 분리 명령

다음 표에서는 여러 프로세스가 있는 디버거 중지, 종료 및 분리 명령의 동작에 대해 설명합니다.

|**Command**|**설명**|
|-|-|
|**디버그** > **디버깅 중지**|**프로세스** 창에서 동작이 변경되지 않는 한 디버거에서 시작된 프로세스가 종료되고 연결된 프로세스는 분리됩니다.|
|**디버그** > **모두 종료**|모든 프로세스가 종료됩니다.|
|**디버그** > **모두 분리**|디버거가 모든 프로세스에서 분리됩니다.|
|**프로세스** 창 > **프로세스 분리**|디버거가 선택된 프로세스에서 분리됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**프로세스** 창 > **프로세스 종료**|선택한 프로세스가 종료됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**프로세스** 창 > **디버깅 중지 시 분리**|선택한 경우 **디버그** > **디버깅 중지**가 선택한 프로세스에서 분리됩니다. <br />선택하지 않은 경우 **디버그** > **디버깅 중지**가 선택한 프로세스를 종료합니다. |

## <a name="see-also"></a>참조

- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)
- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)