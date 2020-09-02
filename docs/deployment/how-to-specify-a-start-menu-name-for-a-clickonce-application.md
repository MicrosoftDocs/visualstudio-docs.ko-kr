---
title: 방법-ClickOnce 응용 프로그램의 시작 메뉴 이름 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 882d6f7471530a101404040368dbc6088e9b5d96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381927"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 시작 메뉴 이름 지정
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]온라인 및 오프 라인 사용을 위해 응용 프로그램을 설치 하는 경우 **시작** 메뉴와 **프로그램 추가/제거** 목록에 항목이 추가 됩니다. 기본적으로 표시 이름은 응용 프로그램 어셈블리의 이름과 같지만 **게시 옵션** 대화 상자에서 **제품 이름** 을 설정 하 여 표시 이름을 변경할 수 있습니다.

 **제품 이름이** *publish.htm* 페이지에 표시 됩니다. 설치 된 오프 라인 응용 프로그램의 경우 **시작** 메뉴의 항목 이름이 되 고 **프로그램 추가/제거**에 표시 되는 이름이 됩니다.

 **게시자 이름은** *publish.htm* 페이지의 **제품 이름**위에 표시 되 고, 설치 된 오프 라인 응용 프로그램의 경우 **시작** 메뉴에 응용 프로그램 아이콘을 포함 하는 폴더의 이름으로도 표시 됩니다.

 시작 메뉴 바로 가기 또는 앱 참조가 *%Appdata%\Microsoft\Windows\Start Menu\Programs \\<게시자 이름 \> *에 생성 됩니다. 바로 가기 또는 앱 참조의 이름이 제품 이름과 동일 합니다.

 **프로젝트 디자이너**의 **게시** 페이지에서 사용할 수 있는 **게시 옵션** 대화 상자에서 **제품 이름** 및 **게시자 이름** 속성을 설정할 수 있습니다.

### <a name="to-specify-a-start-menu-name"></a>시작 메뉴 이름을 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **옵션** 단추를 클릭 하 여 **게시 옵션** 대화 상자를 엽니다.

4. **설명**을 클릭 합니다.

5. **게시 옵션** 대화 상자에서 **제품 이름**에 표시할 이름을 입력 합니다.

6. 필요에 따라 게시자 **이름**에 게시자 이름을 입력할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)