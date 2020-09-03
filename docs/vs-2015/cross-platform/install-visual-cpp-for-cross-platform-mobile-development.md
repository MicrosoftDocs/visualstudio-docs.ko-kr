---
title: 플랫폼 간 모바일 개발용 Visual C++ 설치 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 70f1266581bb633086fa33a28b43e04befc7e6f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844323"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>플랫폼 간 모바일 개발용 Visual C++ 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

플랫폼 간 모바일 개발용 Visual C++](https://go.microsoft.com/fwlink/p/?LinkId=536383)는 Visual Studio 2015의 설치 가능한 구성 요소입니다. 플랫폼 간 Visual Studio 템플릿을 포함하며, 직접 찾아서 다운로드 및 구성하지 않고도 신속하게 시작할 수 있도록 플랫폼 간 도구 및 SDK를 설치합니다. Visual Studio에서 이러한 도구를 사용하여 플랫폼 간 프로젝트를 쉽게 만들고, 편집, 디버그 및 테스트할 수 있습니다. 이 항목에서는 Visual Studio를 사용하여 플랫폼 간 앱을 개발하는 데 필요한 도구 및 타사 소프트웨어를 설치하는 방법을 설명합니다. 구성 요소의 개요는 [Visual C++ 플랫폼 간 모바일](https://go.microsoft.com/fwlink/p/?LinkId=536387)을 참조하세요.  
  
 [사항이](#Requirements)   
 [도구 얻기](#GetTheTools)   
 [도구 설치](#InstallTheTools)   
 [IOS 용 도구 설치](#InstallForiOS)   
 [수동으로 종속성 설치 또는 업데이트](#ThirdParty)  
  
## <a name="requirements"></a><a name="Requirements"></a> 요구 사항  
  
- 설치 요구 사항은 [Visual Studio 2015 시스템 요구 사항](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs)을 참조하세요.  
  
  > [!IMPORTANT]
  > Windows 7 또는 Windows Server 2008 R2를 사용하는 경우 클래식 Windows 애플리케이션용 코드, Android Native Activity 앱 및 라이브러리, iOS용 앱 및 코드 라이브러리를 개발할 수 있지만 Windows 스토어 또는 유니버설 Windows 앱은 개발할 수 없습니다.  
  
  특정 디바이스 플랫폼용 앱을 빌드하려는 경우에는 다음의 몇 가지 요구 사항이 추가로 적용됩니다.  
  
- Windows Phone 에뮬레이터 및 Android용 Microsoft Visual Studio 에뮬레이터를 사용하려면 Hyper-V를 실행할 수 있는 컴퓨터가 필요합니다. 에뮬레이터를 설치하고 실행하려면 먼저 Windows에서 Hyper-V 기능을 사용하도록 설정해야 합니다. 자세한 내용은 에뮬레이터의 [시스템 요구 사항](https://msdn.microsoft.com/4d5bb438-231a-4cd2-84b7-e9660b0e3baf)을 참조하세요.  
  
- Android SDK와 함께 제공되는 x86 Android 에뮬레이터는 Intel HAXM 드라이버를 실행할 수 있는 컴퓨터에서 가장 잘 작동합니다. 이 드라이버를 사용하려면 VT-x 및 XD 비트(Execute Disable Bit)를 지원하는 Intel x64 프로세서가 필요합니다. 자세한 내용은 [Intel ® Hardware Accelerated Execution Manager 설치 지침 - Microsoft Windows](https://github.com/intel/haxm)(영문)를 참조하세요.  
  
- iOS용 코드를 빌드하려면 Apple ID, iOS 개발자 프로그램 계정 및 OS X Mavericks 이상 버전에서 [Xcode 6](https://go.microsoft.com/fwlink/p/?LinkId=536387) 이상을 실행할 수 있는 Mac 컴퓨터가 필요합니다. 자세한 설치 단계는 [Install tools for iOS](#InstallForiOS)를 참조하세요.  
  
## <a name="get-the-tools"></a><a name="GetTheTools"></a> 도구 얻기  
 플랫폼 간 모바일 개발용 Visual C++는 Visual Studio Community, Professional 및 Enterprise 버전에 포함된 설치 가능한 구성 요소입니다. Visual Studio를 다운로드하려면 [Visual Studio 2015 Downloads](https://visualstudio.microsoft.com/downloads/)(Visual Studio 2015 다운로드) 페이지로 이동하여 Visual Studio 2015 업데이트 2 이상을 다운로드하세요.  
  
## <a name="install-the-tools"></a><a name="InstallTheTools"></a> 도구 설치  
 Visual Studio 2015 설치 관리자에는 플랫폼 간 모바일 개발용 Visual C++를 설치하는 옵션이 포함되어 있습니다. 이 옵션은 Visual Studio에 필요한 C++ 언어 도구, 템플릿 및 구성 요소, Android 빌드 및 디버깅에 필요한 GCC 및 Clang 도구 집합 및 iOS 개발을 위해 Mac과 통신하기 위한 구성 요소를 설치합니다. 또한 iOS 및 Android 앱 개발을 지원하는 데 필요한 모든 타사 도구 및 소프트웨어 개발 키트를 설치합니다. 이러한 타사 도구는 대부분 Android 플랫폼 지원에 필요한 오픈 소스 소프트웨어입니다.  
  
- Android NDK(네이티브 개발 키트)는 Android 플랫폼을 대상으로 하는 C++ 코드를 빌드하는 데 필요합니다.  
  
- Android 빌드 프로세스를 수행하려면 Android SDK, Apache Ant 및 Java SE 개발 키트가 필요합니다.  
  
- Android용 Microsoft Visual Studio 에뮬레이터는 코드를 테스트 및 디버그하는 데 유용한 선택적 고성능 에뮬레이터입니다.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Visual C++ for Cross-Platform Mobile Development 및 타사 도구를 설치하려면  
  
1. [도구 다운로드](#GetTheTools)의 링크를 따라 다운로드한 Visual Studio 2015 설치 관리자를 실행합니다. 선택적 구성 요소를 설치하려면 **사용자 지정** 을 설치 유형으로 선택합니다. **다음** 을 선택하여 설치할 선택적 구성 요소를 선택합니다.  
  
2. 기능 선택에서 **플랫폼 간 모바일 개발** 을 확장 하 고 **Visual C++ 모바일 개발**을 선택 합니다.  
  
     ![Visual C&#43;&#43; 모바일 개발 선택](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     기본적으로 **Visual C++ 모바일 개발**을 선택하면 **프로그래밍 언어** 옵션은 **Visual C++** 를 설치하도록 설정되고 **일반 도구와 소프트웨어 개발 키트** 옵션은 필요한 타사 구성 요소를 설치하도록 설정됩니다. 필요한 경우 추가 구성 요소를 선택할 수 있습니다. 기본적으로 **Microsoft Visual Studio Emulator for Android**도 선택됩니다. 이미 설치된 구성 요소는 목록에서 비활성 상태로 표시됩니다.  
  
     유니버설 Windows 앱을 빌드하고 해당 앱과 Android 및 iOS 프로젝트 간에 코드를 공유하려면 **기능 선택**에서 **Windows 및 웹 개발**을 확장하고 **유니버설 Windows 앱 개발 도구**를 선택합니다. 유니버설 Windows 앱을 빌드하지 않으려는 경우에는 이 옵션을 건너뛸 수 있습니다.  
  
     **다음** 을 선택하여 계속 진행합니다.  
  
3. 타사 구성 요소에는 해당 사용 조건이 있습니다. 각 구성 요소 옆에 있는 **사용 조건** 링크를 선택하면 사용 조건을 볼 수 있습니다. **설치**를 선택하여 구성 요소를 추가하고 Visual Studio와 플랫폼 간 모바일 개발용 Visual C++를 설치합니다.  
  
4. 설치가 완료되면 설치 관리자를 닫고 컴퓨터를 다시 시작합니다. 타사 구성 요소에 대한 일부 설정 작업은 컴퓨터가 다시 시작된 다음에야 적용됩니다.  
  
    > [!IMPORTANT]
    > 모든 항목을 정상적으로 설치하려면 컴퓨터를 다시 시작해야 합니다.  
  
     Microsoft Visual Studio Emulator for Android 구성 요소가 설치되지 않으면 컴퓨터에서 Hyper-V가 사용하도록 설정되지 않았을 수 있습니다. **Windows 기능 사용/사용 안 함** 제어판 앱을 사용하여 Hyper-V를 사용하도록 설정한 다음 Visual Studio 설치 관리자를 다시 실행하세요.  
  
    > [!NOTE]
    > 사용 중인 컴퓨터 또는 Windows 버전에서 Hyper-V를 지원하지 않는 경우 Microsoft Visual Studio Emulator for Android 구성 요소를 사용할 수 없습니다. Windows Home Edition에는 Hyper-V 지원이 포함되지 않습니다.  
  
5. Visual Studio를 엽니다. 처음으로 Visual Studio를 실행하는 경우 구성 및 로그인하는 데 약간의 시간이 걸릴 수 있습니다. Visual Studio가 준비되면 **도구** 메뉴에서 **확장 및 업데이트**, **업데이트**를 차례로 선택합니다. 플랫폼 간 모바일 개발용 Visual C++ 또는 Android용 Microsoft Visual Studio 에뮬레이터에 사용할 수 있는 Visual Studio 업데이트가 있는 경우 설치합니다.  
  
## <a name="install-tools-for-ios"></a><a name="InstallForiOS"></a> IOS 용 도구 설치  
 플랫폼 간 모바일 개발용 Visual C++를 사용하여 iOS 코드를 편집 및 디버그하고 iOS 시뮬레이터 또는 iOS 디바이스에 배포할 수 있지만 라이선스 제한으로 인해 Mac에서 원격으로 코드를 빌드해야 합니다. Visual Studio를 사용하여 iOS 앱을 빌드 및 실행하려면 Mac에서 원격 에이전트를 설치 및 구성해야 합니다. 자세한 설치 지침, 필수 조건 및 구성 옵션은 [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조하세요. iOS용으로 빌드하지 않는 경우에는 이 단계를 건너뛸 수 있습니다.  
  
## <a name="install-or-update-dependencies-manually"></a><a name="ThirdParty"></a> 수동으로 종속성 설치 또는 업데이트  
 Visual C++ 모바일 개발 옵션을 설치할 때 Visual Studio 설치 관리자를 사용하여 타사 종속성을 하나 이상 설치하지 않는 경우 나중에 [Install the tools](#InstallTheTools)의 단계를 사용하여 설치할 수 있습니다. Visual Studio와 독립적으로 설치하거나 업데이트할 수도 있습니다.  
  
> [!CAUTION]
> Java를 제외한 종속성은 원하는 순서대로 설치할 수 있습니다. JDK는 Android SDK를 설치하기 전에 설치하고 구성해야 합니다.  
  
 다음 정보에 따라 아래 링크를 통해 종속성을 수동으로 설치할 수 있습니다.  
  
- [Java SE 개발 키트](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   기본적으로 설치 관리자는 Java 도구를 C:\Program Files (x86)\Java에 넣습니다.  
  
- [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
   설치 중에 권장 옵션으로 API를 업데이트합니다. 최소한 Android 5.0 Lollipop용 SDK(API 수준 21)를 설치해야 합니다. 기본적으로 설치 관리자는 Android SDK를 C:\Program Files (x86)\Android\android-sdk에 넣습니다.  
  
   Android SDK 디렉터리에서 SDK Manager 앱을 다시 실행하여 SDK를 업데이트하고 선택적 도구 및 추가 API 수준을 설치할 수 있습니다. **관리자 권한으로 실행** 을 사용하여 SDK Manager 앱을 실행하지 않으면 업데이트가 설치되지 않을 수도 있습니다. Android 앱을 빌드하는 데 문제가 있는 경우 SDK Manager에서 설치된 SDK에 대한 업데이트를 확인합니다.  
  
   Android SDK와 함께 제공되는 Android 에뮬레이터 중 일부를 사용하려면 선택적 Intel HAXM 드라이버를 설치해야 합니다. Intel HAXM 드라이버를 성공적으로 설치하려면 Windows에서 Hyper-V 기능을 제거해야 할 수 있습니다. Windows Phone 에뮬레이터 및 Android용 Microsoft Visual Studio 에뮬레이터를 사용하려면 Hyper-V 기능을 복원해야 합니다.  
  
- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   기본적으로 설치 관리자는 C:\ProgramData\Microsoft\AndroidNDK에 Android NDK를 저장합니다. Android NDK를 다시 다운로드 및 설치하여 NDK 설치를 업데이트할 수 있습니다.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   기본적으로 설치 관리자는 Apache Ant를 C:\Program Files (x86)\Microsoft Visual Studio 14.0\Apps에 넣습니다.  
  
- [Microsoft Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/)  
  
   Visual Studio 갤러리에서 Android용 Microsoft Visual Studio 에뮬레이터를 설치 및 업데이트할 수 있습니다.  
  
  대부분의 경우 Visual Studio는 설치된 타사 소프트웨어의 구성을 검색하고 내부 환경 변수에서 설치 경로를 유지 관리할 수 있습니다. Visual Studio IDE에서 이러한 플랫폼 간 개발 도구의 기본 경로를 재정의할 수 있습니다.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>타사 도구에 대한 경로를 설정하려면  
  
1. Visual Studio 메뉴 모음에서 **도구**, **옵션**을 차례로 선택합니다.  
  
2. **옵션** 대화 상자에서 **플랫폼 간**, **C++** 를 차례로 확장하고 **Android**를 선택합니다.  
  
     ![Android 도구 경로 옵션](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3. 도구에서 사용되는 경로를 변경하려면 경로 옆에 있는 확인란을 선택하고 텍스트 상자에서 폴더 경로를 편집합니다. 찾아보기 단추(**...**)를 사용하여 **위치 선택** 대화 상자를 열고 폴더를 선택할 수도 있습니다.  
  
4. **확인** 을 선택하여 사용자 지정 도구 폴더 위치를 저장합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IOS를 사용 하 여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [플랫폼 간 모바일 Visual C++](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)
