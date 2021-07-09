---
title: Windows에서 Docker 클라이언트 오류 해결 | Microsoft Docs
description: Visual Studio를 사용하여 웹앱을 만들고 Docker에 배포하는 경우 발생하는 문제를 해결합니다.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 5f48b5c06e91b9c05e6edc7e2a1738aeb677a7ba
ms.sourcegitcommit: 69456d802203d21dabc3ae8662547a3241c24f47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110235913"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Docker 관련 Visual Studio 개발 문제 해결

Visual Studio Container Tools로 작업할 때, 애플리케이션을 빌드하거나 디버그하는 중 문제가 발생할 수 있습니다. 다음은 몇 가지 일반적인 문제 해결 단계입니다.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>볼륨 공유 사용 안 함. Windows용 Docker CE 설정(Linux 컨테이너에만 해당)에 볼륨 공유 사용

파일 공유는 Docker에서 Hyper-V를 사용하는 경우에만 관리해야 합니다. WSL 2를 사용하는 경우에는 다음 단계가 필요하지 않으며 파일 공유 옵션이 표시되지 않습니다. 이 문제를 해결하려면:

1. 알림 영역에서 **Windows용 Docker** 를 마우스 오른쪽 단추로 클릭한 다음 **설정** 을 선택합니다.
1. **리소스** > **파일 공유** 를 선택하고 액세스해야 하는 폴더를 공유합니다. 전체 시스템 드라이브를 공유할 수는 있지만 권장되지는 않습니다.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="공유 드라이브":::

> [!TIP]
> Visual Studio 2017 버전 15.6 이후의 Visual Studio 버전에서는 **공유 드라이브** 가 구성되지 않은 경우 메시지가 표시됩니다.

## <a name="unable-to-start-debugging"></a>디버깅을 시작할 수 없음

한 가지 이유로 사용자 프로필 폴더에 부실 디버깅 구성 요소가 있는 것과 관련 있을 수 있습니다. 다음 디버그 세션에 최신 디버깅 구성 요소가 다운로드되도록 하려면 다음 명령을 실행하여 이러한 폴더를 제거합니다.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>애플리케이션을 디버깅할 때 네트워킹에 국한되는 오류

호스트 컴퓨터에서 네트워크 관련 구성 요소를 새로 고침할 [정리 컨테이너 호스트 네트워킹](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)에서 다운로드할 수 있는 스크립트를 실행 시도합니다.

## <a name="mounts-denied"></a>탑재 거부됨

macOS용 Docker를 사용하는 경우 /usr/local/share/dotnet/sdk/NuGetFallbackFolder 폴더를 참조할 때 오류가 발생할 수 있습니다. Docker에서 [파일 공유] 탭에 폴더를 추가하세요.

## <a name="docker-users-group"></a>Docker 사용자 그룹

컨테이너를 사용할 때 Visual Studio에서 다음과 같은 오류가 발생할 수 있습니다.

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Docker 컨테이너를 사용할 수 있는 권한이 있으려면 ‘docker-users’ 그룹의 멤버여야 합니다.  Windows 10에서 해당 그룹에 자신을 추가하려면 다음 단계를 수행합니다.

1. 시작 메뉴에서 **컴퓨터 관리** 를 엽니다.
1. **로컬 사용자 및 그룹** 을 확장하고 **그룹** 을 선택합니다.
1. **docker-users** 그룹을 찾은 다음, 마우스 오른쪽 단추를 클릭하고 **그룹에 추가** 를 선택합니다.
1. 사용자 계정을 하나 이상 추가합니다.
1. 변경 내용을 적용하려면 로그아웃했다가 다시 로그인합니다.

관리자 명령 프롬프트에서 `net localgroup` 명령을 사용하여 특정 그룹에 사용자를 추가할 수도 있습니다.

```cmd
net localgroup docker-users DOMAIN\username /add
```

PowerShell에서 [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) 함수를 사용합니다.

## <a name="low-disk-space"></a>디스크 공간 부족

기본적으로 Docker는 *% ProgramData%/Docker/* 폴더에 이미지를 저장합니다. 이 폴더는 일반적으로 시스템 드라이브인 *C:\ProgramData\Docker\*에 있습니다. 이미지가 시스템 드라이브에서 중요한 공간을 차지하지 않으려면 이미지 폴더 위치를 변경하면 됩니다. 이를 수행하려면:

 1. 작업 표시줄에서 Docker 아이콘을 마우스 오른쪽 단추로 클릭하고 **설정** 를 선택합니다.
 1. **Docker 엔진** 을 선택합니다. 
 1. 편집 창에서 Docker 이미지의 원하는 위치 값을 사용하여 `graph` 속성 설정을 추가합니다.

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Docker 파일 공유 스크린샷":::

**적용 및 다시 시작** 을 클릭합니다. 이러한 단계는 *%ProgramData%\docker\config\daemon.json* 에서 구성 파일을 수정합니다. 이전에 빌드된 이미지는 이동되지 않습니다.

## <a name="container-type-mismatch"></a>컨테이너 유형 불일치

프로젝트에 Docker 지원을 추가할 때 Windows 또는 Linux 컨테이너를 선택할 수 있습니다. Docker 서버 호스트가 프로젝트 대상과 동일한 컨테이너 유형을 실행하도록 구성되지 않은 경우 다음과 유사한 오류가 표시될 수 있습니다.

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="Docker 호스트 및 프로젝트 불일치 스크린샷":::

이 문제를 해결하려면:

- 시스템 트레이에서 Windows용 Docker 아이콘을 마우스 오른쪽 단추로 클릭하고 **Windows 컨테이너로 전환...** 또는 **Linux 컨테이너로 전환...** 을 선택합니다.

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub 리포지토리

다른 문제가 발생하면, [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) 문제를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio 문제 해결](/troubleshoot/visualstudio/welcome-visual-studio/)
