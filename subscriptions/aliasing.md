---
title: 별칭을 사용하여 Visual Studio 구독에 로그인하지 못할 수 있음 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: 별칭 또는 대화명을 사용하는 경우 로그인에 실패할 수 있습니다.
ms.openlocfilehash: 1b6c465bc3e850d8582abde200ac9e5bd995e431
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87234642"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>별칭을 사용하여 Visual Studio 구독에 로그인하지 못할 수 있음
로그인에 사용되는 계정 유형에 따라 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)에 로그인할 때 사용 가능한 구독이 제대로 표시되지 않을 수 있습니다. 한 가지 원인은 구독이 할당된 로그인 ID 대신 “별칭” 또는 “이름”을 사용하기 때문일 수 있습니다. 이것을 “별칭 지정”이라고 합니다.

## <a name="what-is-aliasing"></a>별칭 지정이란 무엇인가요?
“별칭 지정”이라는 용어는 사용자가 Windows(또는 Active Directory)에 로그인하고 전자 메일에 액세스하기 위해 서로 다른 ID를 사용하는 것을 나타냅니다.

회사에 디렉터리 로그인용 Microsoft Online Service가 있지만(예: JohnD@contoso.com) 사용자가 별칭 또는 이름(예: John.Doe@contoso.com)을 사용하여 전자 메일 계정에 액세스할 경우 별칭 지정이 수행됩니다. 사용자가 https://manage.visualstudio.com 의 관리 포털에 나열된 “로그인 전자 메일 주소”를 사용하여 구독에 액세스하는지 확인합니다. 

## <a name="what-are-the-potential-issues"></a>잠재적인 이슈는 무엇인가요?

구독자의 계정 유형에 따라 두 가지 이슈 중 하나가 발생할 수 있습니다. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>회사 또는 학교 계정 UPN 불일치 이슈 
회사에 UPN(UserPrincipalName)이 기본 SMTP 주소와 동일하지 않은 Active Directory 설정이 있는 경우 UPN 불일치가 발생할 수 있습니다. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>로그인 주소가 UPN 불일치의 영향을 받는지 여부를 검색하는 방법 

1. 구독 할당 전자 메일에 포함된 로그인 주소를 사용하여 https://my.visualstudio.com/subscriptions 에 로그인합니다.

2. 페이지의 오른쪽 위에 나열된 로그인 전자 메일 주소가 로그인에 사용한 주소와 일치하는지 확인합니다.  일치하지 않으면 UPN이 불일치하는 것이며 구독을 볼 수 없습니다. 

> [!div class="mx-imgBorder"]
> ![로그인 전자 메일 주소](_img//aliasing/sign-in-email.png "오른쪽 위에 표시되는 전자 메일 주소가 로그인에 사용하는 주소와 일치해야 합니다.")

#### <a name="how-to-fix-a-upn-mismatch"></a>UPN 불일치 해결 방법

1. Visual Studio 운영 관리 포털 [https://manage.visualstudio.com](https://manage.visualstudio.com)에 액세스 

2. UPN 불일치 이슈가 있는 구독자 찾기 ([필터](search-license.md) 기능을 사용하면 구독자를 쉽게 찾을 수 있습니다.)

3. 로그인 전자 메일 주소를 구독자의 UPN으로 변경 

0. 변경 내용 저장 

0. 구독자에게 구독자 포털에서 로그아웃하고 UPN을 사용하여 다시 액세스하라고 알림 

### <a name="personal-account-aliasing-issue"></a>개인 계정 별칭 이슈

Visual Studio 구독 포털에 로그인하는 데 사용된 전자 메일 주소가 구독과 연결된 전자 메일 주소와 일치하지 않는 경우 개인 구독 계정에도 이슈가 발생할 수 있습니다. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>개인 구독 계정이 별칭 이슈에 영향을 받는지 여부를 검색하는 방법

1. [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)에 로그인합니다.

0. 페이지의 오른쪽 위에 나열된 로그인 전자 메일 주소가 로그인에 사용한 주소와 일치하는지 확인합니다.  로그인한 전자 메일 주소가 웹 사이트에 액세스하는 데 사용된 전자 메일 주소와 동일하지 않으면 계정과 별칭이 충돌합니다.

#### <a name="how-to-fix-an-alias-issue"></a>별칭 이슈 해결 방법

Visual Studio 플랫폼은 기본 별칭의 우선 순위를 지정하여 구독 세부 정보를 표시합니다. 

1. **Microsoft에 로그인하는 방법 관리**로 이동합니다. 메시지가 표시되면 Microsoft 계정에 로그인합니다. 

2. 계정 별칭에서 구독을 할당하는 데 사용된 전자 메일 주소 옆에 있는 **기본 별칭으로 지정**을 선택합니다. 

> [!div class="mx-imgBorder"]
> ![기본 전자 메일 주소 설정](_img//aliasing/account-aliases.png "기본 항목으로 만들기 링크를 사용하여 구독의 기본 별칭을 선택합니다.")

3. Visual Studio 구독 포털(https://my.visualstudio.com) )에서 로그아웃 

4. 구독을 할당하는 데 사용된 계정(지금은 기본 별칭으로 구성되어야 함)을 사용하여 다시 로그인합니다. 

## <a name="preventing-aliasing-issues"></a>별칭 이슈 방지

관리자는 구독자가 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)에 성공적으로 로그인했는지 확인하는 두 가지 옵션이 있습니다.
- 첫 번째 옵션(권장)은 디렉터리 계정을 https://my.visualstudio.com 의 Visual Studio 구독 포털 로그인으로 사용하는 것입니다.  
- 두 번째 옵션(덜 안전함)은 구독자가 디렉터리 전자 메일 주소와 다른 전자 메일 주소를 사용하여 로그인할 수 있도록 하는 것입니다.

이 두 옵션 모두 다음 단계를 완료하여 관리 포털에서 구성됩니다.  
1. [https://manage.visualstudio.com](https://manage.visualstudio.com)에 로그인 

0. 단일 사용자를 변경하는 경우 테이블에서 해당 사용자를 선택하고 마우스 오른쪽 단추를 클릭하여 편집합니다. 그러면 로그인 전자 메일 주소를 수정할 수 있는 패널이 열립니다. 로그인 전자 메일 주소 필드에서 필요한 업데이트를 수행합니다. 저장을 클릭하면 변경 내용이 적용됩니다.  

0. 대규모 사용자에게 해당 변경을 수행해야 하는 경우 일괄 편집 기능을 사용하면 됩니다. 자세한 내용은 [일괄 편집을 사용하여 여러 구독자 편집](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) 문서를 참조하세요.

> [!NOTE]
> 개별 및 일괄 변경 모두 구독자는 로그인 전자 메일 주소가 변경되었으며 업데이트된 전자 메일 주소를 사용하여 로그인해야 한다는 지침이 포함된 전자 메일을 받게 됩니다. 구독자가 이전에 다른 로그인 주소에서 혜택을 활성화한 경우에는 다른 로그인 주소를 계속 사용하여 액세스해야 합니다.  

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>다음 단계
Visual Studio 구독 관리에 대해 자세히 알아보세요.
- [개별 구독 할당](assign-license.md)
- [여러 구독 할당](assign-license-bulk.md)
- [구독 편집](edit-license.md)
- [최대 사용량 확인](maximum-usage.md)


