---
title: WSL 2에서 .NET Core 앱 디버그
description: Visual Studio를 종료하지 않고 WSL 2에서 .NET Core 앱을 실행하고 디버그하는 방법을 알아봅니다.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 6ae43b79b9db766d752a25fb538b7f208e6f5e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865620"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Visual Studio를 사용하여 WSL 2에서 .NET Core 앱 디버그

WSL 2를 사용하여 Visual Studio를 종료하지 않고 Linux에서 .NET Core 앱을 쉽게 실행하고 디버그할 수 있습니다. 플랫폼 간 개발자는 더 많은 대상 환경을 테스트하는 간단한 방법으로 이 방법을 사용할 수 있습니다.

Linux를 대상으로 하는 Windows .NET 사용자에게 WSL 2는 현실적인 프로덕션과 생산성 사이에서 가장 효과적인 선택입니다. Visual Studio에서는 [원격 디버거](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)를 사용하는 원격 Linux 환경이나 [컨테이너 도구](../containers/overview.md)를 사용하는 컨테이너에서 이미 디버그할 수 있습니다. 현실적인 프로덕션에 중점을 두는 경우 해당 옵션 중 하나를 사용해야 합니다. 쉽고 빠른 내부 루프가 더 중요한 경우에는 WSL 2가 적합한 옵션입니다.

한 가지 방법만 선택할 필요는 없습니다. Docker 및 WSL 2의 시작 프로필이 동일한 프로젝트에 있을 수 있으며 특정 실행에 더 적합한 프로필을 선택할 수 있습니다. 또한 앱을 배포한 후에는 문제가 있는 경우에도 언제든지 원격 디버거를 사용하여 연결할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

- WSL 2를 사용한 .NET Core 디버깅 선택적 구성 요소가 있는 Visual Studio 2019 v16.9 미리 보기 1 이상 버전

  선택적 구성 요소는 .NET Core 플랫폼 간 또는 ASP.NET 및 웹 개발 워크로드와 함께 기본적으로 포함됩니다. 이러한 워크로드 중 하나 또는 둘 다를 설치해야 합니다.

- [WSL 2](/windows/wsl/about) 설치

- 선택한 [배포](https://aka.ms/wslstore) 설치

## <a name="start-debugging-with-wsl-2"></a>WSL 2를 사용하여 디버깅 시작

1. 필요한 구성 요소를 설치한 후 Visual Studio에서 ASP.NET Core 웹앱 또는 .NET Core 콘솔 앱을 엽니다. 그러면 WSL 2라는 새 시작 프로필이 표시됩니다.

   ![시작 프로필 목록의 WSL 2 시작 프로필](media/linux-wsl2-debugging-select-launch-profile.png)

1. 이 프로필을 선택하여 *launchSettings.json* 에 추가합니다.

   파일의 몇 가지 주요 특성이 다음 예제에 표시되어 있습니다.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   새 프로필을 선택하면 확장에서 WSL 2 배포가 .NET Core 앱을 실행하도록 구성되었는지 확인하고 누락된 종속성을 설치하는 데 도움을 줍니다. 이러한 종속성을 설치하면 WSL 2에서 디버그할 준비가 된 것입니다.

1. 일반적인 방법으로 디버깅을 시작합니다. 그러면 앱이 기본 WSL 2 배포에서 실행됩니다.

   Linux에서 실행되고 있는지 확인하는 간단한 방법은 `Environment.OSVersion`의 값을 확인하는 것입니다.

>[!NOTE]
> Ubuntu 및 Debian만 테스트되었으며 지원됩니다. .NET Core에서 지원하는 다른 배포도 작동하지만 [.NET Core 런타임](https://aka.ms/wsldotnet) 및 [Curl](https://curl.haxx.se/)을 수동으로 설치해야 합니다.

## <a name="choose-a-specific-distribution"></a>특정 배포 선택

기본적으로 WSL 2 시작 프로필은 *wsl.exe* 에 설정된 기본 배포를 사용합니다. 시작 프로필이 특정 배포를 대상으로 하도록 하려면 기본값과 관계없이 시작 프로필을 수정할 수 있습니다. 예를 들어 웹앱을 디버깅하고 Ubuntu 20.04에서 테스트하려는 경우 시작 프로필은 다음과 같습니다.

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>여러 배포를 대상으로 지정

한 단계 더 나아가 여러 배포에서 실행해야 하는 애플리케이션에서 작업하는 경우 각 배포에서 신속하게 테스트하려면 여러 시작 프로필을 사용할 수 있습니다. 예를 들어 Debian, Ubuntu 18.04 및 Ubuntu 20.04에서 콘솔 앱을 테스트해야 하는 경우 다음과 같은 시작 프로필을 사용할 수 있습니다.

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

이러한 시작 프로필을 사용하면 대상 배포 간을 간단히 전환할 수 있으며, 모두 Visual Studio를 종료하지 않고도 편안하게 수행할 수 있습니다.

![시작 프로필 목록의 여러 WSL 2 시작 프로필](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>시작 프로필의 WSL 설정

다음 표에서는 시작 프로필에서 지원되는 설정을 보여 줍니다.

|속성|기본값|목적|토큰 지원 여부|
|-|-|-|-|
|executablePath|dotnet|실행할 실행 파일|예|
|commandLineArgs|WSL 환경에 매핑된 MSBuild 속성 TargetPath의 값|executablePath에 전달된 명령줄 인수|예|
|workingDirectory|콘솔 앱: {*OutDir*}</br>웹앱: {*ProjectDir*}|디버깅을 시작할 작업 디렉터리|예|
|environmentVariables||디버그된 프로세스에 대해 설정할 환경 변수의 키 값 쌍|예|
|setupScriptPath||디버깅 전에 실행할 스크립트. ~/.bash_profile과 같은 스크립트를 실행하는 데 유용합니다.|예|
|distributionName||사용할 WSL 배포의 이름|아니요|
|launchBrowser|false|브라우저 시작 여부|아니요|
|launchUrl||launchBrowser가 true인 경우 시작할 URL|아니요|

지원되는 토큰:

{*ProjectDir*} - 프로젝트 디렉터리의 경로

{*OutDir*} - MSBuild 속성 `OutDir`의 값

>[!NOTE]
> 모든 경로는 Windows가 아닌 WSL에 대한 것입니다.
