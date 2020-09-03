---
title: '스토어 앱에 대 한 디버깅 세션 시작 (VB, c #, c + + 및 XAML) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd0a89ac1d96e2d1af829ba04e6e164f8fae7f8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542183"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Visual Studio에서 스토어 앱의 디버깅 세션 시작(VB, C#, C++ 및 XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 및 Windows Phone]에 적용 됩니다. /Image/windows_and_phone_content.png "windows_and_phone_content")

 이 항목에서는 XAML과 Visual C++, Visual C# 또는 Visual Basic으로 작성된 스토어 앱에서 디버깅 세션을 시작하는 방법을 설명합니다. 응용 프로그램 디버깅에는 디버깅 세션 구성과 응용 프로그램 시작 방법 선택이 모두 포함됩니다.

> [!NOTE]
> JavaScript 및 HTML로 작성 된 앱의 경우 [디버그 세션 시작 (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)을 참조 하세요.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용
 [디버깅을 쉽게 시작하는 방법](#BKMK_The_easy_way_to_start_debugging)

 [디버깅 세션 구성](#BKMK_Configure_the_debugging_session)

- [프로젝트에 대 한 디버깅 속성 페이지 열기](#BKMK_Open_the_debugging_property_page_for_the_project)

- [빌드 구성 옵션 선택](#BKMK_Choose_the_build_configuration_options)

- [배포 대상 선택](#BKMK_Choose_the_deployment_target)

- [사용할 디버거 선택](#BKMK_Choose_the_debugger_to_use)

- [(선택 사항) 디버그 세션 시작 지연](#BKMK__Optional__Delay_starting_the_debug_session)

- [필드 Network 루프백 비활성화 사용 안 함](#BKMK__Optional__Disable_network_loopbacks)

- [(선택 사항) 디버깅을 시작할 때 응용 프로그램 다시 설치](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [(선택 사항) 원격 디버거 시작을 위한 인증 요구 비활성화](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [디버깅 세션을 시작 합니다.](#BKMK_Start_the_debugging_session)

- [디버깅 시작(F5)](#BKMK_Start_debugging__F5_)

- [디버깅을 시작하되F5) 응용 프로그램 시작 지연](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [디버거에서 설치 된 앱 시작](#BKMK_Start_an_installed_app_in_the_debugger)

- [실행 중인 앱에 디버거 연결](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [응용 프로그램이 디버그 모드에서 실행 되도록 설정](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [디버거 연결](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a> 디버깅을 쉽게 시작 하는 방법

1. Visual Studio에서 응용 프로그램 솔루션을 엽니다.

2. F5 키를 선택합니다.

   Visual Studio가 디버거가 연결된 응용 프로그램을 빌드하고 시작합니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다. 자세한 내용은 [디버그 세션 탐색 (Xaml 및 c #)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) 을 참조 하세요.

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a> 디버깅 세션 구성

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 프로젝트에 대한 디버깅 속성 페이지 열기

1. 솔루션 탐색기에서 프로젝트를 선택합니다. 바로 가기 메뉴에서 **속성**을 선택합니다.

2. 다음 작업을 수행하여 프로젝트에 대한 디버그 속성 페이지를 엽니다.

    - Visual C# 및 Visual Basic 응용 프로그램의 경우 **디버그**를 선택합니다.

         ![C&#35; &#47; VB 프로젝트 디버그 속성 페이지](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - Visual C++ 응용 프로그램의 경우 **구성 속성**  노드를 확장한 다음 **디버깅**을 선택합니다.

         ![C&#43;&#43; Windows 스토어 앱 디버깅 속성 페이지](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a> 빌드 구성 옵션 선택

1. **구성** 목록에서 **Debug** 또는 **(활성)Debug**를 선택합니다.

2. **플랫폼** 목록에서 빌드할 대상 플랫폼을 선택합니다. 대부분의 경우 **Any CPU** (Visual C++에서는**All Platforms** )를 선택하는 것이 가장 좋습니다.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a> 배포 대상 선택
 ![Windows에만 적용](../debugger/media/windows-only-content.png "windows_only_content")

 Visual Studio 컴퓨터, 로컬 컴퓨터의 Visual Studio 시뮬레이터 또는 원격 디바이스에서 Windows 스토어 앱을 배포하고 디버깅할 수 있습니다.

- C# 및 Visual Basic 응용 프로그램의 경우 프로젝트에 대한 **디버그** 속성 페이지의 **대상 디바이스** 목록에서 대상을 선택합니다.

- C++ 응용 프로그램의 경우 **디버깅** 속성 페이지의 **실행할 디버거** 목록에서 대상을 선택합니다.

  다음 옵션 중 하나를 선택합니다.

|옵션|설명|
|-|-|
|**로컬 컴퓨터**|로컬 컴퓨터의 현재 세션에서 응용 프로그램을 디버깅합니다. [로컬 컴퓨터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-the-local-machine.md)을 참조 하세요.|
|**시뮬레이터**|[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱에 대한 Visual Studio 시뮬레이터에서 응용 프로그램을 디버깅합니다. 시뮬레이터는 로컬 컴퓨터에서 사용할 수 없는 터치 제스처 및 디바이스 회전과 같은 디바이스 기능을 디버깅할 수 있도록 하는 데스크톱 창입니다. [시뮬레이터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-in-the-simulator.md)을 참조 하세요.|
|**원격 머신**|인트라넷을 통해 로컬 컴퓨터에 연결되거나 이더넷 케이블을 사용하여 직접 연결된 디바이스에서 응용 프로그램을 디버깅합니다. 원격으로 디버깅하려면 Visual Studio 원격 도구가 원격 디바이스에 설치되어 실행되고 있어야 합니다. [원격 컴퓨터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조 하세요.|

 **원격 컴퓨터**를 선택하는 경우 다음 방법 중 하나를 사용하여 원격 컴퓨터의 이름 또는 IP 주소를 지정합니다.

- 원격 컴퓨터의 이름 또는 IP 주소를 입력합니다.

  - C# 및 Visual Basic 응용 프로그램의 경우 **원격 컴퓨터** 상자에 이름 또는 IP 주소를 입력합니다.

  - C++ 응용 프로그램의 경우 **컴퓨터 이름** 상자에 이름 또는 IP 주소를 입력합니다.

- **원격 디버거 연결 선택** 대화 상자에서 원격 컴퓨터를 선택합니다.

   이 대화 상자를 열려면 다음을 수행합니다.

  - C# 및 Visual Basic 응용 프로그램의 경우 **찾기**를 선택합니다.

  - C + + 앱의 경우 **컴퓨터 이름** 상자에서 아래쪽 화살표를 선택 하 고를 선택 **\<Locate...>** 합니다.

    ![원격 디버거 연결 선택 대화 상자](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > **원격 디버거 연결 선택** 대화 상자에는 로컬 서브넷에 있는 컴퓨터와 이더넷 케이블을 통해 Visual Studio 컴퓨터에 직접 연결되어 있는 컴퓨터가 표시됩니다. 다른 컴퓨터를 지정하려면 **컴퓨터 이름** 상자에 이름을 입력합니다.

  ![Windows Phone에만 적용](../debugger/media/phone-only-content.png "phone_only_content")

  디바이스 또는 Visual Studio 휴대폰 에뮬레이터 중 하나에서 Windows Phone 스토어 앱을 배포하고 디버깅할 수 있습니다. **대상 디바이스** 목록에서 디바이스 또는 에뮬레이터를 선택합니다.

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> 사용할 디버거 선택
 기본적으로 Visual Studio는 C# 및 Visual Basic 응용 프로그램에서 관리 코드를 디버깅합니다.

 C# 및 Visual Basic 응용 프로그램의 경우 응용 프로그램에서 관리 코드 및 네이티브 C/C++ 코드를 디버깅하도록 선택할 수 있습니다. **비관리 코드 디버깅 사용** 확인란을 선택하면 디버그 세션에 네이티브 코드가 포함됩니다.

 기본적으로 C++ 응용 프로그램에서는 네이티브 코드가 디버깅됩니다.

 C++ 앱의 경우 그 대신 사용자 앱 구성 요소에 있는 특정 형식의 코드를 디버깅하거나, 네이티브 코드와 함께 이와 같은 특정 형식의 코드를 디버깅하도록 선택할 수 있습니다. 응용 프로그램 프로젝트의 **디버깅** 속성 페이지에 있는 **디버거 형식** 목록에서 디버깅할 코드를 지정합니다.

 **애플리케이션 프로세스** 목록에서 아래 디버거 중 하나를 선택합니다.

|디버거 형식|설명|
|-|-|
|**스크립트만**|응용 프로그램에서 JavaScript 코드를 디버깅합니다. 관리 코드와 네이티브 코드는 무시됩니다.|
|**네이티브 전용**|응용 프로그램에서 네이티브 C/C++ 코드를 디버깅합니다. 관리 코드와 JavaScript 코드는 무시됩니다.|
|**관리 전용**|응용 프로그램에서 관리 코드를 디버깅합니다. JavaScript 코드와 네이티브 C/C++ 코드는 무시됩니다.|
|**혼합(관리/네이티브)**|응용 프로그램에서 네이티브 C/C++ 코드 및 관리 코드를 디버깅합니다. JavaScript 코드는 무시됩니다.|
|**GPU 전용**|GPU(그래픽 처리 장치)에서 실행되는 네이티브 C++ 코드를 디버깅합니다.|

 ![Windows Phone에만 적용](../debugger/media/phone-only-content.png "phone_only_content")

 Windows 스토어 Phone 앱의 경우 **백그라운드 작업 프로세스**에서 백그라운드 프로세스에 사용할 디버거를 선택할 수 있습니다.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a> 필드 디버그 세션 시작 지연
 기본적으로 디버깅을 시작하면 바로 응용 프로그램이 시작됩니다. 디버그 세션을 시작하되 응용 프로그램 시작을 지연할 수도 있습니다. 이 옵션을 선택하는 경우 시작 화면 또는 활성화 계약을 통해 응용 프로그램이 시작되거나 다른 프로세스 또는 메서드를 통해 응용 프로그램이 시작되면 디버거에서 응용 프로그램이 시작됩니다. 응용 프로그램 자체가 실행되지 않는 경우 백그라운드 작업을 디버깅하려면 응용 프로그램의 시작을 지연할 수도 있습니다.

 다음 작업을 통해 응용 프로그램 시작을 지연할 수 있습니다.

- Visual C# 및 Visual Basic 응용 프로그램의 경우 **디버그** 속성 페이지에서 **시작하지 않음(시작 시 코드 디버그)** 을 선택합니다.

- Visual C++ 애플리케이션의 경우 **디버깅** 속성 페이지의 **애플리케이션 시작** 목록에서 **예** 를 선택합니다.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> (선택 사항) 네트워크 루프백 비활성화
 ![Windows에만 적용](../debugger/media/windows-only-content.png "windows_only_content")

 보안상의 이유로 일반적인 방식으로 설치된 Windows 스토어 앱은 앱이 설치된 디바이스에 대한 네트워크 호출을 수행할 수 없습니다. 기본적으로 Visual Studio를 배포하면 배포된 응용 프로그램에 대한 이 규칙의 예외가 만들어 집니다. 이 예외로 인해 사용자는 단일 컴퓨터에서 통신 프로시저를 테스트할 수 있습니다. 응용 프로그램을 Windows 스토어에 제출하기 전에 이 예외 없이 응용 프로그램을 테스트해야 합니다.

 네트워크 루프백 예외를 제거하려면

- Visual C# 및 Visual Basic 응용 프로그램의 경우 **디버그** 속성 페이지에서 **네트워크 루프백 허용** 확인란을 선택 취소합니다.

- Visual C++ 응용 프로그램의 경우 **디버깅** 속성 페이지의 **네트워크 루프백 허용** 목록에서 **아니요** 를 선택합니다.

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> 필드 디버깅을 시작할 때 응용 프로그램 다시 설치
 Visual C# 또는 Visual Basic 응용 프로그램의 설치 및 초기 구성에서 문제를 진단하려면 **디버그** 속성 페이지에서 **패키지 제거 후 다시 설치**  를 선택하여 디버깅을 시작할 때 원래 설치를 다시 만듭니다. 이 옵션은 Visual C++ 프로젝트에는 사용할 수 없습니다.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> 필드 원격 디버거 시작을 위한 인증 요구 비활성화
 ![Windows에만 적용](../debugger/media/windows-only-content.png "windows_only_content")

 기본적으로 원격 디버거를 시작하려면 자격 증명을 제공해야 합니다.

> [!IMPORTANT]
> 인증 안 함 모드에서 원격 디버거를 실행하도록 선택할 수 있지만 이 모드는 사용하지 않는 것이 좋습니다. 이 모드에서 실행할 때는 네트워크 보안이 없습니다. 네트워크에 악의적인 트래픽이나 유해 트래픽 위험이 확실히 없는 경우에만 인증 안 함 모드를 선택하십시오.

 인증 요구를 제거하려면

1. Visual C# 및 Visual Basic 응용 프로그램의 경우 **디버그** 속성 페이지에서 **인증 사용** 확인란을 선택 취소합니다.

2. Visual C++ 응용 프로그램의 경우 **디버깅** 속성 페이지의 **인증 필요** 목록에서 **아니요** 를 선택합니다.

   [항목 내용](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a> 디버깅 세션을 시작합니다.

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a> 디버깅 시작 (F5)
 **디버그** 메뉴에서 **디버깅 시작** (키보드: F5)을 선택 하면 Visual Studio에서 디버거가 연결 된 앱을 시작 합니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 디버깅을 시작 하 되 (F5) 앱 시작 지연
 디버그 모드에서 실행되도록 응용 프로그램을 설정할 수 있지만 디버거가 아닌 방법으로 응용 프로그램을 시작할 수 있습니다. 예를 들어 시작 메뉴에서 응용 프로그램 시작을 디버깅하거나 응용 프로그램을 시작하지 않고 응용 프로그램에서 백그라운드 프로세스를 디버깅할 수 있습니다. 응용 프로그램 시작을 지연하려면 다음을 수행합니다.

- 응용 프로그램의 **디버깅** 속성 페이지(Visual C++에서는**디버그** )에서

  - Visual C# 및 Visual Basic 응용 프로그램의 경우 **시작하지 않음(시작 시 코드 디버그)** 을 선택합니다.

  - Visual C++ 애플리케이션의 경우 **애플리케이션 시작** 목록에서 **예** 를 선택합니다.

- **디버그** 메뉴에서 **디버깅 시작** (키보드: F5)을 선택 합니다.

- 시작 메뉴, 실행 계약 또는 다른 프로시저를 통해 응용 프로그램을 시작합니다.

  디버그 모드에서 응용 프로그램이 시작됩니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

  . 백그라운드 작업을 디버깅 하는 방법에 대 한 자세한 내용은 [Windows 스토어에 대 한 일시 중단, 다시 시작 및 백그라운드 이벤트 트리거](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)를 참조 하세요.

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 디버거에서 설치된 응용 프로그램 시작
 F5 키를 사용하여 디버깅을 시작할 때 Visual Studio에서는 응용 프로그램을 빌드 및 배포하고 디버그 모드에서 실행되도록 응용 프로그램을 설정한 다음 응용 프로그램을 시작합니다. 디바이스에 이미 설치된 응용 프로그램을 시작하려면 설치된 응용 프로그램 패키지 디버그 대화 상자를 사용합니다. 이 절차는 Windows 스토어에서 설치된 응용 프로그램을 디버깅해야 하는 경우나 응용 프로그램의 소스 파일은 있지만 응용 프로그램에 대한 Visual Studio 프로젝트가 없는 경우에 유용합니다. 예를 들어 Visual Studio 프로젝트 또는 솔루션을 사용하지 않는 사용자 지정 빌드 시스템이 있을 수 있습니다.

 응용 프로그램은 로컬 디바이스에 설치되거나 원격 디바이스에 있을 수 있습니다.  응용 프로그램을 즉시 시작하거나 시작 메뉴나 활성화 계약 등의 다른 프로세스나 방법으로 시작될 때 디버거에서 실행되도록 응용 프로그램을 설정할 수 있습니다. 응용 프로그램을 시작하지 않고 백그라운드 프로세스를 디버깅하려는 경우에도 디버그 모드에서 실행되도록 응용 프로그램을 설정할 수 있습니다. 자세한 내용은 [Windows 스토어에 대 한 일시 중단, 다시 시작 및 백그라운드 이벤트 트리거](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)를 참조 하세요.

 디버그 모드에서 실행되도록 설치된 응용 프로그램을 설정하려면 다음을 수행합니다.

> [!NOTE]
> 이 절차를 시작할 때 응용 프로그램이 실행되고 있지 않아야 합니다.

1. **디버그** 메뉴에서 **디버그 Installed App Package**를 선택합니다.

2. 목록에서 다음 옵션 중 하나를 선택합니다.

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **로컬 컴퓨터**  |                                                                                                                로컬 컴퓨터의 현재 세션에서 응용 프로그램을 디버깅합니다. [로컬 컴퓨터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-the-local-machine.md)을 참조 하세요.                                                                                                                 |
   |   **시뮬레이터**    | [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱에 대한 Visual Studio 시뮬레이터에서 응용 프로그램을 디버깅합니다. 시뮬레이터는 로컬 컴퓨터에서 사용할 수 없는 터치 제스처 및 디바이스 회전과 같은 디바이스 기능을 디버깅할 수 있도록 하는 데스크톱 창입니다. [시뮬레이터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-in-the-simulator.md)을 참조 하세요. |
   | **원격 머신** |                          인트라넷을 통해 로컬 컴퓨터에 연결되거나 이더넷 케이블을 사용하여 직접 연결된 디바이스에서 응용 프로그램을 디버깅합니다. 원격으로 디버깅하려면 Visual Studio 원격 도구가 원격 디바이스에 설치되어 실행되고 있어야 합니다. [원격 컴퓨터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조 하세요.                           |

3. **설치된 응용 프로그램 패키지** 목록에서 응용 프로그램을 선택합니다.

4. **다음 코드 형식 디버깅** 목록에서 사용할 디버그 엔진을 선택합니다.

5. (선택 사항) 다른 방법으로 시작될 때 응용 프로그램을 디버깅하거나 백그라운드 프로세스를 디버깅하려면 **시작하지 않음(시작 시 코드 디버그)** 을 선택합니다.

   **시작**을 클릭하면 응용 프로그램이 시작되거나 디버그 모드에서 실행되도록 설정됩니다.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 실행 중인 응용 프로그램에 디버거 연결
 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 응용 프로그램에 디버거를 연결하려면 디버깅 가능 패키지 관리자를 사용하여 응용 프로그램이 디버그 모드에서 실행되도록 설정합니다. 디버깅 가능 패키지 관리자는 Visual Studio 원격 도구와 함께 설치됩니다.

 응용 프로그램에 디버거를 연결하는 기능은 [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]에서 설치된 응용 프로그램과 같은 이미 설치된 응용 프로그램을 디버깅해야 하는 경우 유용합니다. 응용 프로그램의 소스 파일은 있지만 응용 프로그램에 대한 Visual Studio 프로젝트가 없는 경우 연결해야 합니다. 예를 들어 Visual Studio 프로젝트 또는 솔루션을 사용하지 않는 사용자 지정 빌드 시스템이 있을 수 있습니다.

 응용 프로그램에 디버거를 연결하려면 아래와 같은 단계를 수행해야 합니다.

1. 응용 프로그램이 디버그 모드에서 실행되도록 설정합니다. 이 작업은 응용 프로그램이 실행되고 있지 않을 때 수행해야 합니다.

2. 앱을 시작합니다. 시작 화면, 실행 계약 또는 다른 메서드를 통해 응용 프로그램을 시작할 수 있습니다.

3. 실행 중인 응용 프로그램에 디버거 연결합니다.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> 응용 프로그램이 디버그 모드에서 실행되도록 설정

1. 응용 프로그램이 설치된 디바이스에 Visual Studio 원격 도구를 설치합니다. [원격 도구 설치](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools)를 참조하세요.

2. 시작 화면에서 `Debuggable Package Manager` 를 검색한 다음 시작합니다.

     AppxDebug cmdlet에 맞게 올바르게 구성된 PowerShell 창이 나타납니다.

3. 응용 프로그램의 디버깅을 사용하도록 설정하려면 응용 프로그램의 PackageFullName 식별자를 지정해야 합니다. PackageFullName이 포함되어 있는 모든 응용 프로그램의 목록을 보려면 PowerShell 프롬프트에서 `Get-AppxPackage` 를 입력합니다.

4. PowerShell 프롬프트에서 `Enable-AppxDebug` *PackageFullName* 을 입력합니다. 여기서 *PackageFullName* 은 앱의 PackageFullName 식별자입니다.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a> 디버거 연결
 디버거를 연결하려면 다음을 수행합니다.

1. **디버그** 메뉴에서 **프로세스에 연결**을 선택합니다.

    **프로세스에 연결** 대화 상자가 나타납니다.

2. 원격 디바이스의 응용 프로그램에 연결하려면 **한정자** 상자에 원격 디바이스를 지정합니다. 다음과 같습니다.

   - **한정자** 상자에 이름을 입력합니다.

   - **한정자** 상자에서 아래쪽 화살표를 선택한 다음 앞에서 연결한 디바이스의 목록에서 디바이스를 선택합니다.

   - **찾기** 를 선택하여 로컬 서브넷의 디바이스 목록에서 디바이스를 선택합니다.

3. **연결 대상** 상자에서 디버깅할 코드의 형식을 지정합니다.

    **선택** 을 선택한 후 다음 중 하나를 수행합니다.

   - **디버깅할 코드 형식을 자동으로 결정**을 선택합니다.

   - **다음 코드 형식 디버깅** 을 선택한 다음 목록에서 하나 이상의 형식을 선택합니다.

4. **사용 가능한 프로세스**  목록에서 응용 프로그램 프로세스를 선택합니다.

5. **연결**을 선택합니다.

   프로세스에 디버거가 연결됩니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

   [항목 내용](#BKMK_In_this_topic)

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 앱 디버그](../debugger/debug-store-apps-in-visual-studio.md) [디버그 세션 탐색 (Xaml 및 c #)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
