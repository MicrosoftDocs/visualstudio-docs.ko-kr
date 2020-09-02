---
title: 방법-ClickOnce 응용 프로그램의 보안 영역 설정 Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51515339c24ea8a0507c47d0399cde9e423f71a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382135"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 보안 영역 설정
ClickOnce 애플리케이션에 대한 코드 액세스 보안 권한을 설정할 때에는 **프로젝트 디자이너** 의 **보안**페이지에서 기본 권한 집합으로 시작해야 합니다.

 대부분의 경우, 제한된 권한 집합을 포함하는 **인터넷** 영역 또는 더 큰 권한 집합을 포함하는 **로컬 인트라넷** 영역을 선택할 수 있습니다. 애플리케이션에 사용자 지정 권한이 필요한 경우 **사용자 지정** 보안 영역을 선택하여 설정할 수 있습니다. 사용자 지정 권한을 설정하는 방법에 대한 자세한 내용은 [방법: ClickOnce 애플리케이션의 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)을 참조하세요.

### <a name="to-set-a-security-zone"></a>보안 영역을 설정하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴의 **속성**을 클릭 합니다.

2. **보안** 탭을 클릭합니다.

3. **ClickOnce 보안 설정 사용** 확인란을 선택합니다.

4. **부분 신뢰 애플리케이션** 옵션 단추를 선택합니다.

     **ClickOnce 보안 권한** 섹션의 컨트롤이 사용됩니다.

5. **설치할 애플리케이션을 가져올 영역** 드롭다운 목록에서 보안 영역을 선택합니다.

## <a name="see-also"></a>추가 정보
- [방법: ClickOnce 응용 프로그램에 대 한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)
