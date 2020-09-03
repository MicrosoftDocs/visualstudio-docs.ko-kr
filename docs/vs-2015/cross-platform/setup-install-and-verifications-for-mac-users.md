---
title: Mac 사용자용 설정, 설치 및 확인 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 5a3a05e50cfa17432bb2f31274c9b62c6b843687
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917956"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Mac 사용자용 설정, 설치 및 확인
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목은 Mac에서 주로 작업하고 Mac의 Windows 가상 머신 내부에서 선택적으로 Visual Studio를 사용하는 개발자를 위해 제공됩니다. 주로 Windows 컴퓨터에서 작업하는 개발자가 iOS를 대상으로 하도록 보조 Mac을 설정해야 하면 기본 [설정 및 설치](../cross-platform/setup-and-install.md) 항목을 참조하세요.  
  
 Mac에서 Xamarin을 사용하려면 다음이 필요합니다.  
  
- Xamarin 계정. 으로 이동 하 여 [https://www.xamarin.com/](https://www.xamarin.com/) 페이지의 오른쪽 위에서 **로그인** 을 클릭 한 다음 표시 되는 페이지에서 **새 계정 만들기** 를 클릭 합니다. Xamarin 계정에 사용할 전자 메일 주소와 암호를 선택합니다.  
  
- Xcode 7 및 Xamarin 4가 설치된 OSX Yosemite(10.10) 이상을 기반으로 둔 Mac.  
  
- 다음 구성의 하나:  
  
  - **Mac에서 직접 Xamarin Studio를 실행 하는 경우:** Xamarin Studio은 c #을 사용 하 여 Android, iOS 및 Windows 앱 빌드를 지 원하는 Xamarin 개발 환경입니다.  Xamarin Studio를 간단히 살펴보려면 [Xamarin Studio 개요](https://xamarin.com/studio) (영문)(xamarin.com)를 참조하세요.  
  
  - **Mac에 Parallels 또는 VMWare가 구성되어 있는 경우:** Parallels 또는 VMWare 내부에서 Visual Studio 2015 및 Xamarin 4가 설치된 Windows를 실행합니다.  이 구성을 사용하면 Xamarin은 Visual Studio와 함께 설치되고 C#을 사용하여 Android, iOS 및 WinPhone 앱을 빌드하는 데 Visual Studio를 개발 환경으로 사용하는 기능을 제공하는 확장입니다.  Visual Studio Developer Essentials 프로그램 일부로 무료 3개월 Parallels 구독을 구할 수 있습니다. [Microsoft Visual Studio Dev Essentials에는 도선 데스크톱 Pro 및 유사 항목 액세스](https://www.parallels.com/blogs/) (위 도선 블로그)가 포함 됩니다.  
  
  이 항목에서는 이러한 요구 사항에 대한 지침을 제공합니다.  설치 프로세스가 실행되는 동안 [Xamarin을 사용한 모바일 개발에 대해 알아보기](../cross-platform/learn-about-mobile-development-with-xamarin.md) 항목을 검토하여 필요한 배경 자료를 읽고 살펴볼 수 있습니다.  
  
  **항목 내용**  
  
- [Mac 설치(Apple ID, Xcode 및 Xamarin)](#mac)  
  
- [Windows 설치 (Visual Studio 및 Xamarin) 내부](#windows)  
  
- [환경 확인](#verify)  
  
## <a name="mac-setup-apple-id-xcode-and-xamarin"></a><a name="mac"></a> Mac 설치 (Apple ID, Xcode 및 Xamarin)  
  
1. Apple ID가 아직 없는 경우 [apple id](https://appleid.apple.com/) 에서 무료 apple id를 만듭니다. Xcode를 설치하고 서명하려면 이 작업이 필요합니다.  
  
2. 에서 Xcode를 다운로드 하 여 설치  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) 합니다.  
  
3. [Xamarin.iOS 설치 및 구성](/xamarin/ios/get-started/installation/mac) (영문)(xamarin.com)의 지침에 따라 Xamarin을 다운로드하여 설치합니다.  
  
4. Windows 및 Mac 컴퓨터에서 모두 Xamarin 설치를 완료 한 후에는 Windows 컴퓨터의 Visual Studio에서 iOS 및 Mac 작업을 수행할 수 있도록 [XMA를 사용 하 여 mac에 연결](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (xamarin.com)의 지침을 따르세요.  
  
## <a name="windows-setup-inside-parallels-visual-studio-and-xamarin"></a><a name="windows"></a> Parallels 내부의 Windows 설치(Visual Studio 및 Xamarin)  
  
1. Parallels/VMWare 내부에 구성한 Windows 데스크톱을 사용하여 [어떤 버전이든 Visual Studio 2015 설치 관리자를 다운로드하여 설치합니다](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional 또는 Enterprise). Visual Studio 2015 Community는 무료 버전이고, Professional 및 Enterprise 버전은 30일 평가판으로 사용할 수 있습니다.  
  
2. 설치 관리자 내에서 **사용자 지정** 설치를 선택합니다.  
  
     ![Visual Studio 설치에서 사용자 지정 옵션 선택](../cross-platform/media/cross-plat-xamarin-setup-1.png "크로스 Cross-plat Xamarin 설치 1")  
  
3. 다음 확인란을 선택하거나 선택을 취소합니다.  
  
    1. **플랫폼 간 모바일 개발 > C#/.NET(Xamarin)** 을 선택합니다. 그러면 일반 도구와 소프트웨어 개발 키트 아래에서 다양한 Android 도구가 자동으로 선택됩니다.  
  
         ![크로스&#45;플랫폼 모바일 개발 아래에서 Xamarin 옵션을 선택 합니다.](../cross-platform/media/cross-plat-xamarin-setup-2.png "크로스 Cross-plat Xamarin 설치 2")  
  
    2. **플랫폼 간 모바일 개발 > Microsoft Visual Studio Emulator for Android**를 선택 취소합니다.  
  
4. 설치 단추를 클릭하면 프로세스가 실행됩니다. 이 작업도 완료하는 데 약간 시간이 걸리므로 기다리는 동안 이 항목을 계속 진행하여 [Xamarin을 사용한 모바일 개발에 대해 알아보기](../cross-platform/learn-about-mobile-development-with-xamarin.md)를 살펴볼 수 있습니다.  
  
5. 설치가 완료되면 Visual Studio를 시작하고 메시지가 표시되면 Microsoft 계정으로 로그인합니다(Windows에서 사용하는 것과 같은 계정). 그리고 **도구 > 옵션 >Xamarin** 또는 **도구 > 옵션 Xamarin > 기타**에서 **지금 확인** 링크를 통해 Xamarin 업데이트를 확인합니다.  
  
     ![Visual Studio 옵션에서 Xamarin 업데이트 확인](../cross-platform/media/cross-plat-xamarin-setup-3.png "크로스 Cross-plat Xamarin 설치 3")  
  
    > [!NOTE]
    > 이전 Xamarin 라이선스 관련 문제를 방지하려면 Xamarin을 4.0.3.214 이상으로 업데이트해야 합니다.  업데이트를 확인하려고 하는데 Microsoft 빌드 도구에 대한 오류가 발생하면 [Xamarin 포럼](https://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015)의 스레드를 참조하세요.
  
6. Windows 및 Mac 컴퓨터에서 Xamarin 설치를 완료 한 후 [XMA를 사용 하 여 mac에 연결](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (xamarin.com)의 지침에 따라 Visual Studio에서 iOS로 작업할 수 있습니다.  
  
## <a name="verify-your-environment"></a><a name="verify"></a> 환경 확인  
 설치 관리자가 완료되면 잠시 Xamarin 개발을 경험할 모든 준비가 되었는지 확인하세요.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 먼저 제공된 링크로 이동할 때 Xamarin 설명서의 올바른 버전이 표시되도록 오른쪽 위에 **Xamarin Studio** 가 선택되었는지 확인합니다.  
  
 ![Xamarin.com에서 올바른 설명서를 보려면 Xamarin Studio 선택](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. [Android 프로젝트 만들기](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (xamarin.com)의 지침에 따라 android 프로젝트 만들기를 확인 합니다.  
  
2. [Android Player > Xamarin Studio 통합 설명서](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio)(xamarin.com)를 통해 Android Player의 디버깅 유효성을 검사합니다.  
  
   **iOS**  
  
3. [iOS 만들기](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (영문)(xamarin.com)의 지침에 따라 iOS 프로젝트 만들기를 확인합니다.  
  
4. [시뮬레이터의 디버깅 설명서](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (영문)(xamarin.com)를 통해 iOS 시뮬레이터의 디버깅을 확인합니다.  
  
### <a name="visual-studio"></a>Visual Studio  
 먼저 제공된 링크로 이동할 때 Xamarin 설명서의 올바른 버전이 표시되도록 오른쪽 위에 **Visual Studio** 가 선택되었는지 확인합니다.  
  
 ![Xamarin.com에서 올바른 설명서를 보려면 Visual Studio 선택](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 또한 **도구 > Xamarin 계정...** 을 통해 Xamarin 계정에 로그인합니다.  
  
 **Android**  
  
1. [Android 프로젝트 만들기](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (xamarin.com)의 지침에 따라 android 프로젝트 만들기를 확인 합니다.  
  
2. Android 디자이너 유효성 검사: 솔루션 탐색기의 Android 프로젝트에서**리소스 > 레이아웃 > Main.axml** 파일을 엽니다.  
  
   - "설치 된 Android SDK 너무 오래 되었습니다." 라는 오류가 표시 되 면 해당 메시지에서 **Android SDK 열기** 를 클릭 하 고 사용 가능한 최신 SDK 버전을 선택 합니다. SDK를 업데이트하려면 Visual Studio를 관리자로 실행하고 있어야 합니다.  
  
3. Visual Studio에서 Mac에 설치된 에뮬레이터로 연결할 수 있는지 확인합니다.  이의 결과로 Visual Studio 내에서 디버깅용으로 선택할 수 있는 에뮬레이터 목록에 Xamarin Player가 표시됩니다.  이 작업을 수행하려면 [Xamarin Android Player에 Visual Studio 연결](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (영문)(xamarin.com)의 지침을 따르세요.  
  
   **iOS**  
  
4. [XMA를 사용하여 Mac에 연결](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (영문)(xamarin.com)에 설명된 대로 Mac이 네트워크에서 사용 가능하고 Visual Studio와 연결되었는지 확인합니다.  
  
5. [iOS 만들기](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (영문)(xamarin.com)의 지침에 따라 iOS 프로젝트 만들기를 확인합니다.  
  
6. 스토리보드 디자이너 확인: 솔루션 탐색기의 iOS 프로젝트에서 **MainStoryboard.storyboard** 파일을 엽니다. 여기서 Visual Studio는 Mac에서 원격으로 실행 중인 디자이너를 호스트하고 있습니다.  
  
7. 빌드 및 디버깅 확인:  
  
   1. 솔루션 탐색기에서 iOS 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.  
  
   2. 아래와 같이 Visual Studio의 빌드 드롭다운에서 **드롭다운에서 iphonesimulator 대상을** 대상을 선택 합니다. 시뮬레이터가 나열되지 않으면 Mac에서 Xcode를 시작하고 **Xcode->기본 설정**을 선택한 후에 **다운로드**를 클릭합니다. **구성 요소** 에 다운로드할 수 있는 시뮬레이터 버전이 표시되어야 합니다. 디버깅에 대 한 추가 지침은 Xamarin의 [디버깅](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) 페이지 (xamarin.com)에서 찾을 수 있습니다.  
  
        ![IPhoneSimulator 빌드 대상 선택](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")  
  
   3. 아래 표시된 대로 Visual Studio의 디버그 드롭다운에서 iPhone 대상을 선택하고 F5 키를 눌러 디버거를 시작합니다. 그러면 앱을 조작할 Mac에서 시뮬레이터가 시작되고 동시에 Visual Studio에서 디버깅이 수행됩니다.  
  
        ![iPhone 디버그 대상 선택](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")
