---
title: VLSC에 표시된 개인 전자 메일
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/17/2020
ms.topic: conceptual
description: Visual Studio 구독 - 구독자의 Hotmail 또는 Gmail 주소가 보이는 이유는 무엇인가요?
ms.openlocfilehash: 7cd6a4761efb7dcad7568bd0a95ba33141407055
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79550331"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio 구독 - 구독자의 개인 계정이 보이는 이유는 무엇인가요?
기업이 VLSC(볼륨 라이선스 서비스 센터)에서 새 Visual Studio [구독 관리 포털](https://manage.visualstudio.com)로 마이그레이션한 후 관리자는 일부 구독자의 “로그인 전자 메일 주소”에 Hotmail 또는 Outlook과 같은 개인 전자 메일 주소가 표시되는 것을 발견했습니다.  자세한 내용은 [이 비디오](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6)를 참조하세요.

## <a name="cause"></a>원인
이 시나리오는 레거시 MSDN 구독자 환경에 연결된 로그인 프로세스로 인해 발생합니다. 사용자가 수정 과정 없이 VLSC(볼륨 라이선스 서비스 센터)에서 Visual Studio 구독 관리 포털로 마이그레이션되었습니다. 관리자는 사용자가 개인 계정을 사용하여 구독 혜택에 액세스했음을 알지 못했을 수 있습니다. 2016년에 완료된 Visual Studio 구독자 마이그레이션 전에는 Visual Studio 구독을 성공적으로 사용하는 데 필요한 두 가지 작업이 있었습니다.
1. 관리자가 해당 회사 또는 학교 전자 메일 주소를 사용하여 개별 구독자에게 구독을 “할당”했습니다.
2. 구독자가 구독을 “활성화”했습니다.

구독자 활성화 프로세스 중에: 로그인하려면 Microsoft 계정(MSA)이 필요했습니다. 구독자가 해당 회사 또는 학교 계정(예: tasha@contoso.com)을 MSA로 설정하지 않은 경우 새 MSA를 만들거나 기존 MSA를 활용할 수 있었습니다. 이로 인해 “로그인 전자 메일 주소”가 “할당 대상 전자 메일 주소”와 달라졌습니다.

> [!NOTE]
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)의 최신 구독자 환경은 회사/학교 및 MSA(Microsoft 계정) ID 유형을 둘 다 지원합니다.

## <a name="solution"></a>솔루션
문제를 해결하려면 **전자 메일 연결** 단추를 선택하면 됩니다. 그러면 시스템에서는 이름과 성이 일치하는지 여부에 따라 MSA가 있는 계정을 조직의 Azure AD(Azure Active Directory)에 있는 기존 사용자와 대조하려고 합니다. 오류가 발생하는 경우 일치 항목 오른쪽의 **X**를 클릭하여 일치 항목을 제거할 수 있습니다.  

> [!div class="mx-imgBorder"]
> ![전자 메일 연결 단추](_img/connect-emails/connect-emails-button.png)

**디렉터리 검색**을 사용하여 오류를 수정하거나 Azure AD에서 누락된 정보를 입력할 수도 있습니다. 모든 일치 항목이 제대로 표시되면 한 번에 하나씩 선택하는 대신 “Select all matching subscribers”(일치하는 모든 구독자 선택)를 선택할 수 있습니다.  

> [!div class="mx-imgBorder"]
> ![전자 메일 연결 플라이아웃](_img/connect-emails/connect-emails-flyout.png)

그런 다음 “계속”을 클릭하면 적용할 변경 내용을 표시하는 화면으로 이동합니다. 동의하는 경우 “저장”을 클릭하면 변경 내용이 적용됩니다. 구독자는 다음에 구독에 로그인할 때 변경 내용을 알리는 메시지도 받게 됩니다.   

> [!div class="mx-imgBorder"]
> ![전자 메일 연결 확인](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> 로그인 전자 메일 주소를 편집하면 구독자가 https://my.visualstudio.com 의 구독에 로그인하는 데 사용하는 전자 메일만 업데이트됩니다. 구독자가 다른 전자 메일 주소를 사용하여 Azure 또는 Pluralsight 같은 혜택을 이미 활성화한 경우 해당 전자 메일 주소를 사용하여 계속 액세스해야 합니다. 사용자가 액세스하는 새로운 혜택에서는 새 전자 메일 주소를 사용해야 합니다. 

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>다음 단계
- 구독자 전자 메일 주소를 업데이트한 후 로그인 정보가 변경되었음을 구독자에게 알려야 할 수 있습니다.  또한 업데이트된 정보가 포함된 전자 메일을 받게 됩니다.
- 변경이 필요할 수 있는 로그인 전자 메일 주소를 찾기 위해 조직의 [구독자 목록을 필터링](search-license.md)하는 것이 유용할 수 있습니다.  
