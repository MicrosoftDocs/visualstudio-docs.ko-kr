---
title: C++를 사용한 플랫폼 간 모바일 개발 설치 | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: c3ea8c91c54586cf54b82566a4803b464e01750c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916491"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>C++를 사용하여 플랫폼 간 모바일 개발 설치

Visual Studio에서 C++를 사용하여 Windows 데스크톱 앱, UWP(유니버설 Windows 플랫폼) 앱, Linux 앱 및 이제 Android 및 iOS용 앱을 빌드할 수 있습니다. **C++를 사용한 모바일 개발** 워크로드는 플랫폼 간 iOS, Android 및 UWP Visual Studio 템플릿을 포함하는 Visual Studio의 설치 가능한 구성 요소 집합입니다. 직접 찾아서 다운로드 및 구성하지 않고도 신속하게 시작하는 데 필요한 플랫폼 간 도구 및 SDK를 설치합니다. Visual Studio에서 이러한 도구를 사용하여 플랫폼 간 프로젝트를 쉽게 만들고, 편집, 디버그 및 테스트할 수 있습니다. 이 문서에서는 Visual Studio를 사용하여 C++로 플랫폼 간 앱을 개발하는 데 필요한 도구 및 타사 소프트웨어를 설치하는 방법을 설명합니다. 개요는 [Visual C++ 플랫폼 간 모바일](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)을 참조하세요.

## <a name="requirements"></a>요구 사항

::: moniker range="vs-2017"

- 설치 요구 사항은 [Visual Studio 제품군 시스템 요구 사항](/visualstudio/productinfo/vs2017-system-requirements-vs)을 참조하세요.

   > [!IMPORTANT]
   > Windows 7 또는 Windows Server 2008 R2를 사용하는 경우 Windows 데스크톱 애플리케이션용 코드, Android Native Activity 앱 및 라이브러리, iOS용 앱 및 코드 라이브러리를 개발할 수 있지만 Windows 스토어 또는 UWP 앱은 개발할 수 없습니다.

::: moniker-end
::: moniker range=">=vs-2019"

- 설치 요구 사항은 [Visual Studio 제품군 시스템 요구 사항](/visualstudio/releases/2019/system-requirements)을 참조하세요.

   > [!IMPORTANT]
   > Windows 7 또는 Windows Server 2008 R2를 사용하는 경우 Windows 데스크톱 애플리케이션용 코드, Android Native Activity 앱 및 라이브러리, iOS용 앱 및 코드 라이브러리를 개발할 수 있지만 Windows Phone 또는 UWP 앱은 개발할 수 없습니다.

::: moniker-end

특정 디바이스 플랫폼용 앱을 빌드하려는 경우에는 다음의 몇 가지 요구 사항이 추가로 적용됩니다.

- Android SDK와 함께 제공되는 x86 Android 에뮬레이터는 Intel HAXM(Hardware Accelerated Execution Manager)과 같은 하드웨어 가속을 사용할 수 있는 컴퓨터에서 가장 잘 작동합니다. 자세한 내용은 [에뮬레이터 성능에 대한 하드웨어 가속(Hyper-V 및 HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows)을 참조하세요.

- iOS용 코드를 빌드하려면 Apple ID, iOS 개발자 프로그램 계정 및 OS X Mavericks(버전 10.9) 이상 버전에서 [Xcode](https://developer.apple.com/xcode/) 버전 10.2 이상을 실행할 수 있는 Mac 컴퓨터가 필요합니다. 설치 단계 링크는 [iOS용 설치 도구](#install-tools-for-ios)를 참조하세요.

- Windows Phone 에뮬레이터를 사용하려면 Hyper-V를 실행할 수 있는 컴퓨터가 필요합니다. 에뮬레이터를 설치하고 실행하려면 먼저 Windows에서 Hyper-V 기능을 사용하도록 설정해야 합니다. 자세한 내용은 에뮬레이터의 [시스템 요구 사항](system-requirements-for-the-visual-studio-emulator-for-android.md)을 참조하세요.

## <a name="get-the-tools"></a>도구 다운로드

C++를 사용한 모바일 개발은 Visual Studio Community/Professional/Enterprise 버전에서 사용할 수 있습니다. Visual Studio를 설치하려면 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동합니다. 플랫폼 간 모바일 개발 도구는 Visual Studio 2015부터 사용할 수 있습니다.

## <a name="install-the-tools"></a>도구 설치

Visual Studio 설치 관리자에는 **C++를 사용한 모바일 개발** 워크로드가 포함됩니다. 이 워크로드는 Visual Studio에서 Android 및 iOS 개발에 필요한 C++ 언어 도구, 템플릿 및 구성 요소를 설치합니다. 여기에는 Android 빌드 및 디버깅에 필요한 GCC 및 Clang 도구 집합, Android SDK, iOS 개발을 위해 Mac과 통신하기 위한 구성 요소가 포함됩니다. 또한 iOS 및 Android 앱 개발을 지원하는 데 필요한 그 밖의 모든 타사 도구 및 소프트웨어 개발 키트를 설치합니다. 이러한 타사 도구는 대부분 Android 플랫폼 지원에 필요한 오픈 소스 소프트웨어입니다.

- Android 플랫폼을 대상으로 하는 C++ 코드를 빌드하려면 Android NDK(네이티브 개발 키트), Apache Ant, C++ Android 개발 도구가 필요합니다.

- Google Android Emulator 및 Intel HAXM(Hardware Accelerated Execution Manager)은 선택적이지만 권장되는 구성 요소입니다. (Intel HAXM 드라이버는 Intel 프로세서에서만 작동하며 Hyper-V를 비롯한 일부 VM과 호환되지 않습니다.) Android 디바이스에서 직접 개발하고 디버그할 수 있지만, 종종 데스크톱에서 에뮬레이터를 사용하여 디버그하기가 더 쉽습니다.

- iOS 플랫폼을 대상으로 하는 C++ 코드를 빌드하려면 C++ iOS 개발 도구가 필요합니다.

> [!NOTE]
> Visual Studio 2015를 사용하는 경우 [플랫폼 간 모바일 개발용 Visual C++ 설치(Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015)를 참조하세요.

### <a name="install-the-mobile-development-with-c-workload"></a>C++를 사용한 모바일 개발 워크로드 설치

1. **시작** 메뉴에서 **Visual Studio 설치 관리자**를 실행합니다.

1. Visual Studio를 이미 설치한 경우 수정하려는 설치된 Visual Studio 버전의 **수정** 단추를 선택합니다. 또는 **설치**를 선택하여 Visual Studio를 설치합니다.

1. **워크로드** 탭을 선택한 상태에서 아래로 스크롤하여 Visual Studio 설치 관리자에서 **C++를 사용한 모바일 개발**을 선택합니다. 이 워크로드를 선택하면 C++ 개발에 필요한 다른 구성 요소도 선택됩니다. 동시에 설치할 다른 워크로드와 개별 구성 요소를 선택할 수도 있습니다. UWP를 대상으로 하는 플랫폼 간 코드를 빌드하려면 **유니버설 Windows 플랫폼 개발** 워크로드를 선택합니다.

1. **설치 세부 정보** 창에서 **C++를 사용한 모바일 개발**을 확장합니다. **선택 사항** 섹션에서 NDK의 추가 버전, Google Android Emulator, Intel Hardware Accelerated Execution Manager 및 IncrediBuild 빌드 가속화 도구를 선택할 수 있습니다.

1. 기본적으로 워크로드에는 하나 이상의 Android SDK 설정 구성 요소가 포함됩니다. Android SDK의 추가 버전을 사용할 수 있습니다. 설치에 다른 버전을 추가하려면 **개별 구성 요소** 탭을 선택한 다음, **SDK, 라이브러리 및 프레임워크** 섹션으로 아래로 스크롤하여 선택합니다.

1. **수정** 또는 **설치** 단추를 선택하여 **C++를 사용한 모바일 개발** 워크로드와 기타 선택한 워크로드 및 선택적 구성 요소를 설치합니다.

   설치가 완료되면 설치 관리자를 닫고 컴퓨터를 다시 시작합니다. 타사 구성 요소에 대한 일부 설정 작업은 컴퓨터가 다시 시작된 다음에야 적용됩니다.

   > [!IMPORTANT]
   > 모든 항목을 정상적으로 설치하려면 컴퓨터를 다시 시작해야 합니다.

1. Visual Studio를 엽니다.

## <a name="install-tools-for-ios"></a>iOS용 도구 설치

Visual Studio를 사용하여 iOS 코드를 편집 및 디버그하고 iOS 시뮬레이터 또는 iOS 디바이스에 배포할 수 있습니다. 그러나 라이선스 제한으로 인해 Mac에서는 원격으로 코드를 빌드해야 합니다. Visual Studio를 사용하여 iOS 앱을 빌드 및 실행하려면 Mac에서 원격 에이전트를 설치 및 구성해야 합니다. 자세한 설치 지침, 필수 조건 및 구성 옵션은 [iOS를 사용하여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조하세요. iOS용으로 빌드하지 않는 경우에는 이 단계를 건너뛸 수 있습니다.

## <a name="install-or-update-dependencies-manually"></a>수동으로 종속성 설치 또는 업데이트

**C++를 사용한 모바일 개발** 워크로드(또는 Visual Studio 2015의 경우 Visual C++ 모바일 개발 옵션)를 설치할 때 Visual Studio 설치 관리자를 사용하여 타사 종속성을 하나 이상 설치하지 않는 경우 나중에 [도구 설치](#install-the-tools)의 단계를 사용하여 설치할 수 있습니다. Visual Studio 설치 관리자는 최신 타사 구성 요소를 설치하도록 정기적으로 업데이트됩니다. 설치 관리자를 사용하여 업데이트된 SDK 및 NDK를 설치할 수 있습니다. Visual Studio와 독립적으로 설치하거나 업데이트할 수도 있습니다.

Android SDK 디렉터리에서 SDK Manager 앱을 다시 실행하여 SDK를 업데이트하고 선택적 도구 및 추가 API 수준을 설치할 수 있습니다. **관리자 권한으로 실행** 을 사용하여 SDK Manager 앱을 실행하지 않으면 업데이트가 설치되지 않을 수도 있습니다. Android 앱을 빌드하는 데 문제가 있는 경우 SDK Manager에서 설치된 SDK에 대한 업데이트를 확인합니다.

Android SDK와 함께 제공되는 Android 에뮬레이터 중 일부를 사용하려면 하드웨어 가속을 설정해야 할 수도 있습니다. 자세한 내용은 [에뮬레이터 성능에 대한 하드웨어 가속(Hyper-V 및 HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)을 참조하세요.

대부분의 경우 Visual Studio는 설치된 타사 소프트웨어의 구성을 검색하고 내부 환경 변수에서 설치 경로를 유지 관리할 수 있습니다. Visual Studio IDE에서 이러한 플랫폼 간 개발 도구의 기본 경로를 재정의할 수 있습니다.

#### <a name="to-set-the-paths-for-third-party-tools"></a>타사 도구에 대한 경로를 설정하려면

1. Visual Studio 메뉴 모음에서 **도구** > **옵션**을 선택합니다.

1. **옵션** 대화 상자에서 **플랫폼 간** > **C++**  > **Android**를 선택합니다.

   ![Android 도구 경로 옵션](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. 도구에서 사용되는 경로를 변경하려면 경로 옆에 있는 확인란을 선택하고 텍스트 상자에서 폴더 경로를 편집합니다. 찾아보기 단추( **...** )를 사용하여 **위치 선택** 대화 상자를 열고 폴더를 선택할 수도 있습니다.

1. **확인** 을 선택하여 사용자 지정 도구 폴더 위치를 저장합니다.

## <a name="see-also"></a>참조

- [iOS를 사용하여 빌드할 도구 설치 및 구성](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ 플랫폼 간 모바일](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
