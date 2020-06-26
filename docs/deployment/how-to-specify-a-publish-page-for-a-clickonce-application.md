---
title: 방법-ClickOnce 응용 프로그램의 게시 페이지 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf7178a6b5456d048421533b8497682d69c2ee0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381966"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 게시 페이지 지정
응용 프로그램을 게시할 때 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 기본 웹 페이지 (publish.htm)가 생성 되어 응용 프로그램과 함께 게시 됩니다. 이 페이지에는 응용 프로그램의 이름, 응용 프로그램을 설치 하는 링크 및/또는 모든 필수 구성 요소 및 설명 하는 도움말 항목에 대 한 링크가 포함 되어 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 있습니다. 프로젝트의 **게시 페이지** 속성을 사용 하 여 응용 프로그램에 대 한 웹 페이지의 이름을 지정할 수 있습니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 게시 페이지를 지정 하면 다음에 게시할 때 게시 위치에 복사 됩니다. 다시 게시 하는 경우 덮어쓰지 않습니다. 페이지의 모양을 사용자 지정 하려는 경우 변경 내용을 잃지 걱정 하지 않고이 작업을 수행할 수 있습니다. 자세한 내용은 [방법: ClickOnce 기본 웹 페이지 사용자 지정](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)을 참조 하세요.

 게시 **페이지** 속성은 **프로젝트 디자이너**의 **게시** 창에서 액세스할 수 있는 **게시 옵션** 대화 상자에서 설정할 수 있습니다.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>ClickOnce 응용 프로그램에 대 한 사용자 지정 웹 페이지를 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴의 **속성**을 클릭 합니다.

2. **게시** 창을 선택 합니다.

3. **옵션** 단추를 클릭 하 여 **게시 옵션** 대화 상자를 엽니다.

4. **배포**를 클릭합니다.

5. **게시 옵션** 대화 상자에서 **게시 후 배포 웹 페이지 열기** 확인란을 선택 했는지 확인 합니다 (기본적으로 선택 되어 있어야 함).

6. **배포 웹 페이지** 상자에서 웹 페이지의 이름을 입력 하 고 **확인**을 클릭 합니다.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>게시할 때마다 게시 페이지가 시작 되지 않도록 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴의 **속성**을 클릭 합니다.

2. **게시** 창을 선택 합니다.

3. **옵션** 단추를 클릭 하 여 **게시 옵션** 대화 상자를 엽니다.

4. **배포**를 클릭합니다.

5. **게시 옵션** 대화 상자에서 **게시 후 배포 웹 페이지 열기** 확인란의 선택을 취소 합니다.

## <a name="see-also"></a>추가 정보
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [방법: ClickOnce 기본 웹 페이지 사용자 지정](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)