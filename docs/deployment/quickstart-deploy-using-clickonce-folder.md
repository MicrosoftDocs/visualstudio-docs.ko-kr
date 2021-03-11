---
description: Visual Studio 2019 버전 16.8부터는 Visual Studio에서 ClickOnce를 사용하여 .NET Core 3.1 이상 Windows 데스크톱 애플리케이션을 게시하는 데 게시 도구를 사용할 수 있습니다.
title: ClickOnce를 사용하여 .NET Windows 데스크톱 애플리케이션 배포
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: d3977408f191aabc734226fd6b637fcfaaf5e9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165711"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>ClickOnce를 사용하여 .NET Windows 데스크톱 애플리케이션 배포

Visual Studio 2019 버전 16.8부터는 Visual Studio에서 ClickOnce를 사용하여 .NET Core 3.1 이상 Windows 데스크톱 애플리케이션을 게시하는 데 **게시** 도구를 사용할 수 있습니다.

> [!NOTE]
> .NET Framework Windows 애플리케이션을 게시해야 하는 경우 [ClickOnce를 사용하여 데스크톱 앱 배포](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)(C# 또는 Visual Basic)를 참조하세요.

## <a name="publishing-with-clickonce"></a>ClickOnce를 사용하여 게시

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시** 를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 상황에 맞는 메뉴에서 게시 명령](../deployment/media/quickstart-clickonce-solution-explorer.png "게시 선택")

1. 게시 프로필을 이전에 구성한 경우 **게시** 페이지가 나타납니다. **새로 만들기** 를 선택합니다.

1. **게시** 마법사에서 **폴더** 를 선택합니다.

    ![게시 대상으로 폴더 선택](../deployment/media/quickstart-clickonce-publish-folder-category.png "폴더 선택")

1. **특정 대상** 페이지에서 **ClickOnce** 를 선택합니다.

    ![특정 대상으로 ClickOnce 선택](../deployment/media/quickstart-clickonce-publish-folder-target.png "ClickOnce 선택")

1. 경로를 입력하거나 **찾아보기** 를 선택하여 게시 위치를 선택합니다.

    ![게시 위치의 경로 지정](../deployment/media/quickstart-clickonce-publish-location.png "경로 입력")

1. **설치 위치** 페이지에서 사용자가 애플리케이션을 설치할 위치를 선택합니다.

    ![폴더 경로 지정](../deployment/media/quickstart-clickonce-install-location.png "설치 위치 선택")

1. **설정** 페이지에서 ClickOnce에 필요한 설정을 제공할 수 있습니다.

1. UNC 경로 또는 웹 사이트에서 설치하도록 선택한 경우 이 페이지에서 애플리케이션을 오프라인으로 사용할 수 있는지 여부를 지정할 수 있습니다. 이 옵션을 선택하면 사용자 시작 메뉴에 애플리케이션이 나열되어 새 버전이 게시될 때 애플리케이션을 자동으로 업데이트할 수 있습니다. 기본적으로 업데이트는 설치 위치에서 사용할 수 있습니다.  업데이트에 다른 위치를 사용하려는 경우 업데이트 설정 링크를 사용하여 지정할 수 있습니다. 애플리케이션을 오프라인으로 사용할 수 있도록 설정하지 않으면 설치 위치에서 실행됩니다.

    ![게시 설정 지정](../deployment/media/quickstart-clickonce-unc-settings.png "게시 설정 선택")

1. CD, DVD 또는 USB 드라이브에서 설치하도록 선택한 경우 이 페이지에서 애플리케이션이 자동 업데이트를 지원하는지 여부도 지정할 수 있습니다. 업데이트를 지원하도록 선택하는 경우 업데이트 위치가 필요하며 유효한 UNC 경로 또는 웹 사이트여야 합니다.

    ![게시 설정 선택](../deployment/media/quickstart-clickonce-settings.png "게시 설정 선택")

이 페이지에는 페이지 맨 위에 있는 링크를 통해 설치에 포함할 **애플리케이션 파일**, 설치할 **필수 구성 요소** 패키지 및 기타 **옵션** 을 지정할 수 있는 기능이 포함되어 있습니다.

또한 이 페이지에서 게시 버전을 설정하고 게시할 때마다 자동으로 버전이 증가하는지 여부를 설정할 수 있습니다.

> [!NOTE]
> 게시 버전 번호는 각 ClickOnce 프로필에 대해 고유합니다. 둘 이상의 프로필을 유지하려는 경우 이 점을 염두에 두어야 합니다.

10. **매니페스트 서명** 페이지에서 매니페스트에 서명해야 하는지 여부와 사용할 인증서를 지정할 수 있습니다.

    ![ClickOnce 매니페스트 서명](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. **구성** 페이지에서 원하는 프로젝트 구성을 선택할 수 있습니다.

     ![게시 구성 지정](../deployment/media/quickstart-clickonce-configuration.png)

    선택하는 설정에 대한 추가 도움말은 다음을 참조하세요.

    - [프레임워크 종속 배포와 자체 포함 배포](/dotnet/core/deploying/)
    - [대상 런타임 식별자(이식 가능한 RID 등)](/dotnet/core/rid-catalog)
    - [디버그 및 릴리스 구성](../ide/understanding-build-configurations.md)

1. **마침** 을 선택하여 새 ClickOnce 게시 프로필을 저장합니다.

1. **요약** 페이지에서 **게시** 를 선택하면 Visual Studio에서 프로젝트를 빌드하고 지정된 게시 폴더에 게시합니다. 이 페이지에는 프로필 요약도 표시됩니다.

    ![프로필 요약을 표시하는 게시 속성 창](../deployment/media/quickstart-clickonce-summary.png)

1. 다시 게시하려면 **게시** 를 선택합니다.

## <a name="next-steps"></a>다음 단계

.NET 앱:

- [.NET Framework 및 애플리케이션 배포](/dotnet/framework/deployment/)
- [ClickOnce 참조](clickonce-reference.md)
