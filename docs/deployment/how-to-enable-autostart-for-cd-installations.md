---
title: CD 설치를 위한 자동 시작 사용 | Microsoft Docs
description: CD-ROM 또는 DVD-ROM과 같은 이동식 미디어를 통해 ClickOnce 응용 프로그램을 배포할 때 자동 시작을 사용 하도록 설정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6ed3df72b98454c4669e7d9bcd21c0612a6fef3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349960"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>방법: CD 설치를 위한 자동 시작 사용
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Cd-rom 또는 dvd-rom과 같은 이동식 미디어를 사용 하 여 응용 프로그램을 배포할 때 `AutoStart` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 미디어가 삽입 될 때 응용 프로그램이 자동으로 실행 되도록를 사용 하도록 설정할 수 있습니다.

 `AutoStart`**프로젝트 디자이너** 의 **게시** 페이지에서 사용 하도록 설정할 수 있습니다.

### <a name="to-enable-autostart"></a>자동 시작을 사용 하도록 설정 하려면

1. **솔루션 탐색기** 에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴의 **속성** 을 클릭 합니다.

2. **게시** 탭을 클릭합니다.

3. **옵션** 단추를 클릭합니다.

     **게시 옵션** 대화 상자가 나타납니다.

4. **배포** 를 클릭합니다.

5. Cd **설치의 경우 cd를 삽입 하면 자동으로 설치 시작 확인란을** 선택 합니다.

     응용 프로그램이 게시 될 때 *자동 실행 .inf* 파일이 게시 위치로 복사 됩니다.

## <a name="see-also"></a>참고 항목
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)