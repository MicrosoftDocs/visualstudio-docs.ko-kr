---
title: Mac용 Visual Studio 제거
description: Mac용 Visual Studio 및 관련 도구를 제거하는 방법을 안내합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.topic: how-to
ms.openlocfilehash: f8452094f0059a1ffa4421d1ccd02ee244559c72
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950338"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Mac용 Visual Studio 제거

Mac용 Visual Studio와 같은 독립형 앱을 포함하여 플랫폼 간 애플리케이션 개발을 지원하는 여러 가지 Xamarin 제품이 있습니다.

이 가이드를 통해 관련 섹션으로 이동하여 각 제품을 개별적으로 제거하거나 [스크립트 제거](#uninstall-script) 섹션에 제공된 스크립트를 사용하여 모든 제품을 제거할 수 있습니다.

## <a name="uninstall-script"></a>스크립트 제거

Mac용 Visual Studio 및 머신의 모든 구성 요소를 제거하는 데 사용할 수 있는 두 가지 스크립트가 있습니다.

- [Visual Studio 및 Xamarin 스크립트](#visual-studio-for-mac-and-xamarin-script)
- [.NET Core 스크립트](#net-core-script)

다음 섹션에서는 스크립트를 다운로드하고 사용하는 방법에 대한 정보를 제공합니다.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Mac용 Visual Studio 및 Xamarin 스크립트

[스크립트 제거](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh)를 사용하면 Visual Studio 및 Xamarin 구성 요소를 한 번에 제거할 수 있습니다.

이 제거 스크립트는 이 문서에 나와 있는 대부분의 명령을 포함합니다. 다음과 같은 세 가지 항목은 외부 종속성 문제의 소지가 있어 이 스크립트에 포함되지 않았습니다. 이를 제거하려면 아래 관련 섹션으로 이동하여 수동으로 제거하세요.

- **[Mono 제거](#uninstall-mono-sdk-mdk)**
- **[Android AVD 제거](#uninstall-android-avd)**
- **[Android SDK 및 Java SDK 제거](#uninstall-android-sdk-and-java-sdk)**

스크립트를 실행하려면 다음 단계를 수행하십시오.

1. 스크립트를 마우스 오른쪽 단추로 클릭하고 **다른 이름으로 저장**을 선택하여 Mac에 파일을 저장합니다.
2. 터미널을 열고 스크립트를 다운로드한 위치로 작업 디렉터리를 변경합니다.

    ```bash
    cd /location/of/file
    ```

3. 스크립트를 실행 가능으로 설정하고 **sudo**로 실행합니다.

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. 마지막으로 제거 스크립트를 삭제합니다.

### <a name="net-core-script"></a>.NET Core 스크립트

.NET Core의 제거 스크립트는 [dotnet cli 리포지토리](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)에 있습니다.

스크립트를 실행하려면 다음 단계를 수행하십시오.

1. 스크립트를 마우스 오른쪽 단추로 클릭하고 **다른 이름으로 저장**을 선택하여 Mac에 파일을 저장합니다.
2. 터미널을 열고 스크립트를 다운로드한 위치로 작업 디렉터리를 변경합니다.

    ```bash
    cd /location/of/file
    ```

3. 스크립트를 실행 가능으로 설정하고 **sudo**로 실행합니다.

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. 마지막으로 .NET Core 제거 스크립트를 삭제합니다.

## <a name="uninstall-visual-studio-for-mac"></a>Mac용 Visual Studio 제거

Mac에서 Visual Studio를 제거하는 첫 번째 단계는 **/Applications** 디렉터리에서 **Visual Studio.app**을 찾아 **휴지통**으로 끌어놓는 것입니다. 또는 다음 이미지의 그림과 같이 마우스 오른쪽 단추를 클릭하고 **Move to Trash**(휴지통으로 이동)를 선택합니다.

![Visual Studio 애플리케이션을 휴지통으로 이동](media/uninstall-image1.png)

Xamarin과 관련된 다른 파일이 여전히 파일 시스템에 남아 있다고 해도 이 앱 번들을 삭제하면 Mac용 Visual Studio가 제거됩니다.

Mac용 Visual Studio의 모든 흔적을 제거하려면 터미널에서 다음 명령을 실행합니다.

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

다양한 Xamarin 파일 및 폴더를 포함하는 다음 디렉터리를 제거할 수도 있습니다. 그러나 제거하기 전에 이 디렉터리에는 Android 서명 키가 포함되어 있다는 점에 유의해야 합니다. 자세한 내용은 **[Android SDK 및 Java SDK 제거](#uninstall-android-sdk-and-java-sdk)** 섹션을 참조하세요.

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Mono SDK(MDK) 제거

Mono는 Microsoft .NET Framework의 오픈 소스 구현으로서 Xamarin.iOS, Xamarin.Android 및 Xamarin.Mac 등의 모든 Xamarin 제품에서 해당 플랫폼을 대상으로 하여 C#으로 개발하는 데 사용됩니다.

> [!WARNING]
> Mac용 Visual Studio 이외에 Unity와 같은 애플리케이션에서도 Mono를 사용합니다.
> Mono를 제거하기 전에 Mono에 대한 다른 종속성이 없는지 확인하세요.

컴퓨터에서 Mono 프레임워크를 제거하려면 터미널에서 다음 명령을 실행합니다.

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Xamarin.Android 제거

Xamarin.Android를 설치하고 사용하려면 Android SDK, Java SDK 등의 몇 가지 항목이 필요합니다.

Xamarin.Android를 제거하려면 다음 명령을 사용합니다.

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Android SDK 및 Java SDK 제거

Android SDK는 Android 애플리케이션 개발에 필요합니다. Android SDK의 모든 부분을 완전히 제거하려면 **\~/Library/Developer/Xamarin/** 에서 해당 파일을 찾아 **휴지통** 으로 이동합니다.

> [!WARNING]
> Mac용 Visual Studio에서 생성되는 Android 서명 키는 `~/Library/Developer/Xamarin/Keystore`에 있습니다. 해당 키를 적절하게 백업해야 합니다. 또는 키 저장소를 보존하려면 이 디렉터리를 제거하지 마세요.

Java SDK(JDK)는 이미 Mac OS X/macOS에 포함되어 있으므로 제거할 필요가 없습니다.

### <a name="uninstall-android-avd"></a>Android AVD 제거

> [!WARNING]
> Mac용 Visual Studio 외에 Android Studio와 같은 애플리케이션에서도 Android AVD 및 추가 Android 구성 요소를 사용합니다. 이 디렉터리를 제거하면 Android Studio에서 프로젝트가 중단될 수 있습니다.

Android AVD 및 기타 Android 구성 요소를 제거하려면 다음 명령을 사용합니다.

```bash
rm -rf ~/.android
```

Android AVD만 제거하려면 다음 명령을 사용합니다.

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Xamarin.iOS 제거

Xamarin.iOS를 사용하면 Mac용 Visual Studio에서 C# 또는 F#으로 iOS 애플리케이션을 개발할 수 있습니다.

터미널에서 다음 명령을 사용하여 파일 시스템에서 모든 Xamarin.iOS 파일을 제거합니다.

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Xamarin.Mac 제거

다음 두 가지 명령으로 Mac에서 제품과 라이선스를 각각 제거하여 Xamarin.Mac를 컴퓨터에서 제거할 수 있습니다.

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Workbooks 및 Inspector 제거

버전 1.2.2부터 터미널에서 다음 명령을 실행하여 Xamarin Workbooks 및 Inspector를 제거할 수 있습니다.

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

이전 버전의 경우 다음 아티팩트를 수동으로 제거해야 합니다.

* `"/Applications/Xamarin Workbooks.app"`에서 Workbooks 앱 삭제
* `"Applications/Xamarin Inspector.app"`에서 Inspector 앱 삭제
* `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` 및 `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"` 추가 기능 삭제
* `/Library/Frameworks/Xamarin.Interactive.framework` 및 `/Library/Frameworks/Xamarin.Inspector.framework`에서 Inspector 및 지원 파일 삭제

## <a name="uninstall-the-xamarin-profiler"></a>Xamarin Profiler 제거

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Visual Studio 설치 관리자 제거

Xamarin Universal 설치 관리자의 모든 흔적을 제거하려면 다음 명령을 사용합니다.

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>참조

- [Visual Studio 제거(Windows에서)](/visualstudio/install/uninstall-visual-studio)