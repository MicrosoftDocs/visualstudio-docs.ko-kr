---
title: 회사 또는 학교 계정으로 Visual Studio 구독 로그인 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: f39a2672-c283-4755-93d3-31c7c7a032d0
ms.date: 03/11/2020
ms.topic: conceptual
description: 회사 또는 학교 계정으로 Visual Studio 구독에 로그인하는 방법을 알아봅니다.
ms.openlocfilehash: e1f80f88cf3a377cc6fcc8f8bef266ee59b90067
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233204"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-work-or-school-account"></a>회사 또는 학교 계정으로 Visual Studio 구독 로그인 

Visual Studio 구독에 로그인하는 단계는 사용 중인 계정의 종류에 따라 다릅니다.  예를 들어 회사 또는 학교에서 제공한 Microsoft 계정(MSA) 또는 전자 메일 주소를 사용할 수 있습니다.  2019년 1월 현재 GitHub 계정을 사용하여 일부 구독에 로그인할 수도 있습니다. 

이 문서에서는 회사나 직장에서 받은 이메일 주소로 로그인하는 단계를 소개합니다.

## <a name="signing-in-with-your-work-or-school-account"></a>회사 또는 학교 계정으로 로그인

1. [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)을 방문해 보세요.
2. 새 Visual Studio 구독이 할당된 전자 메일 주소를 입력합니다.

   > [!NOTE]
   > 이 주소는 사용자가 받은 구독자 시작 전자 메일에서도 확인됩니다. 시작 전자 메일을 찾는 데 문제가 있는 경우 정크 메일 폴더를 확인하세요.

3. **Continue(계속)** 를 클릭합니다.
4. 회사 로그인 페이지로 리디렉션됩니다.
5. 암호를 입력합니다.
6. **로그인**을 클릭합니다.
7. 그러면 “혜택” 페이지가 표시됩니다.

이제 사용 중인 구독 유형이 포털 위쪽에 걸쳐 있는 파란색 막대에 표시되는 것을 확인할 볼 수 있습니다.

오른쪽 위의 사용자 이름 아래에서 현재 선택한 구독을 볼 수도 있습니다.  여기에는 “표시: ”, 구독이 차례로 표시됩니다.  둘 이상의 구독이 있는 경우 드롭다운 화살표를 클릭하고 사용할 구독을 선택할 수 있습니다.

## <a name="using-your-microsoft-account-msa-to-sign-in-to-a-work-or-school-account"></a>Microsoft 계정(MSA)을 사용하여 회사 또는 학교 계정에 로그인

1. [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)으로 이동합니다.
2. 새 Visual Studio 구독이 할당된 전자 메일 주소를 입력합니다.

   > [!NOTE]
   > 이 주소는 구독자 시작 편지에서도 확인됩니다. 시작 편지를 받지 못한 경우 정크 메일 폴더를 확인하세요.

3. **Continue(계속)** 를 클릭합니다.
4. 결정 페이지로 리디렉션됩니다.
    - 구독이 AAD(Azure Active Directory) 테넌트에 연결된 “회사 또는 학교” 계정에 연결된 경우 **회사 또는 학교 계정**을 선택합니다.
    - 구독이 “회사” 전자 메일 주소에 연결되지만 “개인” Microsoft 계정(MSA)으로도 변환된 경우 **개인**을 선택합니다.

        > [!NOTE]
        > 이 경우는 이전에 Visual Studio 구독(이전 MSDN)을 사용한 많은 구독자에 해당합니다.

    - 하나의 경로가 실패하면 다른 경로를 시도하세요.  구독 관리자가 구독을 수정했을 수 있습니다.

5. 암호를 입력합니다.
6. **로그인**을 클릭합니다.
7. 그러면 “혜택” 페이지가 표시됩니다.

## <a name="frequently-asked-questions"></a>질문과 대답
### <a name="q--im-unable-to-sign-in-using-my-work-or-school-email-address"></a>Q:  내 회사 또는 학교 이메일 주소에 로그인할 수 없습니다.  
A:  로그인 문제는 구독과 연결된 계정과 다른 계정으로 로그인을 시도할 때 가장 흔히 발생합니다.  여러 이메일 주소를 사용하는 경우 잘못된 주소로 로그인을 시도하게 될 수 있습니다.  다른 주소로 로그인해 보세요.  이 작업이 실패하면 [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/) 팀에 연락하여 도움을 받으실 수 있습니다.  

### <a name="q--i-cant-see-my-subscription-where-is-it"></a>Q:  내 구독을 볼 수 없습니다. 어디에 있나요?
A:  여러 사용자의 구독이 둘 이상입니다.  [https://my.visualstudio.com](https://my.visualstudio.com )에서 구독 포털로 로그인할 수는 있는데 구독이 보이지 않을 경우 가장 일반적인 원인은 다음과 같습니다.
1. 다른 Microsoft 계정으로 로그인했습니다.  사용자는 Professional이나 Enterprise 구독 등의 다양한 구독과 Visual Studio Dev Essentials 멤버 자격 보유가 가능하며, 이는 다른 이메일 주소와 연결됩니다. 다른 구독을 보려면 로그아웃하고 다른 MSA로 다시 로그인합니다.
2. 동일한 이메일 주소와 연결된 구독이 여러 개 있습니다.  이메일 주소와 연결된 구독을 모두 보려면 https://my.visualstudio.com/subscriptions 에서 사용하려는 구독을 선택합니다. 

여전히 문제가 있을 경우 [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/) 팀에 연락하여 도움을 받으실 수 있습니다.  

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
구독 포털에 성공적으로 로그인했다면 혜택 페이지(https://my.visualstudio.com/benefits )를 방문하여 사용 가능한 유용한 도구, 서비스 및 제안을 살펴보시기 바랍니다.  