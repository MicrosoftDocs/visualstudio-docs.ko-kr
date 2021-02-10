---
title: ClickOnce 게시 버전 자동 증가
description: Visual Studio를 사용 하 여 ClickOnce 응용 프로그램에 대 한 수정 번호의 자동 증가를 사용 하지 않도록 설정 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947777"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>방법: ClickOnce 게시 버전 자동 증가

응용 프로그램을 게시할 때 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 속성을 변경 하면 `Publish Version` 응용 프로그램이 업데이트로 게시 됩니다. 기본적으로 Visual Studio는 `Revision` 응용 프로그램을 게시할 때마다의 수를 자동으로 증가 시킵니다 `Publish Version` .

**프로젝트 디자이너** 의 **게시** 페이지에서이 동작을 사용 하지 않도록 설정할 수 있습니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>게시 버전 자동 증가를 사용 하지 않도록 설정 하려면

1. **솔루션 탐색기** 에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성** 을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **게시 버전** 섹션에서 **릴리스할 때마다 자동으로 수정 번호 증가** 확인란의 선택을 취소 합니다.

## <a name="see-also"></a>참고 항목

- [방법: ClickOnce 게시 버전 설정](../deployment/how-to-set-the-clickonce-publish-version.md)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)