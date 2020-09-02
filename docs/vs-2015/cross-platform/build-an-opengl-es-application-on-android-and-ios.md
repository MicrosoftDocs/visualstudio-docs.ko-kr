---
title: Android 및 iOS에서 OpenGL ES 애플리케이션 빌드 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b9f5db4ccd70136b711f5bd221244418cf843485
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151213"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Build an OpenGL ES Application on Android and iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

플랫폼 간 모바일 개발용 Visual C++ 옵션을 설치하는 경우 공통 코드를 공유하는 iOS 앱과 Android 앱에 대한 Visual Studio 솔루션 및 프로젝트를 만들 수 있습니다. 이 항목에서는 간단한 iOS 앱과 Android Native Activity 앱 둘 다를 만드는 솔루션 템플릿을 안내합니다. 앱에는 공통적으로 OpenGL ES를 사용하여 각 플랫폼에서 동일한 애니메이션 회전 큐브를 표시하는 C++ 코드가 있습니다. OpenGL ES(OpenGL for Embedded Systems 또는 GLES)는 다양한 모바일 디바이스에서 지원되는 2D 및 3D 그래픽 API입니다.  
  
 [사항이](#req)   
 [새 OpenGLES 응용 프로그램 프로젝트 만들기](#Create)   
 [Android 앱 빌드 및 실행](#BuildAndroid)   
 [IOS 앱 빌드 및 실행](#BuildIOS)   
 [앱 사용자 지정](#Customize)  
  
## <a name="requirements"></a><a name="req"></a> 요구 사항  
 iOS 및 Android용 OpenGL ES 앱을 개발하려면 먼저 모든 시스템 요구 사항을 충족했는지 확인해야 합니다. Visual Studio 2015의 플랫폼 간 모바일 개발용 Visual C++ 옵션을 설치해야 합니다. 필요한 타사 도구 및 SDK가 설치에 포함되어 있고 Android용 Visual Studio 에뮬레이터가 설치되어 있는지 확인합니다. 자세한 내용 및 자세한 지침은 [Install 플랫폼 간 모바일 개발용 Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)를 참조 하세요. iOS 앱을 빌드 및 테스트하려면 Mac 컴퓨터가 필요하며 설치 지침에 따라 설치해야 합니다. IOS 개발을 위해를 설정 하는 방법에 대 한 자세한 내용은 [ios를 사용 하 여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md) 을 참조 하세요.  
  
## <a name="create-a-new-opengles-application-project"></a><a name="Create"></a> 새 OpenGLES 응용 프로그램 프로젝트 만들기  
 이 자습서에서는 먼저 새 OpenGL ES 애플리케이션 프로젝트를 만든 후 Android용 Visual Studio 에뮬레이터에서 기본 앱을 빌드 및 실행합니다. 그런 다음 iOS용 앱을 빌드하고 iOS 시뮬레이터에서 앱을 실행합니다.  
  
#### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면  
  
1. Visual Studio를 엽니다. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.  
  
2. **새 프로젝트** 대화 상자의 **템플릿**에서 **Visual C++**, **플랫폼 간**을 차례로 선택한 후 **OpenGLES 애플리케이션(Android, iOS)** 템플릿을 선택합니다.  
  
3. 앱의 이름을 `MyOpenGLESApp`과 같이 지정한 후 **확인**을 선택합니다.  
  
    ![새 OpenGLES 애플리케이션 프로젝트](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    새 솔루션이 만들어지고 솔루션 탐색기가 열립니다.  
  
    ![솔루션 탐색기의 MyOpenGLESApp](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   새 OpenGL ES 애플리케이션 솔루션에 라이브러리 프로젝트 3개와 애플리케이션 프로젝트 2개가 포함됩니다. 라이브러리 폴더에는 공유 코드 프로젝트 1개와 공유 코드를 참조하는 플랫폼별 프로젝트 2개가 포함됩니다.  
  
- **MyOpenGLESApp.Android.NativeActivity** 에는 참조 및 Android에서 Native Activity로 앱을 구현하는 글루 코드가 포함됩니다. 글루 코드에서 진입점의 구현은 MyOpenGLESApp.Shared의 공용 공유 코드를 포함하는 main.cpp에 있습니다. 미리 컴파일된 헤더는 pch.h에 있습니다. 이 Native Activity 앱 프로젝트는 MyOpenGLESApp.Android.Packaging 프로젝트에서 선택된 공유 라이브러리(.so) 파일로 컴파일됩니다.  
  
- **MyOpenGLESApp.iOS.StaticLibrary** 는 MyOpenGLESApp.Shared의 공유 코드를 포함하는 iOS 정적 라이브러리(.a) 파일을 만듭니다. 이 파일은 MyOpenGLESApp.iOS.Application 프로젝트에서 만든 앱에 연결됩니다.  
  
- **MyOpenGLESApp.Shared** 에는 플랫폼 간에 작동하는 공유 코드가 포함됩니다. 플랫폼별 코드의 조건부 컴파일에 전처리기 매크로를 사용합니다. 공유 코드는 MyOpenGLESApp.Android.NativeActivity 및 MyOpenGLESApp.iOS.StaticLibrary 둘 다에서 프로젝트 참조에 의해 선택됩니다.  
  
  솔루션에는 Android 및 iOS 플랫폼용 앱을 빌드하는 두 프로젝트가 있습니다.  
  
- **MyOpenGLESApp.Android.Packaging** 은 Android 디바이스 또는 에뮬레이터에 배포하기 위한 .apk 파일을 만듭니다. 이 프로젝트에는 리소스와 매니페스트 속성을 설정하는 AndroidManifest.xml 파일이 포함되어 있습니다. Ant 빌드 프로세스를 제어하는 build.xml 파일도 포함되어 있습니다. 이 프로젝트는 기본적으로 시작 프로젝트로 설정되므로 Visual Studio에서 직접 배포 및 실행할 수 있습니다.  
  
- **MyOpenGLESApp.iOS.Application** 에는 MyOpenGLESApp.iOS.StaticLibrary의 C++ 정적 라이브러리 코드에 연결되는 iOS 앱을 개발하기 위한 리소스와 Objective-C 글루 코드가 포함됩니다. 이 프로젝트는 Visual Studio 및 원격 에이전트에서 Mac으로 전송되는 빌드 패키지를 만듭니다. 이 프로젝트를 빌드하면 Visual Studio가 Mac에서 앱을 빌드하고 배포하기 위한 파일과 명령을 보냅니다.  
  
## <a name="build-and-run-the-android-app"></a><a name="BuildAndroid"></a> Android 앱 빌드 및 실행  
 템플릿에서 만든 솔루션은 Android 앱을 기본 프로젝트로 설정합니다.  이 앱을 빌드 및 실행하여 설치 및 설정을 확인할 수 있습니다. 초기 테스트의 경우 Android용 Visual Studio 에뮬레이터에 의해 설치된 디바이스 프로필 중 하나에서 앱을 실행합니다. 다른 대상에서 앱을 테스트하려는 경우 대상 에뮬레이터를 로드하거나 디바이스를 컴퓨터에 연결할 수 있습니다.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Android Native Activity 앱을 빌드 및 실행하려면  
  
1. 아직 선택하지 않은 경우 **솔루션 플랫폼** 드롭다운 목록에서 **x86** 을 선택합니다.  
  
    ![솔루션 플랫폼을 x86으로 설정](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    x86을 사용하여 Windows용 Android 에뮬레이터를 대상으로 지정합니다. 디바이스를 대상으로 지정하는 경우 디바이스 프로세서에 따라 솔루션 플랫폼을 선택합니다. **솔루션 플랫폼** 목록이 표시 되지 않는 경우 **단추 추가/제거** 목록에서 **솔루션 플랫폼** 을 선택한 후 플랫폼을 선택 합니다.  
  
2. **솔루션 탐색기**에서 MyOpenGLESApp.Android.Packaging 프로젝트의 바로 가기 메뉴를 열고 **빌드**를 선택합니다.  
  
    ![Android 패키징 프로젝트 빌드](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    출력 창에 솔루션의 Android 공유 라이브러리 및 Android 앱에 대한 빌드 프로세스 출력이 표시됩니다.  
  
    ![Android 프로젝트용 출력 빌드](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. 배포 대상으로 VS 에뮬레이터 Android Phone(x86) 프로필 중 하나를 선택합니다.  
  
    ![배포 대상 선택](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    다른 에뮬레이터를 설치했거나 Android 디바이스를 연결한 경우 배포 대상 드롭다운 목록에서 선택할 수 있습니다. 앱을 실행하려면 빌드된 솔루션 플랫폼이 대상 디바이스의 플랫폼과 일치해야 합니다.  
  
4. F5 키를 눌러 디버깅을 시작하거나 Shift+F5를 눌러 디버깅하지 않고 시작합니다.  
  
    에뮬레이터가 시작됩니다. 코드를 로드하고 배포하는 데 몇 초 정도 걸릴 수 있습니다. 다음은 앱이 Android용 Visual Studio 에뮬레이터에 표시되는 방식입니다.  
  
    ![Android 에뮬레이터에서 실행 중인 앱](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    앱이 시작되면 중단점을 설정하고 디버거를 사용하여 코드를 단계별로 실행하고 지역을 검토하고 값을 조사할 수 있습니다.  
  
5. Shift+F5를 눌러 디버깅을 중지합니다.  
  
    에뮬레이터는 별도의 프로세스로 계속 실행됩니다. 코드를 편집 및 컴파일하여 동일한 에뮬레이터에 여러 번 배포할 수 있습니다. 앱이 에뮬레이터의 앱 컬렉션에 표시되고, 여기서 직접 시작할 수 있습니다.  
  
   생성된 Android Native Activity 앱 및 라이브러리 프로젝트는 Android 플랫폼과 인터페이스하기 위한 "글루" 코드를 포함하는 C++ 공유 코드를 동적 라이브러리에 배치합니다. 즉, 대부분의 앱 코드는 라이브러리에 있고 매니페스트, 리소스 및 빌드 지침은 패키징 프로젝트에 있습니다. 공유 코드는 NativeActivity 프로젝트의 main.cpp에서 호출됩니다. Android NativeActivity를 프로그래밍하는 방법에 대한 자세한 내용은 Android 개발자 NDK [개념](https://developer.android.com/ndk/guides/concepts.html) 페이지를 참조하세요.  
  
   Visual Studio는 Clang을 플랫폼 도구 집합으로 사용하는 Android NDK를 사용하여 Android Native Activity 프로젝트를 빌드합니다. Visual Studio는 NativeActivity 프로젝트의 속성을 대상 플랫폼에서 컴파일, 연결 및 디버그하는 데 사용되는 명령줄 스위치 및 옵션에 매핑합니다. 자세한 내용을 보려면 MyOpenGLESApp.Android.NativeActivity 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 명령줄 스위치에 대한 자세한 내용은 [Clang 컴파일러 사용자 설명서](http://clang.llvm.org/docs/UsersManual.html)를 참조하세요.  
  
## <a name="build-and-run-the-ios-app"></a><a name="BuildIOS"></a> IOS 앱 빌드 및 실행  
 iOS 앱 프로젝트는 Visual Studio에서 개발되고 편집되지만 라이선싱 제한 사항 때문에 Mac에서 빌드하고 배포해야 합니다. Visual Studio는 Mac에서 실행되는 원격 에이전트와 통신하여 프로젝트 파일을 전송하고 빌드, 배포 및 디버깅 명령을 실행합니다. iOS 앱을 빌드하려면 먼저 Mac 및 Visual Studio를 통신하도록 설정 및 구성해야 합니다. 자세한 지침은 [iOS를 사용 하 여 빌드할 도구 설치 및 구성을](../cross-platform/install-and-configure-tools-to-build-using-ios.md)참조 하세요. 원격 에이전트가 실행되고 Visual Studio가 Mac과 쌍으로 연결되면 iOS 앱을 빌드 및 실행하여 설치 및 설정을 확인할 수 있습니다.  
  
#### <a name="to-build-and-run-the-ios-app"></a>iOS 앱을 빌드하고 실행하려면  
  
1. 원격 에이전트가 Mac에서 실행되고 Visual Studio가 원격 에이전트와 쌍으로 연결되었는지 확인합니다. 원격 에이전트를 시작하려면 터미널 앱 창을 열고 `vcremote`를 참조하세요. 자세한 내용은 [Visual Studio에서 원격 에이전트 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS)을 참조하세요.  
  
    ![vcremote를 실행하는 Mac 터미널 창](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. 아직 선택하지 않은 경우 **솔루션 플랫폼** 드롭다운 목록에서 **x86** 을 선택합니다.  
  
    ![솔루션 플랫폼을 x86으로 설정](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    x86을 사용하여 iOS 시뮬레이터를 대상으로 지정합니다. iOS 디바이스를 대상으로 지정하는 경우 디바이스 프로세서(일반적으로 ARM 프로세서)에 따라 솔루션 플랫폼을 선택합니다. **솔루션 플랫폼** 목록이 표시 되지 않는 경우 **단추 추가/제거** 목록에서 **솔루션 플랫폼** 을 선택한 후 플랫폼을 선택 합니다.  
  
3. 솔루션 탐색기에서 MyOpenGLESApp.iOS.Application 프로젝트의 바로 가기 메뉴를 열고 **빌드**를 선택합니다.  
  
    ![iOS 애플리케이션 프로젝트 빌드](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    출력 창에 솔루션의 iOS 정적 라이브러리 및 iOS 앱에 대한 빌드 프로세스 출력이 표시됩니다. Mac에서 원격 에이전트를 실행하는 터미널 창에 명령 및 파일 전송 작업이 표시됩니다.  
  
    Mac 컴퓨터에 코드 서명 요청을 수락하라는 메시지가 표시될 수도 있습니다. 계속하려면 허용을 선택합니다.  
  
4. 도구 모음에서 **iOS 시뮬레이터** 를 선택하여 Mac의 iOS 시뮬레이터에서 앱을 실행합니다. 시뮬레이터를 시작하는 데 시간이 걸릴 수 있습니다. 출력을 보기 위해 Mac에서 시뮬레이터를 포그라운드로 전환해야 할 수도 있습니다.  
  
    ![iOS 시뮬레이터에서 실행 중인 앱](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    앱이 시작되면 중단점을 설정하고 Visual Studio 디버거를 사용하여 지역을 검사하고, 호출 스택을 확인하고, 값을 조사할 수 있습니다.  
  
    ![iOS 앱의 중단점에 있는 디버거](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. Shift+F5를 눌러 디버깅을 중지합니다.  
  
    iOS 시뮬레이터는 Mac에서 별도의 프로세스로 계속 실행됩니다. 코드를 편집 및 컴파일하여 동일한 iOS 시뮬레이터 인스턴스에 여러 번 배포할 수 있습니다. 배포된 후 시뮬레이터에서 직접 코드를 실행할 수도 있습니다.  
  
   생성된 iOS 앱 및 라이브러리 프로젝트는 공유 코드만 구현하는 C++ 코드를 정적 라이브러리에 넣습니다. 대부분의 애플리케이션 코드는 애플리케이션 프로젝트에 있습니다. 이 템플릿 프로젝트의 공유 라이브러리 코드 호출은 GameViewController.m 파일에서 수행됩니다. iOS 앱을 빌드하기 위해 Visual Studio는 Mac에서 실행되는 원격 클라이언트와 통신해야 하는 Xcode 플랫폼 도구 집합을 사용합니다.  
  
   Visual Studio는 프로젝트 파일을 전송하고 Xcode를 사용하여 앱을 빌드하는 명령을 원격 클라이언트에 보냅니다. 원격 클라이언트는 빌드 상태 정보를 Visual Studio로 다시 보냅니다. 앱이 성공적으로 빌드된 경우 Visual Studio를 사용하여 앱을 실행 및 디버그하는 명령을 보낼 수 있습니다. Visual Studio의 디버거는 Mac에서 실행되는 iOS 시뮬레이터 또는 연결된 iOS 디바이스에서 실행 중인 앱을 제어합니다. Visual Studio는 StaticLibrary 프로젝트의 속성을 대상 iOS 플랫폼에서 빌드, 연결 및 디버그하는 데 사용되는 명령줄 스위치 및 옵션에 매핑합니다. 컴파일러 명령줄 옵션에 대한 자세한 내용을 보려면 MyOpenGLESApp.iOS.StaticLibrary 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다.  
  
## <a name="customize-your-apps"></a><a name="Customize"></a> 앱 사용자 지정  
 공유 C++ 코드를 수정하여 공통 기능을 추가하거나 변경할 수 있습니다. MyOpenGLESApp.Android.NativeActivity 및 MyOpenGLESApp.iOS.Application 프로젝트에서 공유 코드 호출을 일치하도록 변경해야 합니다. 전처리기 매크로를 사용하여 공통 코드에서 플랫폼별 섹션을 지정할 수 있습니다. 전처리기 매크로 `__ANDROID__` 는 Android용으로 빌드할 때 미리 정의됩니다. 전처리기 매크로 `__APPLE__` 는 iOS용으로 빌드할 때 미리 정의됩니다.  
  
 특정 프로젝트 플랫폼에 대한 IntelliSense를 보려면 편집기 창의 위쪽 탐색 모음에 있는 컨텍스트 전환기 드롭다운에서 프로젝트를 선택합니다.  
  
 ![편집기의 프로젝트 컨텍스트 전환기 드롭다운](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 현재 프로젝트의 IntelliSense 문제는 빨간색 물결선으로 표시됩니다. 다른 프로젝트의 문제는 자주색 물결선으로 표시됩니다. 기본적으로 Visual Studio는 Java 또는 Objective-C 파일에 대해 코드 색 지정 또는 IntelliSense를 지원하지 않습니다. 그러나 여전히 원본 파일을 수정하고 리소스를 변경하여 애플리케이션 이름, 아이콘 및 기타 구현 세부 정보를 설정할 수 있습니다.
