---
title: 오프 라인 또는 온라인 설치 모드 지정 (ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 896d2218237b884d9483496e0adac157a6e26fd3
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808739"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>방법: ClickOnce 오프라인 또는 온라인 설치 모드 지정
`Install Mode`응용 프로그램에 대 한는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 오프 라인으로 사용할 수 있는지 아니면 온라인에서 사용할 수 있는지 결정 합니다. **응용 프로그램을 온라인 으로만 사용할 수 있도록**선택 하는 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 실행 하려면 사용자가 게시 위치 (웹 페이지 또는 파일 공유)에 대 한 액세스 권한이 있어야 합니다. **응용 프로그램을 오프 라인으로도 사용할 수**있는 경우 응용 프로그램은 **시작** 메뉴 및 **프로그램 추가/제거** 대화 상자에 항목을 추가 합니다. 사용자는 연결 되지 않은 응용 프로그램을 실행할 수 있습니다.

`Install Mode` **프로젝트 디자이너**의 **게시** 페이지에서를 설정할 수 있습니다.

> [!NOTE]
> `Install Mode`게시 마법사를 사용 하 여를 설정할 수도 있습니다. 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조 하세요.

### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce 응용 프로그램을 온라인 으로만 사용할 수 있도록 설정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **설치 모드 및 설정** 영역에서 **응용 프로그램을 온라인 으로만 사용 가능** 옵션 단추를 클릭 합니다.

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>ClickOnce 응용 프로그램을 온라인 또는 오프 라인으로 사용 하도록 설정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **설치 모드 및 설정** 영역에서 **응용 프로그램을 오프 라인으로 사용 가능** 옵션 단추를 클릭 합니다.

     응용 프로그램이 설치 되 면 **시작** 메뉴에 항목을 추가 하 고 제어판에서 **프로그램을 추가 하거나 제거** 합니다.

## <a name="see-also"></a>추가 정보
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)