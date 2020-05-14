---
title: Visual Studio 구독에 로그인할 때의 문제 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 03/11/2020
ms.topic: conceptual
description: Visual Studio 구독에 로그인할 때 발생할 수 있는 문제에 대해 알아보기
ms.openlocfilehash: de27f64f1d5c83ed01a1e561f4921dbed53c479c
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233236"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Visual Studio 구독에 로그인할 때의 문제
Visual Studio 구독을 사용하려면 먼저 로그인해야 합니다.  구독에 따라 Microsoft 계정(MSA) 또는 AAD(Azure Active Directory) ID로 설정했을 수 있습니다.  이 문서에서는 구독에 로그인하는 동안 발생할 수 있는 몇 가지 문제에 대해 설명합니다.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>회사/학교 이메일 주소를 사용하여 Microsoft 계정(MSA)을 만들 수 없습니다.
Azure AD에서 이메일 도메인을 구성할 때 직장/학교 이메일 주소를 사용하여 새 개인 Microsoft 계정(MSA)을 만드는 기능을 더 이상 사용할 수 없습니다. 무슨 의미인가요? 조직에서 Azure AD를 사용하는 Microsoft의 Office 365 또는 기타 다른 비즈니스 서비스를 사용하는 경우, Azure AD 테넌트에 도메인 이름을 추가하면 사용자는 더 이상 도메인의 이메일 주소를 사용하여 새 개인 Microsoft 계정을 만들 수 없습니다.

### <a name="why-was-this-change-made"></a>이런 변화가 왜 일어났나요?
회사 주소가 있는 개인 Microsoft 계정을 사용자 이름으로 사용하는 것은 최종 사용자와 IT 부서 모두에게 많은 문제를 일으킵니다. 다음은 그 예입니다.
- 사용자는 자신의 개인 Microsoft 계정이 비즈니스 준수이고 비즈니스 문서를 OneDrive에 저장할때 준수한다고 생각할 수 있습니다.
- 조직을 떠나는 사용자는 일반적으로 회사 이메일 주소에 액세스하지 못합니다. 그럴 경우 자신의 암호를 잊어버리면 개인 Microsoft 계정으로 다시 전환하지 못할 수 있습니다. 반대로 IT 부서는 암호를 다시 설정하고 이전 직원의 개인 계정에 로그인할 수 있습니다.
- IT 부서는 계정 소유권 및 보안에 대해 잘못된 인식을 가지고 있습니다. 하지만 사용자는 회사 이메일 주소로 코드를 한 번만 왕복하면 되고, 나중에 언제든지 계정 이름을 바꿀 수 있습니다.

이메일 주소가 동일한 두 개의 계정을 가진 사용자(Azure AD의 하나 및 Microsoft 계정 하나)에게 특히 혼란스러운 상황입니다.

### <a name="what-does-this-experience-look-like"></a>이러한 환경은 어떻게 생겼나요?
회사 또는 학교 이메일 주소로 Microsoft 소비자 앱에 등록하려고 하면 아래 메시자가 표시됩니다.

   > [!div class="mx-imgBorder"]
   > ![회사 이메일로 계정을 만들 수 없습니다.](_img/sign-in-issues/cannot-use-work-email.png)

그러나 개인 및 회사/학교 계정을 지원하는 Microsoft 앱에 등록하려고 하면 다음 메시지가 표시됩니다.

   > [!div class="mx-imgBorder"]
   > ![회사/학교 계정 지원](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>기존 계정에 영향을 주나요?
여기에 설명된 등록 블록만 새 계정 생성을 방지합니다. 이미 회사/학교 이메일 주소가 있는 Microsoft 계정을 가진 사용자에게는 영향을 주지 않습니다. 이미 이러한 상황에 있는 경우 개인 Microsoft 계정의 이름을 쉽게 변경할 수 있습니다. 이 [지원 문서](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account)는 간단한 단계별 지침을 제공합니다. 개인 Microsoft 계정의 이름을 바꾸면 사용자 이름을 변경한다는 의미이며, 회사 이메일이나 Office 365와 같은 비즈니스 서비스에 로그인하는 방법에 영향을 주지 않습니다. 또한 개인적인 것에 영향을 주지 않습니다. 단지 로그인하는 방식만 변경됩니다. 다른(개인) 이메일 주소를 사용하거나, Microsoft에서 새 @outlook.com 이메일 주소를 가져오거나, 전화 번호를 새 사용자 이름으로 사용할 수 있습니다.

> [!NOTE]
> IT 부서에서 회사/학교 이메일로 개인 Microsoft 계정을 만들도록 요청한 경우(예: 프리미엄 지원과 같은 Microsoft 비즈니스 서비스에 액세스하기 위해) 계정 이름을 변경하기 전에 관리 팀에 문의하세요.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>로그인 주소를 삭제하면 구독에 액세스하지 못할 수 있습니다.
구독과 관련된 하나 이상의 ID(MSA 또는 AAD)를 삭제하면 사용자 이름 및 로그인 ID를 포함한 구독자 정보가 익명으로 렌더링되어 구독에 대한 액세스 권한이 손실될 수 있습니다.

구독 액세스 권한에 영향을 주지 않으려면 다음 기술 중 하나를 사용합니다.
- 단일 ID 관리 시스템인 MSA 또는 AAD 중 하나를 배포하세요(동시 배포는 안됨).
- 테넌트를 통해 AAD 및 MSA ID를 연결합니다.

## <a name="signing-in-may-fail-when-using-aliases"></a>별칭을 사용할 경우 로그인에 실패할 수 있습니다.
로그인에 사용되는 계정 유형에 따라 [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)에 로그인할 때 사용 가능한 구독이 제대로 표시되지 않을 수 있습니다. 한 가지 원인은 구독이 할당된 로그인 ID 대신 “별칭” 또는 “이름”을 사용하기 때문일 수 있습니다. 이것을 “별칭 지정”이라고 합니다.

### <a name="what-is-aliasing"></a>별칭 지정이란 무엇인가요?
“별칭 지정”이라는 용어는 사용자가 Windows(또는 Active Directory)에 로그인하고 전자 메일에 액세스하기 위해 서로 다른 ID를 사용하는 것을 나타냅니다.

회사에 디렉터리 로그인용 Microsoft Online Service가 있지만(예: JohnD@contoso.com) 사용자가 별칭 또는 이름(예: John.Doe@contoso.com)을 사용하여 전자 메일 계정에 액세스할 경우 별칭 지정이 수행됩니다. VLSC(볼륨 라이선스 서비스 센터)를 통해 구독을 관리하는 많은 고객의 경우 제공된 전자 메일 주소(John.Doe@contoso.com)가 “회사 또는 학교 계정” 옵션을 통해 인증에 성공하는 데 필요한 디렉터리 주소(JohnD@contoso.com)와 일치하지 않을 때 이 별칭 지정으로 인해 로그인에 실패할 수 있습니다.

### <a name="what-options-do-i-have"></a>어떤 방법이 있습니까?
구독자 관점에서 먼저 관리자와 함께 회사의 ID 구성을 이해하는 것이 중요합니다. 필요한 경우 관리자가 관리 포털에서 계정 설정을 업데이트해야 할 수 있습니다. 또는 사용자가 회사 전자 메일 주소를 사용하여 Microsoft 계정(MSA)을 만들어야 할 수 있습니다. MSA를 만드는 단계를 수행하기 전에 이 작업 수행과 관련된 정책 또는 문제에 대해 관리자와 이야기를 나눕니다. 

## <a name="see-also"></a>참고 항목
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
- AAD 내에서 [MSA 및 AAD 계정을 연결](/azure/active-directory/b2b/add-users-administrator)하는 방법을 알아봅니다.
- [익명화](anonymization.md)에 대해 자세히 알아봅니다.
