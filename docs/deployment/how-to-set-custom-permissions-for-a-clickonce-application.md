---
title: 사용자 지정 권한 설정 (ClickOnce 앱)
description: 기본 권한을 사용 하는 ClickOnce 응용 프로그램을 배포 하거나 응용 프로그램에 필요한 특정 사용 권한에 대 한 사용자 지정 영역을 만드는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5d0348b882a3327c02fca6db0628822c0deffeb
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351000"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 사용자 지정 권한 설정
인터넷 또는 로컬 인트라넷 영역에 대한 기본 권한을 사용하는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션을 배포할 수 있습니다. 또는 애플리케이션에 필요한 특정 사용 권한에 대한 사용자 지정 영역을 만들 수 있습니다. 이렇게 하려면 **프로젝트 디자이너** 의 **보안** 페이지에서 보안 권한을 사용자 지정할 수 있습니다.

### <a name="to-customize-a-permission"></a>사용 권한을 사용자 지정하려면

1. **솔루션 탐색기** 에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성** 을 클릭합니다.

2. **보안** 탭을 클릭합니다.

3. **ClickOnce 보안 설정 사용** 확인란을 선택합니다.

4. **부분 신뢰 애플리케이션** 옵션 단추를 선택합니다.

     **ClickOnce 보안 권한** 섹션의 컨트롤이 사용됩니다.

5. **설치할 애플리케이션을 가져올 영역** 드롭다운 목록에서 **(사용자 지정)** 을 클릭합니다.

6. **권한 XML 편집** 을 클릭합니다.

     XML 편집기에서 *app.manifest* 파일이 열립니다.

7. 애플리케이션에 필요한 사용 권한에 대한 XML 코드를 `</applicationRequestMinimum>` 요소 앞에 추가합니다.

    > [!NOTE]
    > 사용 권한 집합의 `ToXml` 메서드를 사용하여 애플리케이션 매니페스트용 XML 코드를 생성할 수 있습니다. 예를 들어 <xref:System.Security.Permissions.EnvironmentPermission> 사용 권한 집합용 XML을 생성하려면 <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> 메서드를 호출합니다.

## <a name="see-also"></a>참고 항목
- [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)
