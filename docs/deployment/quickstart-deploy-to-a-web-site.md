---
title: 웹 사이트에 게시
description: 게시 도구를 사용하여 ASP.NET, ASP.NET Core, .NET Core 및 Python 앱을 Visual Studio의 웹 사이트에 게시하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf4248b9155e780b63faf48983adfca866440b98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927420"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Visual Studio를 사용하여 웹 사이트에 웹앱 게시

**게시** 도구를 사용하여 ASP.NET, ASP.NET Core, .NET Core 및 Python 앱을 Visual Studio의 웹 사이트에 게시합니다. Node.js의 경우 단계는 지원되지만 사용자 인터페이스는 다릅니다.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> 네트워크 파일 공유에 Windows 데스크톱 애플리케이션을 게시해야 하는 경우 [ClickOnce를 사용하여 데스크톱 앱 배포](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)(C# 또는 Visual Basic)를 참조하세요. C++/CLR의 경우 [ClickOnce를 사용하여 네이티브 앱 배포](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) 또는 C/C++의 경우 [설치 프로젝트를 사용하여 네이티브 앱 배포](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)를 참조하세요.

## <a name="publish-to-a-web-site"></a>웹 사이트에 게시

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시** 를 선택합니다(또는 **빌드** > **게시** 메뉴 항목 사용).

    ![솔루션 탐색기의 프로젝트 상황에 맞는 메뉴에서 게시 명령](../deployment/media/quickstart-publish.png "게시 선택")

1. 게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. **새로 만들기** 를 선택합니다.

1. **게시** 창에서 **웹 서버(IIS)** 를 선택합니다.

    ![게시 대상 선택](../deployment/media/quickstart-publish-iis.png "IIS, FTP 등을 선택합니다.")

1. 배포 방법으로 **웹 배포** 를 선택합니다. 웹 배포는 IIS 서버에 웹 애플리케이션 및 웹 사이트의 배포를 간소화하고, 서버에서 애플리케이션으로 설치되어야 합니다. [웹 플랫폼 설치 관리자](https://www.microsoft.com/web/downloads/platform.aspx)를 사용하여 설치합니다.

    ![배포 방법 선택](../deployment/media/quickstart-publish-iis-web-deploy.png "IIS, FTP 등을 선택합니다.")

1. 게시 방법의 필수 설정을 구성하고 **마침** 을 선택합니다. 

    ![웹 배포 연결 정보](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. 게시하려면 요약 페이지에서 **게시** 를 선택합니다. 출력 창은 배포 진행률 및 결과를 표시합니다.

   IIS의 ASP.NET Core 문제 해결에 관한 도움이 필요하면 [Azure App Service 및 IIS의 ASP.NET Core 문제 해결](/aspnet/core/test/troubleshoot-azure-iis)을 참조하세요.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Visual Studio를 사용하여 게시 프로필을 만드는 방법을 알아보았습니다. 게시 설정을 가져와서 게시 프로필을 구성할 수도 있습니다.

> [!div class="nextstepaction"]
> [게시 설정 가져오기 및 IIS에 배포](tutorial-import-publish-settings-iis.md)
