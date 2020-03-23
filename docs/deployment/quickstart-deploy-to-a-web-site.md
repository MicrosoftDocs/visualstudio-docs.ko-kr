---
title: 웹 사이트에 게시
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1236c3057cd209bd5c7c81304a2168704927c506
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71127939"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Visual Studio를 사용하여 웹 사이트에 웹앱 게시

**게시** 도구를 사용하여 ASP.NET, ASP.NET Core, .NET Core 및 Python 앱을 Visual Studio의 웹 사이트에 게시합니다. Node.js의 경우 단계는 지원되지만 사용자 인터페이스는 다릅니다.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> 네트워크 파일 공유에 Windows 데스크톱 애플리케이션을 게시해야 하는 경우 [ClickOnce를 사용하여 데스크톱 앱 배포](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)(C# 또는 Visual Basic)를 참조하세요. C++/CLI의 경우 [ClickOnce를 사용하여 네이티브 앱 배포](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)를 참조하고, C/C++의 경우 [설치 프로젝트를 사용하여 네이티브 앱 배포](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)를 참조하세요.

## <a name="publish-to-a-web-site"></a>웹 사이트에 게시

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 상황에 맞는 메뉴에서 게시 명령](../deployment/media/quickstart-publish.png "게시 선택")

1. 게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. **새 프로필 만들기**를 선택합니다.

1. **게시 대상 선택** 대화 상자에서 **IIS, FTP 등**을 선택합니다.

    ![IIS, FTP 등을 선택합니다.](../deployment/media/quickstart-publish-iis-ftp.png "IIS, FTP 등을 선택합니다.")

1. **게시**를 선택합니다. 프로필 게시 설정 대화 상자가 열립니다.

    ![폴더 선택](../deployment/media/quickstart-publish-settings-web.png "폴더 선택")

1. **게시 방법** 필드에서 **웹 배포** 또는 **FTP**와 같은 방법을 선택합니다. 다음에 표시되는 설정은 게시 방법에 해당합니다. 웹 배포는 IIS 서버에 웹 애플리케이션 및 웹 사이트의 배포를 간소화하고, 서버에서 애플리케이션으로 설치되어야 합니다. [웹 플랫폼 설치 관리자](https://www.microsoft.com/web/downloads/platform.aspx)를 사용하여 설치합니다.

1. 게시 방법에 대한 필수 설정을 구성하고 **연결 유효성 검사**를 선택합니다. 서버 또는 대상을 사용할 수 있고 설정이 올바른 경우 연결이 유효함을 나타내는 메시지가 나타나고, 게시할 준비가 된 것입니다.

    ![연결 유효성 검사](../deployment/media/quickstart-publish-web-deploy.png "연결 유효성 검사")

1. **설정**을 선택하여 디버그 또는 릴리스 구성을 배포할지 여부와 같은 기타 배포 설정을 구성한 다음, **저장**을 선택합니다. 원격으로 디버그하는 경우 디버그 구성은 필수입니다.

1. 게시하려면 **게시**를 선택합니다. 출력 창은 배포 진행률 및 결과를 표시합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Visual Studio를 사용하여 게시 프로필을 만드는 방법을 알아보았습니다. 게시 설정을 가져와서 게시 프로필을 구성할 수도 있습니다.

> [!div class="nextstepaction"]
> [게시 설정 가져오기 및 IIS에 배포](tutorial-import-publish-settings-iis.md)
