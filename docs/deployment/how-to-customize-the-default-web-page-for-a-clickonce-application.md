---
title: ClickOnce 응용 프로그램의 기본 웹 페이지 사용자 지정
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ee4c1211840f17afe371961dea644372cd63efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382473"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 기본 웹 페이지 사용자 지정
ClickOnce 응용 프로그램을 웹에 게시 하면 웹 페이지가 자동으로 생성 되어 응용 프로그램과 함께 게시 됩니다. 기본 페이지에는 응용 프로그램의 이름 및 응용 프로그램을 설치 하 고, 필수 구성 요소를 설치 하거나, MSDN에서 도움말에 액세스 하는 링크가 포함 되어 있습니다.

> [!NOTE]
> 페이지에 표시 되는 실제 링크는 페이지가 표시 되는 컴퓨터와 포함 된 필수 구성 요소에 따라 달라 집니다.

 웹 페이지의 기본 이름은 *Publish.htm*입니다. **프로젝트 디자이너**에서 이름을 변경할 수 있습니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램의 게시 페이지 지정](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)을 참조 하세요.

 *Publish.htm* 웹 페이지는 최신 버전이 검색 된 경우에만 게시 됩니다.

> [!NOTE]
> **게시** 설정에 대 한 변경 내용은 *Publish.htm* 페이지에 영향을 주지 않습니다. 단, 처음 게시 한 후 필수 구성 요소를 추가 하거나 제거 하면 필수 구성 요소 목록이 더 이상 정확 하지 않게 됩니다. 변경 내용을 반영 하려면 필수 조건 링크의 텍스트를 편집 해야 합니다.

### <a name="to-customize-the-publish-web-page"></a>게시 웹 페이지를 사용자 지정 하려면

1. ClickOnce 응용 프로그램을 웹 위치에 게시 합니다. 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조 하세요.

2. 웹 서버에서 Visual Web Designer 또는 다른 HTML 편집기에서 *Publish.htm* 파일을 엽니다.

3. 원하는 대로 페이지를 사용자 지정 하 고 저장 합니다.

4. 선택 사항입니다. Visual Studio에서 사용자 지정 게시 웹 페이지를 덮어쓰지 않도록 하려면 게시 **옵션** 대화 상자에서 **모든 게시 후 자동으로 배포 웹 페이지 생성** 을 선택 취소 합니다.

## <a name="see-also"></a>참조
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)
- [방법: ClickOnce 애플리케이션을 사용하여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [방법: ClickOnce 애플리케이션의 게시 페이지 지정](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)