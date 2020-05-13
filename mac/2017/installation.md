---
title: Mac용 Visual Studio 2017 설치
description: Mac용 Visual Studio 및 플랫폼 간 개발에 필요한 추가 구성 요소를 설치하는 방법에 대한 지침입니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: dfc9f7469f5954aaac56b5d45bb5ae722110dfcc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984917"
---
# <a name="install-visual-studio-2017-for-mac"></a>Mac용 Visual Studio 2017 설치

> [!NOTE]
> Mac용 Visual Studio 2019는 [현재 사용 가능](installation.md?view=vsmac-2019)합니다. Mac용 Visual Studio의 이전 버전은 Visual Studio [다운로드 페이지](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)를 참조하세요.

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Mac용 Visual Studio 2019에서 다운그레이드할까요?

최상의 환경을 위해 다운그레이드하기 전에 Mac용 Visual Studio 2019를 [제거](uninstall.md)해야 합니다. 다운로드하게 하는 문제가 있는 경우 [문제를 보고](report-a-problem.md)하여 알려 주세요.
 
## <a name="requirements"></a>요구 사항

네이티브 플랫폼 간 앱 개발을 시작하려면 Mac용 Visual Studio를 다운로드할 때 설치 및 설정해야 하는 몇 가지 사항이 있습니다.

Visual Studio에서 iOS를 사용하는 경우 다음 사항이 필요합니다.

- macOS Sierra 10.12 이상이 설치된 Mac
- Xcode 9.3 이상. 대개 안정적인 최신 버전을 사용하는 것이 좋습니다.
- Apple ID. Apple ID가 없으면 https://appleid.apple.com 에서 새로 만들 수 있습니다. Xcode를 설치하고 서명하려면 Apple ID가 있어야 합니다.

## <a name="install"></a>설치

1. [visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)에서 Mac용 Visual Studio를 다운로드합니다.

2. 설치 관리자 패키지가 다운로드되면 **VisualStudioForMacInstaller.dmg** 파일을 클릭하여 설치 관리자를 탑재한 후, 다음 이미지와 같이 로고를 두 번 클릭하여 실행합니다.

   ![설치 관리자 대화 상자](media/installer-image1.png)

3. 다음 이미지와 비슷한 경고 대화 상자가 표시될 수도 있습니다. 이 경우 **열기**를 클릭합니다.

   ![경고 대화 상자](media/installer-image2.png)

4. 설치 관리자가 시스템을 검사하여 설치 또는 업데이트해야 하는 구성 요소를 확인합니다.

   ![시스템 평가](media/installer-image3.png)

5. 그런 다음 개인 정보 및 라이선스 조건에 동의하라는 경고 대화 상자가 표시됩니다. **계속** 단추를 눌러 조건에 동의합니다.

   ![라이선스 대화 상자](media/installer-image4.png)

6. 설치 관리자가 누락되어 다운로드 및 설치해야 하는 필수 구성 요소 목록을 표시합니다. 여기서 다운로드할 제품을 선택합니다.

   ![항목 선택](media/installer-image5.png)

   일부 플랫폼을 설치하지 않으려는 경우 아래 가이드를 사용하면 설치할 플랫폼을 결정할 수 있습니다.

   * **Xamarin을 사용하는 앱**:
      - Xamarin.Forms - **Android** 및 **iOS** 플랫폼을 선택합니다.
      - iOS에만 해당 - **iOS** 플랫폼을 선택합니다([**Xcode**](https://developer.apple.com/xcode/)를 설치해야 함).
      - Android에만 해당 - **Android** 플랫폼을 선택합니다(관련 종속성도 선택해야 함).
      - Mac에만 해당 - **macOS** 플랫폼을 선택합니다([**Xcode**](https://developer.apple.com/xcode/)를 설치해야 함).
      - 완벽한 플랫폼 간 Xamarin 앱 - **Android**, **iOS** 및 **macOS** 플랫폼을 선택합니다.
   * **.NET Core 애플리케이션** - **.NET Core** 플랫폼을 선택합니다.
   * **ASP.NET Core 웹 애플리케이션** - **.NET Core** 플랫폼을 선택합니다.
   * **플랫폼 간 Unity 게임 개발** - Mac용 Visual Studio 이외에는 추가 플랫폼을 설치하지 않아도 됩니다. Unity 확장 설치에 대한 자세한 내용은 [Unity 설치 가이드](/visualstudio/mac/setup-vsmac-tools-unity)를 참조하세요.

   이 설치 화면에는 각 개별 구성 요소의 버전 및 크기가 표시됩니다. 각 구성 요소를 클릭하여 해당 구성 요소에 대한 종속성 목록을 표시하거나(Android), 다운로드한 추가 패키지를 확인하거나(.NET Core), 필요한 추가 애플리케이션을 볼 수 있습니다(iOS 및 macOS).

   ![Android 추가 종속성](media/installer-image6.png)

7. 선택 항목에 만족할 경우 **설치 및 업데이트** 단추를 선택하여 설치 프로세스를 시작합니다.

8. 설치 관리자가 선택한 항목의 다운로드 및 설치 프로세스를 시작합니다.

   ![설치 시작](media/installer-image7.png)

   ![Xamarin.Mac 다운로드](media/installer-image8.png)

   ![설치 완료](media/installer-image9.png)

9. 설치를 완료하는 데 필요한 개별 구성 요소에 대한 필수 사용 권한을 상승하라는 메시지가 표시될 수 있습니다. 여기서 관리자 자격 증명을 입력하여 설치 프로세스를 계속합니다.

   ![사용 권한을 입력하여 설치 관리자 계속 진행](media/installer-image10.png)

10. 설치가 완료되면 **시작**을 눌러 Visual Studio에서 앱 개발을 시작할 수 있습니다.

    ![Visual Studio 열기](media/installer-image11.png)

> [!NOTE]
> 원래 설치 중 #6단계에서 선택 취소하여 플랫폼 또는 도구를 설치하지 않도록 선택한 경우 나중에 구성 요소를 추가하려면 [설치 관리자](https://visualstudio.microsoft.com/vs/)를 다시 실행해야 합니다.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>방화벽 또는 프록시 서버 뒤에 Mac용 Visual Studio 설치

방화벽 뒤에 있는 Mac용 Visual Studio를 설치하려면 소프트웨어에 필요한 도구 및 업데이트의 다운로드를 허용하기 위해 일부 엔드포인트에 액세스가 가능해야 합니다.

다음 위치에 액세스할 수 있도록 네트워크를 구성합니다.

- [Visual Studio 엔드포인트](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>다음 단계

Mac용 Visual Studio를 설치하면 앱 코드 작성을 시작할 수 있습니다. 다음 가이드에서는 프로젝트를 작성 및 배포하는 다음 단계를 안내합니다.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [디바이스 프로비저닝](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(디바이스에서 애플리케이션을 실행하려면).

### <a name="android"></a>Android

1. [Xamarin Android SDK Manager 사용](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK 에뮬레이터](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [개발용 디바이스 설정](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core 앱, ASP.NET Core 웹앱, Unity 게임 개발

다른 워크로드의 경우 [워크로드](/visualstudio/mac/workloads) 페이지를 참조하세요.

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>참고 항목

- [Visual Studio 2017 설치(Windows에서)](/visualstudio/install/install-visual-studio)
