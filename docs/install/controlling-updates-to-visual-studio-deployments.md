---
title: 배포에 대한 업데이트 제어
description: 네트워크에서 설치할 때 Visual Studio에서 업데이트를 찾는 위치를 변경하는 방법을 알아봅니다.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8743f042c7c33da34895f93e5df3990f6e0b2ed2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115314"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>네트워크 기반 Visual Studio 배포에 대한 업데이트 제어

엔터프라이즈 관리자는 때때로 레이아웃을 만들고 최종 사용자에게 배포하기 위해 네트워크 파일 공유에서 레이아웃을 호스트합니다.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio가 업데이트를 검색하는 위치 제어

설치가 네트워크 공유에서 배포된 경우에도 기본적으로 Visual Studio에서는 온라인으로 업데이트를 계속 검색합니다. 업데이트가 사용 가능한 경우 사용자는 업데이트를 설치할 수 있습니다. 오프라인 레이아웃에 없는 업데이트된 콘텐츠는 웹에서 다운로드됩니다.

Visual Studio가 업데이트를 검색하는 위치를 직접 제어하려면 Visual Studio가 검색하는 위치를 수정할 수 있습니다. 사용자가 업데이트되는 버전도 제어할 수 있습니다. 이렇게 하려면 다음 단계를 따르십시오.

1. 오프라인 레이아웃을 만듭니다.

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. 레이아웃을 호스트할 파일 공유로 복사합니다.

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. 레이아웃에서 response.json 파일을 수정하고 `channelUri` 값을 변경하여 관리자가 제어하는 channelManifest.json 복사본을 가리킵니다.

   다음 예제와 같이 값에서 백슬래시를 이스케이프해야 합니다.

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   이제 최종 사용자는 이 공유에서 설치 프로그램을 실행하여 Visual Studio를 설치할 수 있습니다.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

엔터프라이즈 관리자가 사용자가 최신 버전의 Visual Studio로 업데이트할 시점을 결정할 경우 다음과 같이 [레이아웃 위치를 업데이트](update-a-network-installation-of-visual-studio.md)하여 업데이트된 파일을 통합할 수 있습니다.

1. 다음 명령과 비슷한 명령을 사용합니다.

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. 업데이트된 레이아웃의 response.json 파일에 사용자 지정, 특히 다음과 같은 channelUri 수정이 포함되어 있는지 확인합니다.

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   이 레이아웃의 기존 Visual Studio 설치는 `\\server\share\VS\ChannelManifest.json`에서 업데이트를 검색합니다. 이 channelManifest.json이 사용자가 설치한 것보다 최신 버전인 경우 Visual Studio에서는 사용자에게 사용 가능한 업데이트가 있음을 알립니다.

   새로운 설치를 통해 레이아웃에서 직접 Visual Studio의 업데이트된 버전이 자동으로 설치됩니다.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE에서 알림 제어

::: moniker range="vs-2017"

앞의 설명대로 Visual Studio에서는 설치가 시작된 위치(예: 네트워크 공유 또는 인터넷)를 확인하여 사용 가능한 업데이트가 있는지 확인합니다. 사용 가능한 업데이트가 있을 경우 Visual Studio에서는 창의 오른쪽 위에 알림 플래그를 표시하여 사용자에게 알립니다.

   ![업데이트 알림 플래그](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

앞의 설명대로 Visual Studio에서는 설치가 시작된 위치(예: 네트워크 공유 또는 인터넷)를 확인하여 사용 가능한 업데이트가 있는지 확인합니다. 사용 가능한 업데이트가 있을 경우 Visual Studio에서는 창의 오른쪽 위에 알림 아이콘을 통해 사용자에게 알립니다.

   ![Visual Studio IDE의 알림 아이콘](media/vs-2019/notification-bar.png "Visual Studio IDE의 알림 아이콘")

::: moniker-end

최종 사용자에게 업데이트를 알리지 않으려는 경우 알림을 사용하지 않도록 설정할 수 있습니다. (예를 들어, 하려는 중앙 소프트웨어 배포 메커니즘을 통해 업데이트를 제공하는 경우 알림을 사용하지 않도록 설정할 수 있습니다.)

::: moniker range="vs-2017"

Visual Studio 2017에서는 [레지스트리 항목을 개인 레지스트리에 저장](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)하므로 레지스트리를 일반적인 방법으로 직접 편집할 수 없습니다. 하지만 Visual Studio에는 Visual Studio 설정을 변경하는 데 사용할 수 있는 `vsregedit.exe` 유틸리티가 포함되어 있습니다. 다음 명령으로 알림을 끌 수 있습니다.

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019에서는 [레지스트리 항목을 개인 레지스트리에 저장](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)하므로 레지스트리를 일반적인 방법으로 직접 편집할 수 없습니다. 하지만 Visual Studio에는 Visual Studio 설정을 변경하는 데 사용할 수 있는 `vsregedit.exe` 유틸리티가 포함되어 있습니다. 다음 명령으로 알림을 끌 수 있습니다.

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

편집할 설치된 인스턴스와 일치하도록 디렉터리를 바꾸어야 합니다.

> [!TIP]
> [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances)를 사용하여 클라이언트 워크스테이션에서 Visual Studio의 특정 인스턴스를 찾습니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 인스턴스 관리 도구](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing/)
