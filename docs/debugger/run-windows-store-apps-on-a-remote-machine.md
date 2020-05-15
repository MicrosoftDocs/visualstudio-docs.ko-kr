---
title: 원격 컴퓨터의 UWP 앱 디버그 | Microsoft Docs
ms.date: 10/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 50d307cd65bfdf534b6ca3586e69bbc27be25e36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902886"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Visual Studio에서 원격 컴퓨터의 UWP 앱 디버그

Visual Studio를 사용하여 다른 컴퓨터 또는 디바이스에서 UWP(유니버설 Windows 플랫폼) 앱을 실행, 디버그, 프로파일링 및 테스트할 수 있습니다. Visual Studio 컴퓨터에서 터치, 지리적 위치 또는 물리적 방향 등의 UWP 관련 기능을 지원하지 않는 경우 원격 컴퓨터에서 UWP 앱을 실행하는 것이 특히 유용합니다.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> 필수 구성 요소

Visual Studio에서 원격 디바이스에 있는 UWP 앱을 디버깅하려면 다음을 수행합니다.

- 원격 디버깅을 위해 Visual Studio 프로젝트를 구성해야 합니다.
- 원격 컴퓨터와 Visual Studio 컴퓨터는 네트워크를 통해 연결되거나 USB 또는 이더넷 케이블을 통해 직접 연결되어야 합니다. 인터넷을 통한 디버깅은 지원되지 않습니다.
- Visual Studio 컴퓨터와 원격 컴퓨터 모두에서 [개발자 모드를 설정](/windows/uwp/get-started/enable-your-device-for-development)해야 합니다.
- 원격 컴퓨터에서 Visual Studio용 원격 도구를 실행해야 합니다.
  - 일부 Windows 10 버전은 원격 도구를 자동으로 시작하고 실행합니다. 그렇지 않으면 [Visual Studio용 원격 도구를 설치하고 실행합니다](#BKMK_download).
  - Windows Mobile 10 디바이스는 원격 도구를 요구하거나 지원하지 않습니다.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> 원격 디버깅을 위해 Visual Studio 프로젝트 구성하기
<a name="BKMK_DirectConnect"></a> 프로젝트 **속성**을 사용하여 연결할 원격 디바이스를 지정합니다. 설정은 프로그래밍 언어에 따라 달라집니다.

> [!CAUTION]
> 기본적으로 속성 페이지는 **유니버설(암호화 되지 않은 프로토콜)** 을 Windows 10 원격 연결에 대한 **인증 형식**으로 설정합니다. 원격 디버거에 연결하기 위해 **인증 안 함**을 설정해야 할 수도 있습니다. **유니버설(암호화 되지 않은 프로토콜)** 및 **인증 안 함** 프로토콜은 네트워크 보안이 없으므로 개발 및 원격 컴퓨터 간에 전달되는 데이터가 취약해집니다. 악의적이거나 공격적인 트래픽 위험에 노출되지 않는 신뢰할 수 있는 네트워크에 대해서만 이러한 인증 유형을 선택합니다.
>
>**인증 형식**으로 **Windows 인증**을 선택하는 경우 디버그할 때 원격 컴퓨터에 로그인해야 합니다. 또한 원격 디버거는 Visual Studio 컴퓨터와 동일한 사용자 계정을 사용하여 **Windows 인증** 모드에서 실행되어야 합니다.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> 원격 디버깅을 위한 C# 또는 Visual Basic 프로젝트 구성하기

1. Visual Studio **솔루션 탐색기**에서 C# 또는 Visual Basic 프로젝트를 선택하고 **속성** 아이콘을 선택하고, **Alt**+**Enter** 키를 누르거나 **속성**을 마우스 오른쪽 단추로 클릭하여 선택합니다.

1. **디버그** 탭을 선택합니다.

1. **대상 디바이스**에서 원격 컴퓨터에 대해 **원격 컴퓨터**를 선택하고 직접 연결된 Windows Mobile 10 디바이스에 대해 **디바이스**를 선택합니다.

1. 원격 컴퓨터의 경우 **원격 컴퓨터** 필드에 네트워크 이름 또는 IP 주소를 입력하거나 **원격 연결 대화 상자**에서 디바이스를 검색하려면 [검색](#remote-connections)을 선택합니다.

    ![원격 디버깅의 관리되는 프로젝트 속성](../debugger/media/vsrun_managed_projprop_remote.png "원격 디버깅의 관리되는 프로젝트 속성")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> 원격 디버깅을 위한 C++ 프로젝트 구성하기

1. Visual Studio **솔루션 탐색기**에서 C++ 프로젝트를 선택하고 **속성** 아이콘을 선택하고, **Alt**+**Enter** 키를 누르거나 **속성**을 마우스 오른쪽 단추로 클릭하여 선택합니다.

1. **디버깅** 탭을 선택합니다.

3. **실행할 디버거**에서 원격 컴퓨터에 대해 **원격 컴퓨터**를 선택하고 직접 연결된 Windows Mobile 10 디바이스에 대해 **디바이스**를 선택합니다.

1. 원격 컴퓨터의 경우 **컴퓨터 이름** 필드에 네트워크 이름 또는 IP 주소를 입력하거나 **원격 연결 대화 상자**에서 디바이스를 검색하려면 드롭다운에서 [찾기](#remote-connections)를 선택합니다.

    ![원격 디버깅의 C++ 프로젝트 속성](../debugger/media/vsrun_cpp_projprop_remote.png "원격 디버깅의 C++ 프로젝트 속성")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a>원격 연결 대화 상자 사용

**원격 연결** 대화 상자에서 특정 원격 컴퓨터 이름 또는 IP 주소를 검색하거나, 둥근 화살표 새로 고침 아이콘을 선택하여 연결을 자동으로 검색할 수 있습니다. 이 대화 상자는 로컬 서브넷에서 현재 원격 디버거를 실행 중인 디바이스만 검색합니다. **원격 연결** 대화 상자에서 모든 디바이스를 검색할 수 있는 것은 아닙니다.

 ![원격 연결 대화 상자](../debugger/media/vsrun_selectremotedebuggerdlg.png "원격 연결 대화 상자")

>[!TIP]
>이름으로 원격 디바이스에 연결할 수 없는 경우 IP 주소를 사용합니다. IP 주소를 확인하려면 원격 디바이스에서 명령 창에 **ipconfig**를 입력합니다. IP 주소는 **IPv4 주소**로 표시됩니다.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Visual Studio용 원격 도구 다운로드 및 설치

Visual Studio에서 원격 컴퓨터의 애플리케이션을 디버깅하려면 원격 컴퓨터에서 Visual Studio용 원격 도구를 실행해야 합니다.

- Windows Mobile 10 디바이스는 원격 도구를 요구하거나 지원하지 않습니다.
- 작성자의 업데이트(버전 1703) 이상, Windows 10 Xbox, IoT 및 HoloLens 디바이스를 실행하는 Windows 10 PC는 앱을 배포할 때 원격 도구를 자동으로 설치합니다.
- 이전 작성자 업데이트 Windows 10 PC에서는 디버깅을 시작하기 전에 원격 컴퓨터에서 원격 도구를 수동으로 다운로드하여 설치하고 실행해야 합니다.

**원격 도구 다운로드 및 설치:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a>원격 도구 구성

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> UWP 앱을 원격으로 디버그하기

원격 디버깅은 로컬 디버깅과 동일하게 작동합니다.

1. Windows 10 이전 작성자 업데이트 버전에서는 원격 디버깅 모니터(*msvsmon.exe*)가 원격 디바이스에서 실행되고 있어야 합니다.

1. Visual Studio 컴퓨터에서 도구 모음의 녹색 화살표 옆에 올바른 디버깅 대상(**원격 컴퓨터** 또는 **디바이스**)이 표시되는지 확인합니다.

1. **디버그** > **디버깅 시작**을 선택하고 **F5 키**를 누르거나, 도구 모음에서 녹색 화살표를 선택하여 디버깅을 시작합니다.

   그러면 프로젝트가 다시 컴파일된 후 원격 디바이스에서 배포되고 시작됩니다. 디버거는 중단점에서 실행을 일시 중단하며 사용자는 한 단계씩 코드를 실행하거나, 프로시저 단위로 실행하거나 코드를 종료하여 한 번에 한 줄씩 실행할 수 있습니다.

1. 필요한 경우 **디버그** > **디버깅 중지**를 선택하거나 하거나 **Shift**+**F5 키**를 눌러 디버깅을 중지하고 원격 애플리케이션을 닫습니다.

## <a name="see-also"></a>참조
- [고급 원격 배포 옵션](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Visual Studio로 UWP 앱 테스트](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [Visual Studio에서 UWP 앱 디버그](debugging-windows-store-and-windows-universal-apps.md)
