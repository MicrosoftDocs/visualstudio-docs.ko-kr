---
title: 로컬 폴더에 배포
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3355636eba7556a472d8ce272437fb07c30714be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184175"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Visual Studio를 사용하여 로컬 폴더에 앱 배포

**게시** 도구를 사용하여 ASP.NET, ASP.NET Core, .NET Core 및 Python 앱을 Visual Studio의 로컬 폴더에 게시합니다. Node.js의 경우 단계는 지원되지만 사용자 인터페이스는 다릅니다.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> 로컬 폴더에 Windows 데스크톱 애플리케이션을 게시해야 하는 경우 [ClickOnce를 사용하여 데스크톱 앱 배포](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)(C# 또는 Visual Basic)를 참조하세요. C++/CLR의 경우 [ClickOnce를 사용하여 네이티브 앱 배포](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) 또는 C/C++의 경우 [설치 프로젝트를 사용하여 네이티브 앱 배포](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)를 참조하세요.

## <a name="deploy-to-a-local-folder"></a>로컬 폴더에 배포

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 상황에 맞는 메뉴에서 게시 명령](../deployment/media/quickstart-publish.png "게시 선택")

1. **게시** 대화 상자에서 **폴더**를 선택합니다.

    ![게시 대상으로 폴더 선택](../deployment/media/quickstart-publish-folder.png "폴더 선택")

1. 경로를 입력하거나 **찾아보기**를 선택하여 폴더를 지정합니다.

    ![폴더 경로 지정](../deployment/media/quickstart-publish-folder-path.png "폴더 선택")

1. **게시**를 선택합니다. Visual Studio는 프로젝트를 빌드하고 지정된 폴더에 게시합니다. 프로필 요약을 표시하는 프로젝트 속성 **게시** 창이 나타납니다.

    ![프로필 요약을 표시하는 게시 속성 창](../deployment/media/quickstart-publish-folder-summary.png)

1. 배포 설정을 구성하려면 게시 프로필 요약에서 **편집**을 선택하고 **설정** 탭을 선택합니다.

    ![프로필 설정](../deployment/media/quickstart-profile-settings.png "프로필 설정")

1. 디버그 또는 릴리스 구성을 배포할지 여부와 같은 옵션을 구성한 다음, **저장**을 선택합니다.

1. 다시 게시하려면 **게시**를 선택합니다.

게시된 파일을 원하는 방식으로 배포합니다. 예를 들어 *.zip* 파일로 패키지하거나, 간단한 복사 명령을 사용하거나, 선택한 설치 패키지와 함께 배포할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [게시 도구를 사용하여 .NET Core 애플리케이션 배포](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Microsoft Store(데스크톱 브리지)의 데스크톱 앱 패키지](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [.NET Framework 및 애플리케이션 배포](/dotnet/framework/deployment/)
