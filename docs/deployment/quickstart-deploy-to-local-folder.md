---
title: 로컬 폴더에 배포
description: 게시 도구를 사용하여 ASP.NET, ASP.NET Core, .NET Core 및 Python 앱을 Visual Studio의 폴더에 게시하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2b16c10d13f63be43ad2e8c3e16d24c0f9fd5e38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927433"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Visual Studio를 사용하여 앱을 폴더에 배포

**게시** 도구를 사용하여 ASP.NET, ASP.NET Core, .NET Core 및 Python 앱을 Visual Studio의 폴더에 게시합니다. Node.js의 경우 단계는 지원되지만 사용자 인터페이스는 다릅니다.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> 폴더에 Windows 데스크톱 애플리케이션을 게시해야 하는 경우 [ClickOnce를 사용하여 데스크톱 앱 배포](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)(C# 또는 Visual Basic)를 참조하세요. C++/CLR의 경우 [ClickOnce를 사용하여 네이티브 앱 배포](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) 또는 C/C++의 경우 [설치 프로젝트를 사용하여 네이티브 앱 배포](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)를 참조하세요.

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> 폴더에 .NET Core 3.1 이상 Windows 데스크톱 애플리케이션을 게시해야 하는 경우 [ClickOnce를 사용하여 .NET Windows 애플리케이션 배포](quickstart-deploy-using-clickonce-folder.md)를 참조하세요.

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>로컬 폴더에 배포

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시** 를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 상황에 맞는 메뉴에서 게시 명령](../deployment/media/quickstart-publish.png "게시 선택")

1. 게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. **새로 만들기** 를 선택합니다.

1. **게시** 창에서 **폴더** 를 선택합니다.

    ![게시 대상으로 폴더 선택](../deployment/media/quickstart-publish-folder-new.png "폴더 선택")

::: moniker range=">=vs-2019"

4. .NET Core 3.1 이상 Windows 애플리케이션을 배포하는 경우 **특정 대상** 창에서 **폴더** 를 선택해야 할 수 있습니다.

![특정 대상으로 폴더 선택](../deployment/media/quickstart-publish-folder-targets.png "특정 대상 선택")

5. ClickOnce를 사용하여 .NET Core 3.1 이상 Windows 애플리케이션을 게시하려는 경우 [ClickOnce를 사용하여 .NET Windows 애플리케이션 배포](quickstart-deploy-using-clickonce-folder.md)를 참조하세요.

 ::: moniker-end

4. 경로를 입력하거나 **찾아보기** 를 선택하여 폴더를 지정합니다.

    ![폴더 경로 지정](../deployment/media/quickstart-publish-folder-path.png "폴더 선택")

1. **게시** 를 선택합니다. Visual Studio는 프로젝트를 빌드하고 지정된 폴더에 게시합니다. 프로필 요약을 표시하는 프로젝트 속성 **게시** 창이 나타납니다.

    ![프로필 요약을 표시하는 게시 속성 창](../deployment/media/quickstart-publish-folder-summary.png)

1. 배포 설정을 구성하려면 게시 프로필 요약에서 **편집** 을 선택하고 **설정** 탭을 선택합니다.

   표시되는 설정은 애플리케이션 유형에 따라 달라집니다. 다음 그림은 ASP.NET Core 앱에 대한 설정 예입니다.

    ![프로필 설정](../deployment/media/quickstart-profile-settings.png "프로필 설정")

    .NET에서 설정을 선택하는 방법에 대한 추가 도움말은 다음을 참조하세요.

    - [프레임워크 종속 배포와 자체 포함 배포](/dotnet/core/deploying/)
    - [대상 런타임 식별자(이식 가능한 RID 등)](/dotnet/core/rid-catalog)
    - [디버그 및 릴리스 구성](../ide/understanding-build-configurations.md)

1. 디버그 또는 릴리스 구성을 배포할지 여부와 같은 옵션을 구성한 다음, **저장** 을 선택합니다.

1. 다시 게시하려면 **게시** 를 선택합니다.

게시된 파일을 원하는 방식으로 배포합니다. 예를 들어 *.zip* 파일로 패키지하거나, 간단한 복사 명령을 사용하거나, 선택한 설치 패키지와 함께 배포할 수 있습니다.

## <a name="next-steps"></a>다음 단계

.NET 앱:

- [게시 도구를 사용하여 .NET Core 애플리케이션 배포](/dotnet/core/deploying/deploy-with-vs)
- [.NET Core 애플리케이션 게시(프레임워크 종속 배포와 자체 포함 배포)](/dotnet/core/deploying/)
- [.NET Framework 및 애플리케이션 배포](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [ClickOnce를 사용하여 .NET Windows 애플리케이션 배포](quickstart-deploy-using-clickonce-folder.md)
 ::: moniker-end
