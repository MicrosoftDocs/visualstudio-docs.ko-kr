---
title: 설치된 UWP 앱 패키지 디버그 | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d5c2e94e9fa80145489bddfb005b7136bdff8a71
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211296"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Visual Studio에서 설치된 UWP 앱 패키지 디버그

Visual Studio는 Windows 10 컴퓨터와 Xbox, HoloLens 및 IoT 디바이스에서 설치된 UWP(유니버설 Windows 플랫폼) 앱 패키지를 디버그할 수 있습니다.

>[!NOTE]
>휴대폰에서는 설치된 UWP 앱에 대한 Visual Studio 디버깅이 지원되지 않습니다.

UWP 앱을 디버그하는 방법에 대한 자세한 내용은 [설치된 앱 패키지 디버그](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) 및 [유니버설 Windows 앱(UWP) 빌드](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/)에 대한 블로그 게시물을 참조하세요.

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>로컬 머신에서 설치된 UWP 앱 디버그

1. Visual Studio에서 **디버그** > **기타 디버그 대상** > **설치된 앱 패키지 디버그**를 선택합니다.

1. **설치된 앱 패키지 디버그** 대화 상자의 **연결 형식**에서 **로컬 머신**을 선택합니다.

1. **설치된 앱 패키지**에서 디버그하려는 앱을 선택하거나 검색 상자에 해당 이름을 입력합니다. 실행되고 있지 않은 설치된 앱 패키지는 **실행 중이 아님**에, 실행 중인 앱은 **실행 중**에 표시됩니다.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. 필요한 경우 **다음 코드 형식 디버그**에서 코드 형식을 변경하고 기타 옵션을 선택합니다.
   - 앱이 시작될 때 디버깅을 시작하려면 **시작하지 않음(시작 시 코드 디버그)** 을 선택합니다. 애플리케이션을 시작할 때 디버깅을 시작하는 것은 [다른 시작 메서드](/windows/uwp/xbox-apps/automate-launching-uwp-apps)에서 제어 경로를 디버그(예: 사용자 지정 매개 변수를 사용한 프로토콜 활성화)하는 효과적인 방법입니다.

1. **시작**을 선택하거나, 앱이 실행 중인 경우 **연결**을 선택합니다.

> [!NOTE]
> Visual Studio에서 **디버그** > **프로세스에 연결**을 선택하여 실행 중인 UWP 또는 다른 앱 프로세스에 연결할 수도 있습니다. 원래 Visual Studio 프로젝트는 실행 중인 프로세스에 연결할 필요가 없지만, 앱의 기호를 로드하는 방법은 원래 코드가 없는 프로세스를 디버그할 때 상당히 유용합니다. [디버거에서 기호 파일 및 원본 파일 지정](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote">원격 컴퓨터 또는 디바이스에서 설치된 UWP 앱 디버그</a>

Visual Studio는 Windows 10 디바이스 또는 원격 사후 작성자 업데이트 Windows 10 컴퓨터에서 설치된 UWP 앱을 처음 디버그할 때 대상 디바이스에 원격 디버깅 도구를 설치합니다.

1. Visual Studio 컴퓨터와 원격 디바이스 또는 컴퓨터에서 [개발자 모드를 사용하도록 설정](/windows/uwp/get-started/enable-your-device-for-development)합니다.

1. 사전 작성자 업데이트 Windows 10을 실행하는 원격 컴퓨터에 연결하는 경우 원격 컴퓨터에 [원격 디버거를 수동으로 설치하고 시작](../debugger/remote-debugging.md)합니다.

1. Visual Studio 컴퓨터에서 **디버그** > **기타 디버그 대상** > **설치된 앱 패키지 디버그**를 선택합니다.

1. **설치된 앱 패키지 디버그** 대화 상자의 **연결 형식**에서 **원격 머신** 또는 **디바이스**를 선택합니다.

   **디바이스**를 선택하는 경우는 컴퓨터가 Windows 10 디바이스에 물리적으로 연결되어 있어야 합니다.

   원격 머신의 경우 컴퓨터 주소가 **주소** 옆에 표시되지 않으면 **변경**을 선택합니다.

   1. **원격 연결** 대화 상자의 **주소** 옆에 연결하려는 컴퓨터의 이름이나 IP 주소를 입력합니다.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      디버거가 컴퓨터 이름을 사용하여 원격 컴퓨터에 연결할 수 없는 경우에는 대신 IP 주소를 사용합니다. Xbox, HoloLens 또는 IoT 디바이스에 대한 IP 주소를 사용합니다.
   1. **인증 모드** 옆에 있는 인증 옵션을 선택합니다.

      대부분의 앱의 경우 기본값인 **유니버설(암호화되지 않은 프로토콜)** 을 유지합니다.
   1. **선택**을 선택합니다.

1. **설치된 앱 패키지**에서 디버그하려는 앱을 선택하거나 검색 상자에 해당 이름을 입력합니다. 실행되고 있지 않은 설치된 앱 패키지는 **실행 중이 아님**에, 실행 중인 앱은 **실행 중**에 표시됩니다.

1. 필요한 경우 **다음 코드 형식 디버그**에서 코드 형식을 변경하고 기타 옵션을 선택합니다.
   - 앱이 시작될 때 디버깅을 시작하려면 **시작하지 않음(시작 시 코드 디버그)** 을 선택합니다. 애플리케이션을 시작할 때 디버깅을 시작하는 것은 [다른 시작 메서드](/windows/uwp/xbox-apps/automate-launching-uwp-apps)에서 제어 경로를 디버그(예: 사용자 지정 매개 변수를 사용한 프로토콜 활성화)하는 효과적인 방법입니다.

1. **시작**을 선택하거나, 앱이 실행 중인 경우 **연결**을 선택합니다.

연결된 Xbox, HoloLens 또는 IoT 디바이스에서 설치된 앱 패키지를 처음 디버그하기 시작하면 Visual Studio에서는 대상 디바이스에 대한 올바른 버전의 원격 디버거를 설치합니다. 원격 디버거를 설치하는 데 시간이 걸릴 수 있으며 그동안 **원격 디버거를 시작하는 중입니다**라는 메시지가 표시됩니다.

>[!NOTE]
>현재 Xbox 또는 HoloLens 디바이스는 디버거가 연결된 앱이 아직 실행 중이 아닐 경우 앱을 다시 시작합니다.

UWP 앱의 원격 배포에 대한 자세한 내용은 [UWP 앱 배포 및 디버그](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) 및 [Debug UWP apps on remote machines](run-windows-store-apps-on-a-remote-machine.md)(원격 머신에서 UWP 앱 디버그)를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [원격 디버깅](../debugger/remote-debugging.md)
- [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)