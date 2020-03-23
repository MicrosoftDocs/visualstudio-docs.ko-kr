---
title: 여러 프로세스 디버그 | 마이크로 소프트 문서
ms.date: 11/20/2018
ms.topic: conceptual
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
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301184"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>여러 프로세스 디버그(C#, 비주얼 베이직, C++)

Visual Studio는 여러 프로세스가 있는 솔루션을 디버깅할 수 있습니다. 프로세스 사이를 시작하고 전환하고, 중단, 계속 및 소스를 단계별로 전환하고, 디버깅을 중지하고, 개별 프로세스에서 종료 또는 분리할 수 있습니다.

## <a name="start-debugging-with-multiple-processes"></a>여러 프로세스로 디버깅 시작

Visual Studio 솔루션에서 두 개 이상의 프로젝트를 독립적으로 실행할 수 있는 경우 디버거가 시작되는 프로젝트를 선택할 수 있습니다. 현재 시작 프로젝트는 솔루션 **탐색기에서**굵게 표시됩니다.

시작 프로젝트를 변경하려면 **솔루션 탐색기에서**다른 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정을**선택합니다.

시작 프로젝트를 만들지 않고 **솔루션 탐색기에서** 프로젝트 디버깅을 시작하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고**새 인스턴스** 시작 또는 **새 인스턴스로 단계** **제거를** > 선택합니다.

**솔루션 속성에서 시작 프로젝트 또는 여러 프로젝트를 설정하려면 다음을 수행합니다.**

1. **솔루션 탐색기에서** 솔루션을 선택한 다음 도구 모음에서 **속성** 아이콘을 선택하거나 솔루션을 마우스 오른쪽 단추로 클릭하고 **속성을**선택합니다.

1. **속성** 페이지에서 공통 **속성** > **시작 프로젝트를 선택합니다.**

   ![프로젝트의 시작 유형을 변경하는 중](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. **현재 선택,** **단일 시작 프로젝트** 및 프로젝트 파일 또는 여러 시작 **프로젝트를**선택합니다.

   **여러 시작 프로젝트를**선택하는 경우 각 프로젝트에 대해 수행할 시작 순서 및 **Start without debugging**작업을 변경할 수 **None** **있습니다.**

1. **적용**을 선택하거나 **확인을** 선택하여 대화 상자를 적용하고 닫습니다.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> 프로세스에 연결

디버거는 원격 장치를 포함하여 Visual Studio 외부의 프로세스에서 실행되는 앱에 *연결할* 수도 있습니다. 앱에 연결한 후 Visual Studio 디버거를 사용할 수 있습니다. 디버깅 기능이 제한될 수 있습니다. 앱이 디버그 정보로 빌드되었는지 여부, 앱의 소스 코드에 액세스할 수 있는지 여부 및 JIT 컴파일러가 디버그 정보를 추적하는지 여부에 따라 달라집니다.

자세한 내용은 [실행 중인 프로세스에 연결 을](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)참조하십시오.

**실행 중인 프로세스에 연결하려면:**

1. 앱을 실행중인 경우 > **프로세스에 대한** **디버그**연결 을 선택합니다.

   ![프로세스 대화 상자에 연결](../debugger/media/dbg_attachtoprocessdlg.png "프로세스에 연결 대화 상자")

1. **프로세스에 연결** 대화 상자에서 사용 가능한 **프로세스** 목록에서 프로세스를 선택한 다음 **연결 을**선택합니다.

>[!NOTE]
>자식 프로젝트가 동일한 솔루션에 있는 경우에도 디버거는 디버깅된 프로세스에서 시작되는 자식 프로세스에 자동으로 연결되지 않습니다. 자식 프로세스를 디버깅하려면 시작 후 자식 프로세스에 연결하거나 Windows 레지스트리 편집기를 구성하여 새 디버거 인스턴스에서 자식 프로세스를 시작하도록 구성합니다.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>레지스트리 편집기를 사용하여 디버거에서 프로세스를 자동으로 시작합니다.

경우에 따라 다른 프로세스에서 시작된 앱의 시작 코드를 디버깅해야 할 수 있습니다. 서비스 및 사용자 지정 설치 작업을 예로 들 수 있습니다. 디버거를 시작하고 앱에 자동으로 연결할 수 있습니다.

1. *regedit.exe를*실행하여 Windows 레지스트리 편집기를 시작합니다.

1. 레지스트리 편집기에서 **HKEY_LOCAL_MACHINE\소프트웨어\Microsoft\Windows NT\currentVersion\이미지 파일 실행 옵션으로 이동합니다.**

1. 디버거에서 시작할 응용 프로그램의 폴더를 선택합니다.

   앱이 하위 폴더로 나열되지 않은 경우 **이미지 파일 실행 옵션을**마우스 오른쪽 단추로 클릭하고 **새** > **키를**선택하고 앱 이름을 입력합니다. 또는 트리에서 새 키를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기를**선택한 다음 앱 이름을 입력합니다.

1. 트리에서 새 키를 마우스 오른쪽 단추로 클릭하고 **새** > **문자열 값을**선택합니다.

1. 새 값의 이름을 **새 값** #1 `debugger`에서 로 변경합니다.

1. **디버거를** 마우스 오른쪽 단추로 클릭하고 **에서 수정을**선택합니다.

   ![문자열 편집 대화 상자](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "문자열 편집 대화 상자")

1. 문자열 **편집** 대화 상자에서 값 `vsjitdebugger.exe` **데이터** 상자를 입력한 다음 **확인을**선택합니다.

   ![regedit.exe의 자동 디버거 시작 항목](../debugger/media/dbg_execution_automaticstart_result.png "regedit.exe의 자동 디버거 시작 항목")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>여러 프로세스로 디버그
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

여러 프로세스로 앱을 디버깅할 때 중단, 단계 별 및 계속 디버거 명령은 기본적으로 모든 프로세스에 영향을 미칩니다. 예를 들어 중단점에서 프로세스가 일시 중단되면 다른 모든 프로세스의 실행도 일시 중단됩니다. 이 기본 동작을 변경하여 실행 명령의 대상을 더욱 세부적으로 제어할 수 있습니다.

**한 프로세스가 중단될 때 모든 프로세스가 일시 중단되는지 여부를 변경하려면 다음을 수행합니다.**

- **도구(또는** **디버그)**> **옵션** > **디버깅** > **일반에서**한 프로세스가 중단될 **때 모든 프로세스 를** 선택하거나 지웁니다.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> 명령 중단, 단계별 실행 및 계속 실행

다음 표는 하나의 프로세스가 중단확인란을 선택하거나 선택 해제할 **때 Break 모든 프로세스가** 선택될 때 디버깅 명령의 동작에 대해 설명합니다.

|**명령**|선택|선택 취소됨|
|-|-|-|
|**디버그**  > **브레이크 모두**|모든 프로세스가 중단됩니다.|모든 프로세스가 중단됩니다.|
|**디버그** > **계속**|모든 프로세스가 다시 시작됩니다.|일시 중단된 모든 프로세스가 다시 시작됩니다.|
|**단계 디버그,** > **Step Into** **단계별**또는 **단계별**|현재 프로세스가 단계별로 실행되는 동안 모든 프로세스가 실행됩니다. <br />그런 다음 모든 프로세스가 중단됩니다.|현재 프로세스가 단계별로 실행됩니다. <br />일시 중단된 프로세스가 다시 시작됩니다. <br />실행 중인 프로세스가 계속 실행됩니다.|
|**Debug** > **현재 프로세스로 단계**디버그, **현재 프로세스단계 단계**또는 현재 프로세스 **단계**|해당 없음|현재 프로세스가 단계별로 실행됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|소스 창 **중단점**|모든 프로세스가 중단됩니다.|소스 창 프로세스만 중단됩니다.|
|소스 창 **커서에 실행**<br />소스 창이 현재 프로세스에 있어야 합니다.|모든 프로세스가 소스 창 프로세스가 커서까지 실행되는 동안 실행되었다가 중단됩니다.<br />그런 다음 다른 모든 프로세스가 중단됩니다.|소스 창 프로세스가 커서까지 실행됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**프로세스** 창 > **프로세스**|해당 없음|선택한 프로세스가 중단됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**프로세스** > **프로세스 계속**|해당 없음|선택한 프로세스가 다시 시작됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 소스 및 기호(.pdb) 파일 찾기
프로세스의 소스 코드를 탐색하려면 디버거가 소스 파일 및 기호 파일에 액세스해야 합니다. 자세한 내용은 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

프로세스의 파일에 액세스할 수 없는 경우 **디스어셈블리 제거** 창을 사용하여 탐색할 수 있습니다. 자세한 내용은 [사용 방법: 분해 창 사용을](../debugger/how-to-use-the-disassembly-window.md)참조하십시오.

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> 프로세스 간 전환

디버깅할 때 여러 프로세스에 연결할 수 있지만 지정된 시간에 디버거에서 하나의 프로세스만 활성화됩니다. **디버그 위치** 도구 모음이나 **프로세스** 창에서 활성 또는 *현재* 프로세스를 설정할 수 있습니다. 프로세스 간에 전환하려면 두 프로세스가 모두 중단 모드여야 합니다.

**위치 디버그 도구 모음에서 현재 프로세스를 설정하려면 다음을 수행합니다.**

1. **위치 디버그** 도구 모음을 열려면**도구 모음** > **디버그 위치** **보기를** > 선택합니다.

1. 디버깅 중에 **디버그 위치** 도구 모음에서 **프로세스** 드롭다운에서 현재 프로세스로 설정할 프로세스를 선택합니다.

   ![프로세스 간 전환](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**프로세스 창에서 현재 프로세스를 설정하려면 다음을 수행합니다.**

1. 디버깅하는 동안 **프로세스** 창을 열려면**Windows** > **프로세스** **디버그를** > 선택합니다.

1. **프로세스** 창에서 현재 프로세스는 노란색 화살표로 표시됩니다. 현재 프로세스로 설정하려는 프로세스를 두 번 클릭합니다.

   ![프로세스 창](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

프로세스로 전환하면 디버깅을 위해 현재 프로세스로 설정됩니다. 디버거 창은 현재 프로세스의 상태를 표시하고 스테핑 명령은 현재 프로세스에만 영향을 미칩니다.

## <a name="stop-debugging-with-multiple-processes"></a>여러 프로세스로 디버깅 중지

기본적으로 **디버그** > **중지 디버깅을**선택하면 디버거가 모든 프로세스에서 종료되거나 분리됩니다.

- 디버거에서 현재 프로세스가 시작된 경우 프로세스가 종료됩니다.

- 디버거를 현재 프로세스에 연결한 경우 디버거는 프로세스에서 분리되며 프로세스는 계속 실행됩니다.

Visual Studio 솔루션에서 프로세스디버깅을 시작하면 이미 실행 중인 다른 프로세스에 연결한 다음 **디버깅 중지를**선택하여 디버깅 세션이 종료됩니다. Visual Studio에서 시작된 프로세스는 종료되고 연결한 프로세스는 계속 실행됩니다.

**디버깅 중지가** 개별 프로세스에 영향을 주는 방법을 제어하려면 **프로세스** 창에서 프로세스를 마우스 오른쪽 단추로 클릭한 다음 **디버깅 중지확인란에서 Detach를** 선택하거나 지웁니다.

>[!NOTE]
>하나의 프로세스가 디버거 옵션을 **중단할 때 모든 프로세스 나누기는** 프로세스의 중지, 종료 또는 분리에 영향을 주지 않습니다.

### <a name="stop-terminate-and-detach-commands"></a>중지, 종료 및 분리 명령

다음 표에서는 여러 프로세스를 통해 디버거 중지, 종료 및 분리 명령의 동작에 대해 설명합니다.

|**명령**|**설명**|
|-|-|
|**디버그** > **중지 디버깅**|**프로세스** 창에서 동작이 변경되지 않으면 디버거에서 시작한 프로세스가 종료되고 연결된 프로세스가 분리됩니다.|
|**모두 종료 디버그** > **Terminate All**|모든 프로세스가 종료됩니다.|
|**디버그** > **분리 모두**|디버거가 모든 프로세스에서 분리됩니다.|
|**분리** **프로세스>** 프로세스 창|디버거가 선택된 프로세스에서 분리됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**프로세스** 종료 > **프로세스** 창|선택한 프로세스가 종료됩니다.<br />다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|
|**디버깅이 중지될 때** **처리** 창 > 분리|이 옵션을 선택하면 **디버그** > **중지가** 선택한 프로세스에서 분리됩니다. <br />이 옵션을 선택하지 않으면 **디버그** > **중지 디버깅이** 선택한 프로세스를 종료합니다. |

## <a name="see-also"></a>참고 항목

- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)
- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)