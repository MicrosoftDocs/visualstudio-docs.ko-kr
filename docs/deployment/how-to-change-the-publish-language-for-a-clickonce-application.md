---
title: ClickOnce 응용 프로그램의 게시 언어 변경
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0252cf39f8f5ee268adbf625f03a9b5a305b903a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382590"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 게시 언어 변경

응용 프로그램을 게시할 때 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 설치 중에 표시 되는 사용자 인터페이스는 개발 컴퓨터의 언어 및 문화권으로 기본 설정 됩니다. 지역화 된 응용 프로그램을 게시 하는 경우 언어와 문화권을 지역화 된 버전과 일치 하도록 지정 해야 합니다. 이는 프로젝트의 속성에 의해 결정 됩니다 `Publish language` .

`Publish language`속성은 **프로젝트 디자이너**의 **게시** 페이지에서 액세스할 수 있는 **게시 옵션** 대화 상자에서 설정할 수 있습니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="to-change-the-publish-language"></a>게시 언어를 변경 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **옵션** 단추를 클릭 하 여 **게시 옵션** 대화 상자를 엽니다.

4. **설명**을 클릭 합니다.

5. **게시 옵션** 대화 상자의 **게시 언어** 드롭다운 목록에서 언어 및 문화권을 선택 하 고 **확인**을 클릭 합니다.

## <a name="see-also"></a>추가 정보

- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)