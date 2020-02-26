---
title: 별칭을 사용하여 Visual Studio 구독에 로그인하지 못할 수 있음 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: 별칭 또는 대화명을 사용하는 경우 로그인에 실패할 수 있습니다.
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276626"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>별칭을 사용하여 Visual Studio 구독에 로그인하지 못할 수 있음
로그인에 사용되는 계정 유형에 따라 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)에 로그인할 때 사용 가능한 구독이 제대로 표시되지 않을 수 있습니다. 한 가지 원인은 구독이 할당된 로그인 ID 대신 “별칭” 또는 “이름”을 사용하기 때문일 수 있습니다. 이것을 “별칭 지정”이라고 합니다.

## <a name="what-is-aliasing"></a>별칭 지정이란 무엇인가요?
“별칭 지정”이라는 용어는 사용자가 Windows(또는 Active Directory)에 로그인하고 전자 메일에 액세스하기 위해 서로 다른 ID를 사용하는 것을 나타냅니다.

회사에 디렉터리 로그인용 Microsoft Online Service가 있지만(예: olivia@contoso.com) 사용자가 별칭 또는 이름(예: OliviaG@contoso.com)을 사용하여 전자 메일 계정에 액세스할 경우 별칭 지정이 수행됩니다. 사용자가 https://manage.visualstudio.com 의 Visual Studio 구독 관리 포털에 나열된 “로그인 전자 메일 주소”로 로그인하여 구독에 액세스했는지 확인합니다.

## <a name="as-an-administrator-what-options-do-i-have"></a>관리자로서 어떤 옵션이 있나요?

구독자의 계정 유형에 따라 해당하는 솔루션을 아래에서 찾습니다.

### <a name="work-or-school-account-upn-mismatch-issue"></a>회사 또는 학교 계정 UPN 불일치 이슈

UPN(사용자 계정 이름)이 기본 SMTP 주소와 동일하지 않은 회사에 Active Directory가 설정된 경우 UPN 불일치 이슈가 발생할 수 있습니다. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>사용자의 로그인 주소에 UPN 불일치가 있는지 탐지하는 방법

사용자가 다음 단계를 완료하도록 합니다.

1. 구독 할당 전자 메일에 포함된 로그인 주소를 사용하여 https://my.visualstudio.com 에 로그인합니다.  

    > [!NOTE]
    > 구독 할당 전자 메일이 없는 경우 관리 포털 내에서 다시 보낼 수 있습니다.  

2. **구독** 탭을 클릭합니다.
3. “로그인했습니다...”라고 표시된 오른쪽 상단의 전자 메일 주소가 구독 할당 전자 메일의 로그인 전자 메일 주소와 동일한지 확인합니다.  동일하지 않으면 구독 혜택에 액세스할 수 없게 됩니다. 

   > [!div class="mx-imgBorder"]
   > ![구독 페이지](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>UPN 불일치를 해결하는 방법

1. https://manage.visualstudio.com 의 Visual Studio 관리 관리 포털에 액세스 

2. UPN 불일치 이슈가 있는 사용자를 찾습니다.  구독이 많은 경우 [필터](search-license.md) 기능을 사용하면 이 작업을 더욱 쉽게 수행할 수 있습니다. 

3. 로그인 전자 메일 주소를 사용자의 UPN으로 변경합니다.

4. 변경 내용 저장 

5. 사용자에게 구독자 포털에서 로그아웃하고 UPN을 사용하여 다시 로그인하도록 요청합니다.   

### <a name="personal-account-aliasing-issue"></a>개인 계정 별칭 이슈

별칭 이슈는 개인 계정에도 영향을 줄 수 있습니다. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>개인 계정에 별칭 이슈가 있는지 탐지하는 방법

1. https://my.visualstudio.com 에 로그인합니다.

2. **구독** 탭을 클릭하고 로그인한 주소를 확인합니다. 

3. 로그인한 전자 메일 주소가 웹 사이트에 액세스하는 데 사용된 전자 메일 주소와 동일하지 않으면 계정과 별칭이 충돌합니다. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>개인 계정 별칭 이슈를 해결하는 방법

Visual Studio 구독 플랫폼은 기본 별칭의 우선 순위를 지정하여 구독 세부 정보를 표시합니다.  이 이슈를 해결하려면 로그인 시 다른 전자 메일 별칭을 기본 별칭으로 설정해야 합니다. 

1. [Microsoft에 로그인하는 방법 관리](https://go.microsoft.com/fwlink/p/?linkid=842796)로 이동합니다.
2. 메시지가 표시되면 Microsoft 계정에 로그인합니다. 
3. 계정 별칭에서 구독을 할당하는 데 사용된 전자 메일 주소 옆에 있는 **기본 별칭으로 지정**을 선택합니다. 
4. 계정 별칭에서 구독을 할당하는 데 사용된 전자 메일 주소 옆에 있는 기본 별칭으로 지정을 선택합니다. 
5. Visual Studio 구독자 포털(https://my.visualstudio.com) 로그아웃 
6. 새 기본 별칭을 사용하여 포털에 다시 액세스합니다. 

### <a name="ensure-a-successful-experience-for-your-users"></a>사용자에게 성공적인 환경 보장

관리자는 구독자가 https://my.visualstudio.com 에 성공적으로 로그인했는지 확인하는 두 가지 옵션이 있습니다. 

- 첫 번째 옵션(권장)은 https://manage.visualstudio.com 의 로그인 주소로 디렉터리 계정을 사용하는 것입니다.
- 덜 안전한 두 번째 옵션은 구독자가 디렉터리 전자 메일 주소와 다른 전자 메일 주소를 사용하여 로그인할 수 있도록 하는 것입니다.

두 옵션은 모두 다음 단계를 완료하여 관리 포털에서 구성됩니다.

1. https://manage.visualstudio.com 에 로그인 

2. 단일 사용자를 변경하는 경우 테이블에서 해당 사용자를 선택하고 마우스 오른쪽 단추를 클릭하여 편집합니다. 그러면 로그인 전자 메일 주소를 수정할 수 있는 패널이 열립니다.  

3. 로그인 전자 메일 주소 필드에서 필요한 업데이트를 수행합니다. 

4. 저장을 클릭하면 변경 내용이 적용됩니다.  
대규모 사용자에게 해당 변경을 수행해야 하는 경우 일괄 편집 기능을 사용하면 됩니다. 해당 프로세스에 대한 자세한 내용은 [구독 편집](edit-license.md) 문서의 **일괄 편집을 사용하여 여러 구독자 편집** 섹션을 참조하세요.  

## <a name="next-steps"></a>다음 단계
Visual Studio 구독 관리에 대해 자세히 알아보세요.
- [개별 구독 할당](assign-license.md)
- [여러 구독 할당](assign-license-bulk.md)
- [구독 편집](edit-license.md)
- [구독 삭제](delete-license.md)
- [최대 사용량 확인](maximum-usage.md)

## <a name="see-also"></a>참조
- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)
