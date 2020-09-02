---
title: 플랫폼 간 모바일 개발
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1efc8ea7f40c3098e681cc80ac90789b629630a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312758"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio에서 플랫폼 간 모바일 개발
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio를 사용하여 Android, iOS 및 Windows 디바이스용 앱을 빌드할 수 있습니다.  앱을 디자인할 때 Visual Studio의 도구를 사용하여 Office 365, Azure App Service 및 Application Insights와 같은 연결된 서비스를 쉽게 추가할 수 있습니다.

 C# 및 .NET Framework, HTML 및 JavaScript 또는 C++를 사용하여 앱을 빌드합니다. 코드, 문자열, 이미지 및 경우에 따라 사용자 인터페이스도 공유합니다.

 게임 또는 몰입형 그래픽 앱을 빌드하려는 경우 Visual Studio Tools for Unity를 설치하여 iOS, Android, Windows 및 기타 플랫폼에서 실행되는 앱을 위한 인기 있는 플랫폼 간 게임/그래픽 엔진 및 개발 환경인 Unity와 함께 Visual Studio의 모든 강력한 생산성 기능을 이용하세요.

 **문서 내용:**

- [Android, iOS 및 Windows용 앱 빌드(.NET Framework)](#NET)

  - [단일 코드 베이스에서 Android, iOS 및 Windows를 대상으로 합니다.](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Windows 10 장치를 대상으로 합니다.](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Android, iOS 및 Windows 용 앱 빌드 (HTML/JavaScript)](#HTML)

- [Android 및 Windows용 앱 빌드(C++)](#CPP)

- [Visual Studio Tools for Unity를 사용하여 Android, iOS 및 Windows용 플랫폼 간 게임 빌드](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a> Android, iOS 및 Windows 용 앱 빌드 (.NET Framework)
 ![디바이스](../cross-platform/media/homedevices.png "HomeDevices")

 Xamarin을 사용하면 동일한 솔루션 및 공유 코드는 물론 UI에서도 Android, iOS 및 Windows를 대상으로 지정할 수 있습니다.

|**자세히**|
|--------------------|
|[Visual Studio 설치](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Visual Studio의 Xamarin에 대해 알아보기](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio 및 Xamarin](../cross-platform/visual-studio-and-xamarin.md)(MSDN 라이브러리)|
|[ALM(Application Lifecycle Management) 및 Xamarin 앱](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md)(MSDN 라이브러리)|
|[Visual Studio의 유니버설 Windows 앱에 대해 알아보기](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift와 C# 간의 유사점에 대해 알아보기](https://aka.ms/scposter) (download.microsoft.com)|
|[Android 용 Visual Studio 에뮬레이터에 대해 알아보기](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> 단일 코드 베이스에서 Android, iOS 및 Windows를 대상으로 지정
 C# 또는 F#(Visual Basic은 현재 지원되지 않음)을 사용하여 Android, iOS 및 Windows용 네이티브 앱을 빌드할 수 있습니다.  시작하려면 Visual Studio 2015를 설치하여 설치 관리자에서 **사용자 지정** 옵션을 선택하고 **플랫폼 간 모바일 개발 > C#/.NET(Xamarin)** 아래 확인란을 선택합니다. Visual Studio 2013용 Xamarin을 설치하는 데 필요한 [Xamarin 설치 관리자](https://www.xamarin.com/download)로도 시작할 수 있습니다.

 Visual Studio 2015가 이미 설치되어 있는 경우 **제어판 > 프로그램 및 기능**에서 설치 관리자를 실행한 후 Xamarin에 대해 위와 동일한 **사용자 지정** 옵션을 선택합니다.

 완료 되 면 프로젝트 템플릿이 **새 프로젝트** 대화 상자에 표시 됩니다. Xamarin 템플릿을 가장 쉽게 찾는 방법은 "Xamarin"을 검색하는 것입니다.

 Xamarin은 Android, iOS 및 Windows의 기본 기능을 .NET 개체로 표시합니다. 따라서 앱은 네이티브 API와 네이티브 사용자 정의 컨트롤에 대한 모든 권한이 있으며 네이티브 플랫폼 언어로 작성된 앱과 응답 성능이 동일합니다.

 프로젝트를 만든 후 Visual Studio의 모든 생산성 기능을 활용할 수 있습니다. 예를 들어 디자이너를 사용하여 페이지를 만들고 IntelliSense를 사용하여 모바일 플랫폼의 네이티브 API를 탐색할 수 있습니다. 앱을 실행하고 앱의 모양을 확인할 준비가 되면 Visual Studio Emulator for Android 또는 Android SDK 에뮬레이터를 사용하거나 기본적으로 Windows 앱을 실행하거나 Windows Phone Emulator에서 Windows 앱을 실행할 수 있습니다. 또한 테더링된 Android 및 Windows 디바이스를 직접 사용할 수도 있습니다. iOS 프로젝트의 경우 네트워크로 연결된 Mac에 연결하고 Visual Studio에서 Mac 에뮬레이터를 시작하거나 테더링된 디바이스에 연결합니다.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Xamarin.Forms를 사용하여 모든 디바이스에서 렌더링되는 페이지 집합을 디자인합니다.
 앱 디자인의 복잡도에 따라 프로젝트 템플릿의 *모바일 앱* 그룹에서 **Xamarin.Forms** 템플릿을 사용하여 앱을 빌드하는 것이 효과적일 수 있습니다. Xamarin.Forms는 Android, iOS 및 Windows에서 공유할 수 있는 단일 인터페이스를 만들 수 있는 UI 도구 키트입니다.  Xamarin.Forms 솔루션을 컴파일하면 Android 앱, iOS 앱 및 Windows 앱을 얻게 됩니다. 자세한 내용은 [Xamarin을 사용한 모바일 개발에 대해 알아보기](../cross-platform/learn-about-mobile-development-with-xamarin.md)를 참조하세요.

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Android, iOS 및 Windows 앱 간에 코드 공유
 Xamarin.Forms를 사용하지 않고 각 플랫폼에 대해 개별적으로 디자인하는 경우 플랫폼 프로젝트(Android, iOS 및 Windows) 간에 UI가 아닌 코드를 대부분 공유할 수 있습니다. 여기에는 비즈니스 논리, 클라우드 통합, 데이터베이스 액세스 또는 .NET Framework를 대상으로 하는 다른 코드가 포함됩니다. 공유할 수 없는 코드는 특정 플랫폼을 대상으로 하는 코드뿐입니다.

 ![Windows, iOs 및 Android UI 간에 코드 공유](../cross-platform/media/sharecode.png "ShareCode")

 공유 프로젝트나 이식 가능한 클래스 라이브러리 프로젝트 중 하나 또는 둘 다를 사용하여 코드를 공유할 수 있습니다. 공유 프로젝트에 적합한 코드도 있고 이식 가능한 클래스 라이브러리 프로젝트에 더 적절한 코드도 있습니다.

|**자세히**|
|--------------------|
|코드를 공유할 때 공유 프로젝트나 이식 가능한 클래스 라이브러리 프로젝트 중 하나를 사용할지 아니면 둘 다를 사용할지 선택<br /><br /> [플랫폼 간 코드 공유](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (.NET Framework 블로그)<br /><br /> [Sharing Code Options](/xamarin/cross-platform/app-fundamentals/code-sharing)(코드 공유 옵션)(Xamarin)<br /><br /> [.NET Framework를 사용한 코드 공유 옵션](https://msdn.microsoft.com/library/dn720832.aspx) (MSDN Library)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a> Windows 10 디바이스를 대상으로 지정
 ![Windows 디바이스](../cross-platform/media/windowsdevices.png "Windows 장치")

 전체 범위의 Windows 10 디바이스를 대상으로 하는 단일 앱을 만들려는 경우 유니버설 Windows 앱을 만듭니다. 단일 프로젝트를 사용하여 앱을 디자인하면 어떤 디바이스에서 페이지를 표시하든 관계없이 페이지가 제대로 렌더링됩니다.

 유니버설 Windows 앱 프로젝트 템플릿으로 시작합니다. 페이지를 시각적으로 디자인한 다음 미리 보기 창에서 열어 다양한 유형의 디바이스에서 어떻게 표시되는지 확인합니다. 디바이스에서 페이지가 표시되는 방식이 마음에 들지 않으면 화면 크기, 해상도 또는 다양한 방향(예: 가로 또는 세로 모드)에 잘 맞도록 페이지를 최적화할 수 있습니다. Visual Studio의 직관적인 도구 창과 쉽게 액세스할 수 있는 메뉴 옵션을 사용하여 모든 작업을 수행할 수 있습니다. 앱을 실행 하 고 코드를 단계별로 실행할 준비가 되 면 **표준** 도구 모음에 있는 하나의 드롭다운 목록에서 다양 한 장치 유형의 장치 에뮬레이터 및 시뮬레이터를 모두 찾을 수 있습니다.

 Windows 10은 비교적 새로운 기능이므로 Windows 8.1을 대상으로 하는 프로젝트 템플릿도 있습니다. 필요한 경우 해당 프로젝트 템플릿을 사용할 수 있으며 Windows 10 휴대폰, 태블릿 및 PC에서 앱이 실행됩니다. 그러나 Windows 8.1을 실행하는 모든 디바이스는 Windows 10으로 자동 업그레이드를 받으므로 대신 Windows 8.1을 대상으로 해야 하는 특별한 이유가 없다면 Windows 10을 대상으로 하는 프로젝트 템플릿을 사용하는 것이 좋습니다.

|**자세한 정보**|
|--------------------|
|[유니버설 Windows 앱에 대해 알아보기](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows 개발자 센터)|
|[첫 번째 앱 빌드](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows 개발자 센터)|
|[UWP(유니버설 Windows 플랫폼)용 앱 개발](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[UWP(유니버설 Windows 플랫폼)로 앱 마이그레이션](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a> Android, iOS 및 Windows용 앱 빌드(HTML/JavaScript)
 ![디바이스](../cross-platform/media/homedevices.png "HomeDevices")

 HTML과 JavaScript에 대해 잘 알고 있는 웹 개발자는 Visual Studio Tools For Apache Cordova를 사용하여 Windows, Android 및 iOS를 대상으로 지정할 수 있습니다. 이러한 앱은 세 플랫폼을 모두 대상으로 지정할 수 있으며 가장 익숙한 기술과  프로세스를 사용하여 빌드할 수 있습니다.

 Apache Cordova는 플러그 인 모델이 포함된 프레임워크입니다. 이 플러그 인 모델은 세 플랫폼 모두(Android, iOS 및 Windows)의 기본 디바이스 기능에 액세스하는 데 사용할 수 있는 단일 JavaScript API를 제공합니다.

 이러한 API는 크로스 플랫폼이기 때문에 작성하는 코드를 세 플랫폼 간에 대부분 공유할 수 있습니다. 따라서 개발 및 유지 관리 비용이 줄어듭니다. 또한 처음부터 다시 시작할 필요가 없습니다. 다양한 유형의 웹 애플리케이션을 만든 경우 어떤 방식으로든 수정하거나 다시 디자인할 필요 없이 해당 파일을 Cordova 앱과 공유할 수 있습니다.

 ![다중&#45;장치 하이브리드 앱](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 시작하려면 Visual Studio 2015를 설치하고 설정하는 동안 **HTML/JavaScript(Apache Cordova)** 기능을 선택합니다. Visual Studio 2013을 사용 중인 경우 Visual Studio Tools for Apache Cordova 확장을 설치합니다. 어떤 경우든지 Cordova 도구는 다중 플랫폼 앱을 빌드하는 데 필요한 모든 타사 소프트웨어를 자동으로 설치합니다.

 확장을 설치한 후 Visual Studio를 열고 **빈 앱 (Apache Cordova)** 프로젝트를 만듭니다. 그런 다음 JavaScript 또는 Typescript를 사용하여 앱을 개발할 수 있습니다. 플러그 인을 추가하여 앱 기능을 확장할 수도 있습니다. 플러그 인의 API는 코드 작성 시 IntelliSense에 표시됩니다.

 앱을 실행하고 코드를 단계별로 실행할 준비가 되면 Apache Ripple 에뮬레이터 또는 Visual Studio Emulator(Android 또는 Windows Phone)와 같은 에뮬레이터, 브라우저 또는 컴퓨터에 직접 연결한 디바이스를 선택합니다. 그런 다음 앱을 시작합니다. Windows PC에서 앱을 개발하는 경우 Windows PC에서 실행할 수도 있습니다. 이러한 모든 옵션은 Visual Studio Tools for Apache Cordova의 일부로 Visual Studio에 기본 제공됩니다.

 유니버설 Windows 앱을 만들기 위한 프로젝트 템플릿은 Visual Studio에서 계속 제공되므로 Windows 디바이스만 대상으로 하려는 경우 자유롭게 사용할 수 있습니다. 나중에 Android 및 iOS를 대상으로 지정하려는 경우에는 언제든지 코드를 Cordova 프로젝트로 이동할 수 있습니다. 오픈 소스 버전 WinJS API가 있기 때문에 해당 API를 사용하는 코드를 다시 사용할 수 있습니다. 즉, 나중에 다른 플랫폼을 대상으로 하려는 경우 Visual Studio Tools for Apache Cordova로 시작하는 것이 좋습니다.

|**자세히**|
|--------------------|
|[Visual Studio 설치](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Visual Studio Tools for Apache Cordova 시작](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Android 용 Visual Studio 에뮬레이터에 대해 알아보기](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a> Android 및 Windows 용 앱 빌드 (c + +)
 ![C++를 사용하여 Android, iOS 및 Windows용 빌드](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 먼저 Visual Studio 2015와 플랫폼 간 모바일 개발용 Visual C++ 도구를 설치합니다. 그런 다음 Android용 Native Activity 애플리케이션이나 Windows를 대상으로 하는 앱을 빌드할 수 있습니다. iOS를 대상으로 하는 C++ 템플릿은 아직 사용할 수 없습니다. 원하는 경우 동일한 솔루션에서 Android 및 Windows를 대상으로 지정한 후 플랫폼 간 정적 또는 동적 공유 라이브러리를 사용하여 Android와 Windows 사이에 코드를 공유할 수 있습니다.

 게임과 같은 고급 그래픽 조작이 필요한 Android용 앱을 빌드해야 하는 경우 C++를 사용하여 빌드할 수 있습니다. **Native-Activity 애플리케이션(Android)** 프로젝트를 사용하여 시작합니다. 이 프로젝트는 Clang 도구 체인을 완전히 지원합니다.

 ![Native Activity 프로젝트 템플릿](../cross-platform/media/cross-plat-cpp-native.png "교차 Plat_CPP_Native")

 앱을 실행하고 앱의 모양을 확인할 준비가 되면 Android용 Visual Studio 에뮬레이터를 사용합니다. 이 에뮬레이터는 빠르고 안정적이며 설치와 구성이 간편합니다.

 C++ 및 유니버설 Windows 앱 프로젝트 템플릿을 사용하여 전체 범위의 Windows 10 디바이스를 대상으로 하는 앱을 빌드할 수도 있습니다. 자세한 내용은 이 항목의 앞부분에 있는 [Windows 10 디바이스를 대상으로 지정](#WindowsHTML) 섹션을 참조하세요.

 정적 또는 동적 공유 라이브러리를 만들어 Android와 Windows 사이에 C++ 코드를 공유할 수 있습니다.

 ![정적 및 동적 공유 라이브러리](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 이 섹션의 앞부분에서 설명한 것과 같은 Windows 또는 Android 프로젝트에서 해당 라이브러리를 사용할 수 있습니다. 또한 Xamarin, Java 또는 관리되지 않는 DLL에서 함수를 호출할 수 있는 언어를 사용하여 빌드하는 앱에서도 해당 라이브러리를 사용할 수 있습니다.

 이러한 라이브러리에서 코드를 작성할 때 IntelliSense를 사용하여 Android 및 Windows 플랫폼의 기본 API를 탐색할 수 있습니다. 이러한 라이브러리 프로젝트는 Visual Studio 디버거에 완전히 통합되므로 중단점을 설정하고 코드를 단계별로 실행하고 디버거의 모든 고급 기능을 사용하여 문제를 찾고 해결할 수 있습니다.

|**자세히**|
|--------------------|
|[Visual Studio를 다운로드 합니다.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[플랫폼 간 모바일 개발용 Visual C++ 설치](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|
|[여러 플랫폼을 대상으로 한 C++ 사용에 대해 알아보기](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[필요한 것을 설치한 다음 Android용 Native-Activity 애플리케이션 만들기](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Library)|
|[Android 용 Visual Studio 에뮬레이터에 대해 알아보기](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Android 및 Windows 앱과 C++ 코드를 공유하는 방법에 대해 알아보기](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[플랫폼 간 모바일 개발 예제](https://msdn.microsoft.com/library/dn707596.aspx)(MSDN 라이브러리)|
|[개발자 코드 샘플](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B)(code.msdn)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a> Visual Studio tools for Unity를 사용 하 여 Android, iOS 및 Windows 용 플랫폼 간 게임 빌드
 Visual Studio Tools for Unity는 Visual Studio의 강력한 코드 편집, 생산성 및 디버깅 도구를 Unity와 통합 하는 Visual Studio의 무료 확장입니다. *Unity*는 Windows, IOS, Android 및 기타 플랫폼을 대상으로 하는 몰입 형 앱을 위한 인기 있는 플랫폼 간 게임/그래픽 엔진 및 개발 환경입니다.

 ![VSTU 개발 환경](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 VSTU(Visual Studio Tools for Unity)를 사용하면 Visual Studio를 통해 게임 및 편집기 스크립트를 C#으로 작성한 다음 강력한 디버거를 사용하여 오류를 찾고 수정할 수 있습니다. VSTU의 최신 릴리스에서는 Unity 5를 지원하며 Unity의 ShaderLab 셰이더 언어를 위한 구문 색 지정, Unity와의 보다 효율적인 동기화, 보다 풍부한 디버깅, MonoBehavior 마법사에 대한 향상된 코드 생성 기능을 포함합니다. VSTU는 Unity 프로젝트 파일, 콘솔 메시지 및 Visual Studio에서 게임을 시작하는 기능도 제공하므로 코드를 작성하는 동안 Unity 편집기 전환에 소요되는 시간을 단축할 수 있습니다.

 이제 Unity와 Visual Studio Tools for Unity를 사용하여 게임 작성을 시작해 보세요.

|**자세히**|
|--------------------|
|[Visual Studio를 사용하여 Unity 게임을 제작하는 방법 알아보기](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Visual Studio Tools for Unity에 대해 자세히 알아보기](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Library)|
|[Visual Studio Tools for Unity 사용 시작](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Library)|
|[Visual Studio Tools for Unity 2.0 Preview에서 향상된 최신 기능에 대해 알아보기](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio 블로그)|
|[Visual Studio Tools for Unity 2.0 Preview에 대한 동영상 소개 보기](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (동영상)|
|[Unity에 대해 알아보기](https://unity.com/) (Unity 웹 사이트)|

## <a name="see-also"></a>관련 항목

- [Add Office 365 API’s to a Visual Studio project](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)(Visual Studio 프로젝트에 Office 365 API 추가)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
