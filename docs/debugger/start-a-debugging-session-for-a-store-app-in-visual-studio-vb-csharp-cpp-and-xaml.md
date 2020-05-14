---
title: UWP 앱에 대한 디버깅 세션 시작 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: c4504dda362c8a50f33168a12839e894a14316d7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72436011"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>UWP 앱에 대한 디버깅 세션 시작

이 문서에서는 UWP(유니버설 Windows 플랫폼) 앱에 대한 Visual Studio 디버깅 세션을 시작하는 방법을 설명합니다. UWP 앱은 XAML 및 C++, XAML 및 C#/Visual Basic으로 쓸 수 있습니다. UWP 앱 디버깅을 시작하려면 디버깅 세션을 구성하고 앱을 시작하는 방법을 선택합니다.

::: moniker range=">=vs-2019"
> [!NOTE]
> Visual Studio 2019부터 HTML 및 JavaScript용 UWP 앱은 더 이상 지원되지 않습니다.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017에서 이 문서에 표시된 대부분의 명령과 옵션은 HTML 및 JavaScript용 UWP 앱에도 적용됩니다. 관리되는 앱과 C++ 앱의 명령이 다른 경우 JavaScript 앱은 일반적으로 C++ UWP 앱의 명령과 동일합니다.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Visual Studio 도구 모음에서 디버깅 시작

디버깅을 구성하고 시작하는 가장 쉬운 방법은 표준 Visual Studio 도구 모음입니다.

![도구 모음에서 디버그](../debugger/media/vsrun_select_target_device.png)

1. **표준** 도구 모음의 **구성** 드롭다운에서 **디버그**를 선택합니다.

1. **플랫폼** 드롭다운에서 빌드할 대상 플랫폼을 선택합니다.

1. 녹색 화살표 옆의 드롭다운에서 디버그 대상을 선택합니다. 로컬 컴퓨터, 직접 연결된 디바이스, 로컬 Visual Studio 시뮬레이터, 원격 디바이스 또는 에뮬레이터를 선택할 수 있습니다.

1. 디버깅을 시작하려면 도구 모음에서 녹색 **시작** 화살표를 선택하거나 **디버그** > **디버깅 시작**을 선택하거나 **F5**를 누릅니다.

   Visual Studio가 디버거가 연결된 응용 프로그램을 빌드하고 시작합니다.

중단점에 도달하거나 수동으로 디버깅을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> 배포/대상 옵션

Visual Studio 도구 모음 또는 프로젝트의 디버깅 속성 페이지에서 디버깅 대상을 설정할 수 있습니다. 다음 옵션 중 하나를 선택합니다.

|||
|-|-|
|**로컬 컴퓨터**|로컬 컴퓨터의 현재 세션에서 응용 프로그램을 디버깅합니다.|
|**시뮬레이터**|UWP 앱에 대한 Visual Studio 시뮬레이터에서 응용 프로그램을 디버깅합니다. 시뮬레이터는 로컬 컴퓨터에 없는 터치 제스처 및 디바이스 회전과 같은 디바이스 기능을 시뮬레이션하는 데스크톱 창입니다. 시뮬레이터 옵션은 앱의 **대상 플랫폼 최소 버전**이 로컬 컴퓨터의 운영 체제보다 작거나 같은 경우에만 사용할 수 있습니다. 자세한 내용은 [시뮬레이터에서 UWP 앱 실행](../debugger/run-windows-store-apps-in-the-simulator.md)을 참조하세요.|
|**원격 컴퓨터**|네트워크 또는 이더넷 케이블을 통해 로컬 컴퓨터에 연결된 디바이스에서 앱을 디버그합니다. Visual Studio용 원격 도구가 원격 디바이스에 설치되어 실행되고 있어야 합니다. 자세한 내용은 [원격 컴퓨터에서 UWP 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조하세요.|
|**디바이스**|USB로 연결된 디바이스에서 앱을 디버그합니다. 디바이스는 개발자 잠금과 화면 잠금이 해제되어 있어야 합니다.|
|**모바일 에뮬레이터**|에뮬레이터 이름에 지정된 에뮬레이터를 부팅하고, 앱을 배포하고, 디버깅을 시작합니다. 에뮬레이터는 Hyper-V를 사용하는 컴퓨터에서만 사용할 수 있습니다.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 프로젝트 속성 페이지에서 디버깅 구성

추가 디버깅 옵션을 구성하려면 프로젝트의 디버깅 속성 페이지를 사용합니다.

**디버깅 속성을 열려면:**

1. **솔루션 탐색기**에서 프로젝트를 선택한 다음 **속성** 아이콘을 선택하거나 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

1. **속성** 창의 왼쪽에서 다음을 수행합니다.

   - C# 및 Visual Basic 앱의 경우 **디버그**를 선택합니다.

     ![C# 및 Visual Basic 프로젝트 디버그 속성 페이지](../debugger/media/dbg_csvb_debugpropertypage.png)

   - C++ 앱의 경우 **구성 속성** > **디버깅**을 선택합니다.

     ![C++ UWP 앱 디버깅 속성 페이지](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> 사용할 디버거 선택

Visual Studio는 C# 및 Visual Basic 앱에서 기본적으로 관리 코드를 디버깅합니다. 다른 코드 형식이나 추가 코드 형식을 디버깅하도록 선택할 수 있습니다. 프로젝트에 포함된 모든 백그라운드 작업에 대해 **디버거 형식** 값을 설정할 수도 있습니다.

C++ 앱에서 Visual Studio는 기본적으로 네이티브 코드를 디버그합니다. 네이티브 코드 대신 또는 네이티브 코드 외에 특정 형식의 코드를 디버그하도록 선택할 수 있습니다.

**디버그할 코드 형식을 지정하려면:**

- C# 및 Visual Basic 앱의 경우 **디버그** 속성 페이지에 있는 **디버거 형식**의 **애플리케이션 형식** 및 **백그라운드 프로세스 형식** 드룹다운에서 다음 디버거 중 하나를 선택합니다.

- C++ 앱의 경우 **디버깅** 속성 페이지의 **디버거 형식** 드롭다운 목록에서 다음 디버거 중 하나를 선택합니다.

|||
|-|-|
|**관리 전용**|응용 프로그램에서 관리 코드를 디버깅합니다. JavaScript 코드와 네이티브 C/C++ 코드는 무시됩니다.|
|**네이티브 전용**|응용 프로그램에서 네이티브 C/C++ 코드를 디버깅합니다. 관리 코드와 JavaScript 코드는 무시됩니다.|
|**혼합(관리/네이티브)**|응용 프로그램에서 네이티브 C/C++ 코드 및 관리 코드를 디버깅합니다. JavaScript 코드는 무시됩니다. C++ 프로젝트에서 이 옵션을 **관리/네이티브**라고 합니다.|
|**스크립트**|응용 프로그램에서 JavaScript 코드를 디버깅합니다. 관리 코드와 네이티브 코드는 무시됩니다.|
|**스크립트가 포함된 네이티브**|앱에서 네이티브 C/C++ 코드 및 JavaScript 코드를 디버깅합니다. 관리 코드는 무시됩니다. C++ 프로젝트 또는 백그라운드 작업에서만 사용할 수 있습니다.|
|**GPU 전용(C++ AMP)**|GPU(그래픽 처리 장치)에서 실행되는 네이티브 C++ 코드를 디버깅합니다. C++ 프로젝트에서만 사용할 수 있습니다.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> 네트워크 루프백 비활성화(선택 사항)

 보안을 위해 일반적인 방식으로 설치된 UWP 앱은 앱이 설치된 디바이스에 대한 네트워크 호출을 수행할 수 없습니다. Visual Studio는 기본적으로 이 규칙에서 배포된 앱을 제외하므로 단일 컴퓨터에서 통신 프로시저를 테스트할 수 있습니다. 앱을 릴리스하기 전에 예외 없이 앱을 테스트해야 합니다.

**네트워크 루프백 예외를 제거하려면:**

- C# 및 Visual Basic 앱의 경우 **디버그** 속성 페이지의 **시작 옵션**에서 **로컬 네트워크 루프백 허용** 확인란의 선택을 취소합니다.

- C++ 앱의 경우 **디버깅** 속성 페이지의 **로컬 네트워크 루프백 허용** 드롭다운에서 **아니요**를 선택합니다.

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> 디버깅을 시작할 때 응용 프로그램 다시 설치(선택 사항)
 C# 또는 Visual Basic 앱의 설치 문제를 진단하려면 **디버그** 속성 페이지에서 **내 패키지 제거 후 다시 설치**를 선택합니다. 이 옵션은 디버깅을 시작할 때 원래 설치를 다시 만듭니다. C++ 프로젝트에는 이 옵션을 사용할 수 없습니다.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> 원격 디버깅에 대한 인증 옵션 설정

기본적으로 **원격 컴퓨터**를 배포 대상으로 선택할 때 원격 디버거를 실행하려면 Windows 자격 증명을 제공해야 합니다. 인증 요구를 변경할 수 있습니다.

**유니버설(암호화되지 않은 프로토콜)** 인증 모드는 IoT, Xbox, HoloLens 디바이스 및 크리에이터 업데이트 이상 Windows 10 PC용입니다.

**인증 방법을 변경하려면:**

- C# 및 Visual Basic 앱의 경우 **디버그** 속성 페이지에서 **대상 디바이스**로 **원격 컴퓨터**를 선택합니다. 그런 다음 **인증 모드**에 대해 **없음** 또는 **유니버설(암호화되지 않은 프로토콜)** 을 선택합니다.

- C++ 앱의 경우 **디버깅** 속성 페이지의 **실행할 디버거**에서 **원격 컴퓨터**를 선택합니다. 그런 다음 **인증 형식**에 대해 **인증 없음** 또는 **유니버설(암호화되지 않은 프로토콜)** 을 선택합니다.

> [!CAUTION]
> 원격 디버거를 **없음** 또는 **유니버설(암호화되지 않은 프로토콜)** 모드에서 실행하면 네트워크 보안이 없습니다. 악의적인 코드 또는 공격적인 트래픽 위험에 노출되지 않는 신뢰할 수 있는 네트워크에 대해서만 이러한 모드를 선택합니다.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> 디버깅 시작 옵션

**디버그** > **디버깅 시작**을 선택하거나 **F5**를 누르면 Visual Studio가 연결된 앱이 시작됩니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 디버깅을 시작하지만 앱 시작 지연

기본적으로 디버깅을 시작하면 Visual Studio가 앱을 즉시 시작합니다. 디버그 모드에서 실행되도록 앱을 설정할 수 있지만, 디버거 외부에서 앱을 시작할 수도 있습니다. 예를 들어 Windows **시작** 메뉴에서 앱 시작을 디버그하거나 앱에서 백그라운드 프로세스를 디버그할 수 있습니다. 이 옵션을 선택하면 시작 시 디버거에서 앱이 시작됩니다.

**자동 앱 시작을 사용하지 않도록 설정하려면:**

- C# 및 Visual Basic 앱의 경우 **디버그** 속성 페이지의 **시작 옵션**에서 **시작하지 않음(시작 시 코드 디버그)** 을 선택합니다.

- C++ 앱의 경우 **디버깅** 속성 페이지의 **애플리케이션 시작** 드롭다운에서 **아니요**를 선택합니다.

백그라운드 작업 디버깅에 대한 자세한 내용은 [UWP 앱에서 일시 중단, 다시 시작 및 백그라운드 이벤트 트리거](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)를 참조하세요.

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 설치되어 있거나 실행 중인 UWP 앱 디버그

**설치된 앱 패키지 디버그**를 사용하여 로컬 또는 원격 디바이스에 이미 설치되어 있거나 실행 중인 UWP 앱을 디버그할 수 있습니다. 앱이 Microsoft Store에서 설치되었거나 Visual Studio 프로젝트가 아닐 수 있습니다. 예를 들어 앱에 Visual Studio를 사용하지 않는 사용자 지정 빌드 시스템이 있을 수 있습니다.

설치된 앱을 즉시 시작하거나, 다른 방법으로 시작될 때 디버거에서 실행되도록 설정할 수 있습니다. 자세한 내용은 [UWP 앱에서 일시 중단, 다시 시작 및 백그라운드 이벤트 트리거](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)를 참조하세요.

디버거에 설치되어 있거나 실행 중인 UWP 앱을 시작하려면 **디버그** > **다른 디버그 대상** > **설치된 앱 패키지 디버그**를 선택합니다. 자세한 내용은 [설치된 앱 패키지 디버그](../debugger/debug-installed-app-package.md)를 참조하세요.

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 실행 중인 Windows 8.x 앱에 디버거 연결

[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 응용 프로그램에 디버거를 연결하려면 디버깅 가능 패키지 관리자를 사용하여 응용 프로그램이 디버그 모드에서 실행되도록 설정합니다. 디버깅 가능 패키지 관리자는 Visual Studio용 원격 도구와 함께 설치됩니다.

1. 앱이 설치된 디바이스에 Visual Studio용 원격 도구를 설치합니다. 자세한 내용은 [원격 도구 설치](../debugger/remote-debugging.md)를 참조하세요.

1. Windows **시작** 화면에서 **디버깅 가능 패키지 관리자**를 검색하고 시작합니다.

   AppxDebug cmdlet에 맞게 올바르게 구성된 PowerShell 창이 나타납니다.

1. 앱의 PackageFullName 식별자를 지정합니다.

   1. 모든 앱의 PackageFullName이 포함되어 있는 목록을 보려면 PowerShell 프롬프트에서 `Get-AppxPackage`를 입력합니다.

   1. PowerShell 프롬프트에서 `Enable-AppxDebug <PackageFullName>`을 입력합니다. 여기서 \<PackageFullName>은 앱의 PackageFullName 식별자입니다.

1. **디버그** > **프로세스에 연결**을 선택합니다.

1. **프로세스에 연결** 대화 상자에서 **연결 대상** 상자에 원격 디바이스를 지정합니다.

   디바이스 이름을 입력하고, **연결 대상** 상자의 드롭다운에서 선택하거나, **찾기**를 선택하여 **원격 연결** 대화 상자에서 디바이스를 찾을 수 있습니다.

1. 디버그할 코드 형식을 지정하려면 **연결 대상** 상자 옆에 있는 **선택**을 선택합니다.

1. **코드 형식 선택** 대화 상자에서 다음 중 하나를 선택합니다.
   - **디버깅할 코드 형식을 자동으로 결정**, 또는
   - **다음 코드 형식 디버그**를 선택한 다음 목록에서 하나 이상의 형식을 선택합니다.

1. **사용 가능한 프로세스** 목록에서 디버그할 앱 프로세스를 선택합니다.

1. **연결**을 선택합니다.

 프로세스에 디버거가 연결됩니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript 앱은 *wwahost.exe* 프로세스의 인스턴스에서 실행됩니다. JavaScript 앱이 두 개 이상 실행되는 경우 연결할 앱의 *wwahost.exe* 프로세스의 PID(숫자 프로세스 ID)를 알고 있어야 합니다.
>
> JavaScript 앱에 연결하는 가장 쉬운 방법은 다른 JavaScript 앱을 모두 닫는 것입니다. 또는 앱을 시작하기 전에 Windows 작업 관리자에서 *wwahost.exe* 프로세스를 실행하는 PID를 메모할 수 있습니다. 앱을 시작하면 해당 *wwahost.exe* PID가 이전에 메모한 것과 다릅니다.
::: moniker-end

## <a name="see-also"></a>참조

- [Visual Studio에서 앱 디버그](../debugger/debugging-windows-store-and-windows-universal-apps.md)