---
title: ClickOnce 게시 버전을 설정 합니다. | Microsoft Docs
description: 응용 프로그램이 업데이트 인지 여부를 확인 하는 ClickOnce 게시 버전 속성을 설정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 100c3cd12a3011d35445ac885333802e28b4a92f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349791"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>방법: ClickOnce 게시 버전 설정
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` 속성은 게시 중인 응용 프로그램을 업데이트로 처리할지 여부를 결정 합니다. 각 시간 버전이 증가 하면 응용 프로그램이 업데이트로 게시 됩니다.

 `Publish Version`속성은 **프로젝트 디자이너** 의 **게시** 페이지에서 설정할 수 있습니다.

> [!NOTE]
> 응용 프로그램이 게시 될 때마다 속성이 자동으로 증가 하는 프로젝트 옵션이 있습니다 `Publish Version` .이 옵션은 기본적으로 사용 하도록 설정 되어 있습니다. 자세한 내용은 [방법: ClickOnce 게시 버전 자동 증가](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)를 참조 하세요.

### <a name="to-change-the-publish-version"></a>게시 버전을 변경 하려면

1. **솔루션 탐색기** 에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴의 **속성** 을 클릭 합니다.

2. **게시** 탭을 클릭합니다.

3. **게시 버전** 필드에서 **주** 버전, **부** 버전, **빌드** 버전 또는 **수정** 버전 번호를 늘립니다.

    > [!NOTE]
    > 버전 번호는 감소 해서는 안 됩니다. 이렇게 하면 예기치 않은 업데이트 동작이 발생할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)
- [방법: ClickOnce 게시 버전 자동 증가](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)