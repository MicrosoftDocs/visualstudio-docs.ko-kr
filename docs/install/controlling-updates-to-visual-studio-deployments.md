---
title: 배포에 대한 업데이트 제어
description: 네트워크에서 설치할 때 Visual Studio에서 업데이트를 찾는 위치를 변경하는 방법을 알아봅니다.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3504e866a7f89de8fa38f92a8bfea501ddd952c9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666798"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>네트워크 기반 Visual Studio 배포에 대한 업데이트 제어

엔터프라이즈 관리자는 때때로 레이아웃을 만들고 최종 사용자에게 배포하기 위해 네트워크 파일 공유에서 레이아웃을 호스트합니다. 이 페이지에서는 네트워크 레이아웃 옵션을 적절하게 구성하는 방법을 설명합니다. 

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio가 업데이트를 검색하는 위치 제어

**시나리오 1: 클라이언트가 원래 레이아웃에서 설치되었지만 네트워크 레이아웃 위치 또는 웹에서 업데이트를 받도록 구성됨**

설치가 원래 네트워크 공유에서 배포된 경우에도 기본적으로 Visual Studio에서는 온라인으로 업데이트를 계속 검색합니다. 웹에서 업데이트가 사용 가능하면 사용자가 업데이트를 설치할 수 있습니다. 업데이트된 제품 비트에 대해 네트워크 레이아웃 캐시를 먼저 검사하는 경우에도 해당 항목이 없으면 Visual Studio가 웹에서 업데이트된 제품 비트를 검색하여 다운로드합니다.

**시나리오 2: 클라이언트가 원래 설치되었고 네트워크 레이아웃에서만 업데이트를 수신해야 함**

예를 들어 클라이언트 컴퓨터가 인터넷에 연결되지 않고 항상 레이아웃으로부터 업데이트를 설치하도록 하려는 경우와 같이 Visual Studio 클라이언트가 업데이트를 검색하는 위치를 제어하려는 경우에는 클라이언트의 설치 관리자가 업데이트된 제품 비트를 검색하는 위치를 구성할 수 있습니다. 클라이언트가 레이아웃으로부터 초기 설치를 수행하기 전에 이 설정이 올바르게 구성되어 있는지 확인하는 것이 가장 좋습니다. 

1. 오프라인 레이아웃을 만듭니다.

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. 레이아웃을 호스트할 파일 공유로 복사합니다.

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. 레이아웃에서 `response.json` 파일을 수정하고 `channelUri` 값을 변경하여 관리자가 제어하는 channelManifest.json 복사본을 가리킵니다.

   다음 예제와 같이 값에서 백슬래시를 이스케이프해야 합니다.

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   이제 최종 사용자는 이 공유의 설치 프로그램을 실행하여 Visual Studio를 설치할 수 있습니다.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

엔터프라이즈 관리자가 사용자가 최신 버전의 Visual Studio로 업데이트할 시점을 결정할 경우 다음과 같이 [레이아웃 위치를 업데이트](update-a-network-installation-of-visual-studio.md)하여 업데이트된 파일을 통합할 수 있습니다.

1. 다음 명령과 비슷한 명령을 사용합니다.

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. 업데이트된 레이아웃의 `response.json` 파일에 사용자 지정, 특히 다음과 같은 channelUri 수정이 포함되어 있는지 확인합니다.

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

이 레이아웃의 기존 Visual Studio 설치는 `\\server\share\VS\ChannelManifest.json`에서 업데이트를 검색합니다. 이 channelManifest.json이 사용자가 설치한 것보다 최신 버전인 경우 Visual Studio에서는 사용자에게 사용 가능한 업데이트가 있음을 알립니다.

클라이언트에서 시작된 모든 설치 업데이트는 레이아웃에서 직접 업데이트된 버전의 Visual Studio를 자동으로 설치합니다.

**시나리오 3: 클라이언트가 원래 웹에서 설치되었지만 이제는 네트워크 레이아웃에서만 업데이트를 수신해야 함**

클라이언트 컴퓨터가 이미 웹에서 Visual Studio를 설치했을 수 있지만 이제는 관리자가 모든 향후 업데이트를 관리되는 레이아웃에서 제공하려는 경우도 있을 수 있습니다. 이 시나리오를 지원하는 유일한 방법은 원하는 버전의 제품을 사용하여 네트워크 레이아웃을 만든 다음 클라이언트 컴퓨터에서 레이아웃 위치(예: `\\server\share\vs_enterprise.exe`)의 부트스트래퍼를 실행하는 것입니다. 이상적으로는 원래 클라이언트 설치는 ChannelURI가 올바르게 구성된 네트워크 레이아웃의 부트스트래퍼를 사용하여 실행되어야 하지만, 네트워크 레이아웃 위치의 업데이트된 부트스트래퍼를 실행하는 것도 유효합니다. 이러한 작업 중 하나는 클라이언트 머신에서 해당 특정 레이아웃 위치와의 연결을 포함합니다. 이 시나리오가 제대로 작동하려면 레이아웃의 `response.json` 파일에 구성된 ‘ChannelURI’가 원래 설치가 실행될 때 클라이언트 컴퓨터에 설정된 ChannelURI와 동일해야 합니다. 이 값은 원래 인터넷 [릴리스 채널](https://aka.ms/vs/16/release/channel)로 설정되었을 가능성이 높습니다. 


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

## <a name="see-also"></a>참조

* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [관리자 업데이트 사용](enabling-administrator-updates.md)
* [관리자 업데이트 적용](applying-administrator-updates.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 인스턴스 관리 도구](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing/)
