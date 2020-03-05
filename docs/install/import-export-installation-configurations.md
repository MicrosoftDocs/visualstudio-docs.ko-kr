---
title: 설치 구성 가져오기 또는 내보내기
titleSuffix: ''
description: 다른 사용자와 공유하기 위해 설치 구성을 .vsconfig 파일로 내보내고 가져와 복제하는 방법을 알아봅니다.
ms.date: 05/18/2019
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 12d22334094b848350d44d245685532fed196389
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114847"
---
# <a name="import-or-export-installation-configurations"></a>설치 구성 가져오기 또는 내보내기

설치 구성 파일을 사용하여 조직에서 Visual Studio를 구성할 수 있습니다. 이렇게 하려면 Visual Studio 설치 관리자를 사용하여 워크로드 및 구성 요소 정보를 .vsconfig 파일로 내보내면 됩니다. 그런 다음, 구성을 새 설치 또는 기존 설치로 가져오고 다른 사용자와 공유할 수 있습니다.

방법은 다음과 같습니다.

::: moniker range="vs-2017"

> [!NOTE]
> 이 기능은 Visual Studio 2017 버전 15.9 이상에서만 사용할 수 있습니다.

::: moniker-end

## <a name="export-a-configuration"></a>구성 내보내기

이전에 설치된 Visual Studio 인스턴스 또는 현재 설치 중인 인스턴스에서 설치 구성 파일을 내보내도록 선택할 수 있습니다.

1. Visual Studio 설치 관리자를 엽니다.

1. 제품 카드에서 **기타** 단추를 선택한 후 **구성 내보내기**를 선택합니다.

   ![Visual Studio 설치 관리자의 제품 카드에서 구성 내보내기](../install/media/vs-2019/vs-installer-export-config.png)

1. .vsconfig 파일을 저장할 위치로 이동하거나 위치를 찾아본 다음, **세부 정보 검토**를 선택합니다.

   ![Visual Studio 설치 관리자에서 구성 내보내기](../install/media/vs-2019/export-configuration-confirmation.png)

1. 원하는 워크로드 및 구성 요소를 가져왔는지 확인한 후 **내보내기**를 선택합니다.

## <a name="import-a-configuration"></a>구성 가져오기

설치 구성 파일을 가져올 준비가 되면 다음 단계를 수행합니다.

1. Visual Studio 설치 관리자를 엽니다.

1. 제품 카드에서 **기타** 단추를 선택한 후 **구성 가져오기**를 선택합니다.

1. 가져올 .vsconfig 파일을 찾은 다음, **세부 정보 검토**를 선택합니다.

1. 원하는 워크로드 및 구성 요소를 가져왔는지 확인한 후 **닫기**를 선택합니다.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>누락된 구성 요소 자동 설치

**Visual Studio 2019의 새로운 기능**: .vsconfig 파일을 솔루션 루트 디렉터리에 저장한 후 솔루션을 열면 Visual Studio에서는 누락된 구성 요소를 자동으로 검색하고 설치할지 묻는 메시지를 표시합니다.

![솔루션 탐색기에서 추가 구성 요소 제안](../install/media/vs-2019/solution-explorer-config-file.png)

솔루션 탐색기에서 바로 .vsconfig 파일을 생성할 수도 있습니다.

1. 솔루션 파일을 마우스 오른쪽 단추로 클릭합니다.

1. **추가** > **설치 구성 파일**을 선택합니다.

1. .vsconfig 파일을 저장할 위치를 확인한 후 **세부 정보 검토**를 선택합니다.

1. 원하는 워크로드 및 구성 요소를 가져왔는지 확인한 후 **내보내기**를 선택합니다.

::: moniker-end

> [!NOTE]
> 자세한 내용은 [.vsconfig를 사용하여 조직에서 Visual Studio 구성](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/)을 참조하세요.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [Visual Studio의 네트워크 설치 만들기](create-a-network-installation-of-visual-studio.md)
* [Visual Studio의 네트워크 기반 설치 업데이트](update-a-network-installation-of-visual-studio.md)
* [Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)
* [엔터프라이즈 배포에 대한 기본값 설정](set-defaults-for-enterprise-deployments.md)
