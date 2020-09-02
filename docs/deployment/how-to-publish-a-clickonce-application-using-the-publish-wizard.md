---
title: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518252ac24dc45036587de114f68cd0a77b8c5b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382304"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시
ClickOnce 애플리케이션을 사용자에게 제공하려면 파일 공유나 경로, FTP 서버 또는 이동식 미디어에 해당 애플리케이션을 게시해야 합니다. 게시 마법사를 사용하여 애플리케이션을 게시할 수 있습니다. 게시와 관련된 추가 속성은 **프로젝트 디자이너**의 **게시** 페이지에서 사용 가능합니다. 자세한 내용은 [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)를 참조하세요.

게시 마법사를 실행하기 전에 게시 속성을 적절하게 설정해야 합니다. 예를 들어 ClickOnce 애플리케이션에 서명을 하기 위한 키는 **프로젝트 디자이너**의 **서명** 페이지에서 지정할 수 있습니다. 자세한 내용은 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)을 참조 하세요.

> [!NOTE]
> ClickOnce를 사용하여 애플리케이션 버전을 둘 이상 설치하면 이전 애플리케이션 버전이 지정한 게시 위치의 *Archive* 폴더로 이동합니다. 이러한 방식으로 이전 버전이 보관되므로 설치 디렉터리에 이전 버전의 폴더가 남지 않습니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 실제 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 클릭합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="to-publish-to-a-file-share-or-path"></a>파일 공유나 경로에 게시하려면

1. **솔루션 탐색기**에서 애플리케이션 프로젝트를 선택합니다.

2. **빌드** 메뉴에서 *Projectname* **게시** 를 클릭 합니다.

    게시 마법사가 나타납니다.

3. **애플리케이션을 게시할 위치** 페이지에 아래 형식 중 하나를 사용하여 올바른 FTP 주소나 올바른 파일 경로를 입력한 후, **다음**을 클릭합니다.

4. **애플리케이션 설치 방법** 페이지에서 사용자가 애플리케이션을 설치하기 위해 이동할 위치를 선택합니다.

   - 웹 사이트에서 설치하는 경우 **웹 사이트에서**를 클릭하고 이전 단계에서 입력한 파일 경로에 해당하는 URL을 입력합니다. **다음**을 클릭합니다. 이 옵션은 일반적으로 FTP 주소를 게시 위치로 지정하는 경우에 사용됩니다. FTP에서 직접 다운로드할 수는 없습니다. 따라서 여기에 URL을 입력해야 합니다.

   - 파일 공유에서 애플리케이션을 직접 설치하는 경우에는 **UNC 경로 또는 파일 공유에서**를 클릭한 후, **다음**을 클릭합니다. (이 옵션은 *c:\deploy\myapp* 또는 *\\\server\myapp* 형식의 게시 위치용입니다.)

   - 이동식 미디어에서 설치하는 경우에는 **CD-ROM 또는 DVD-ROM에서**를 클릭한 후, **다음**을 클릭합니다.

5. **애플리케이션을 오프라인으로 사용할 수 있는지 여부** 페이지에서 적절한 옵션을 클릭합니다.

   - 사용자의 네트워크 연결이 끊어져도 애플리케이션을 실행할 수 있도록 설정하려면 **예, 이 애플리케이션을 온라인 또는 오프라인으로 사용할 수 있습니다.** 를 클릭합니다. **시작** 메뉴의 바로 가기가 애플리케이션용으로 만들어집니다.

   - 게시 위치에서 애플리케이션을 직접 실행하려면 **아니요, 이 애플리케이션은 온라인으로만 사용할 수 있습니다.** 를 클릭합니다. **시작** 메뉴에 바로 가기가 만들어지지 않습니다.

     **다음**을 클릭하여 계속합니다.

6. **마침**을 클릭하여 애플리케이션을 게시합니다.

    게시 상태가 상태 알림 영역에 표시됩니다.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>CD-ROM 또는 DVD-ROM에 게시하려면

1. **솔루션 탐색기**에서 애플리케이션 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

    **프로젝트 디자이너가** 나타납니다.

2. **게시** 탭을 클릭하여 **프로젝트 디자이너**에서 **게시** 페이지를 열고 **게시 마법사** 단추를 클릭합니다.

    게시 마법사가 나타납니다.

3. **애플리케이션을 게시할 위치** 페이지에 애플리케이션을 게시할 파일 경로나 FTP 위치를 *d:\deploy*와 같이 입력합니다. 그리고 **다음**을 클릭하여 계속합니다.

4. **애플리케이션 설치 방법** 페이지에서 **CD-ROM 또는 DVD-ROM에서**를 클릭한 후, **다음**을 클릭합니다.

   > [!NOTE]
   > 드라이브에 CD-ROM 삽입 시 설치가 자동으로 실행되도록 하려면 **프로젝트 디자이너**에서 **게시** 페이지를 열고 **옵션** 단추를 클릭한 다음, **게시 옵션** 마법사에서 **CD 설치에서 CD를 삽입하면 자동으로 설치 시작**을 선택합니다.

5. CD-ROM으로 애플리케이션을 배포하는 경우 웹 사이트에서 업데이트를 제공할 수 있습니다. **애플리케이션이 업데이트를 확인할 위치** 페이지에서 업데이트 옵션을 선택합니다.

   - 애플리케이션이 업데이트를 확인하도록 하려면 **애플리케이션이 업데이트를 확인할 위치**를 클릭하고 업데이트를 게시할 위치를 입력합니다. 이 위치는 파일 위치, 웹 사이트 또는 FTP 서버일 수 있습니다.

   - 애플리케이션이 업데이트를 확인하지 않도록 하려면 **애플리케이션이 업데이트를 확인하지 않음**을 클릭합니다.

     **다음**을 클릭하여 계속합니다.

6. **마침**을 클릭하여 애플리케이션을 게시합니다.

    게시 상태가 상태 알림 영역에 표시됩니다.

   > [!NOTE]
   > 게시가 완료되면 CD 재작성기 또는 DVD 재작성기를 사용하여 3단계에서 지정한 위치에서 CD-ROM 또는 DVD-ROM 미디어로 파일을 복사합니다.

## <a name="see-also"></a>참조

- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)