---
title: VLSC의 Visual Studio 구독 관련 개인 전자 메일
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/21/2021
ms.topic: conceptual
description: Visual Studio 구독 - 구독자의 Hotmail 또는 Gmail 주소가 보이는 이유는 무엇인가요?
ms.openlocfilehash: 99c22d74a9a6fb57e79f699e548de928ef1ebcb6
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104777002"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio 구독 - 구독자의 개인 계정이 보이는 이유는 무엇인가요?
기업이 VLSC(볼륨 라이선스 서비스 센터)에서 새 Visual Studio [구독 관리 포털](https://manage.visualstudio.com)로 마이그레이션한 후 관리자는 일부 구독자의 “로그인 전자 메일 주소”에 Hotmail 또는 Outlook과 같은 개인 전자 메일 주소가 표시되는 것을 발견했습니다.  

## <a name="cause"></a>원인
이 시나리오는 레거시 MSDN 구독자 환경에 연결된 로그인 프로세스로 인해 발생합니다. 사용자가 수정 과정 없이 VLSC(볼륨 라이선스 서비스 센터)에서 Visual Studio 구독 관리 포털로 마이그레이션되었습니다. 관리자는 사용자가 개인 계정을 사용하여 구독 혜택에 액세스했음을 알지 못했을 수 있습니다. 2016년에 완료된 Visual Studio 구독자 마이그레이션 전에는 Visual Studio 구독을 성공적으로 사용하는 데 필요한 두 가지 작업이 있었습니다.
1. 관리자가 해당 회사 또는 학교 전자 메일 주소를 사용하여 개별 구독자에게 구독을 “할당”했습니다.
2. 구독자가 구독을 “활성화”했습니다.

구독자 활성화 프로세스 중에: 로그인하려면 Microsoft 계정(MSA)이 필요했습니다. 구독자가 해당 회사 또는 학교 계정(예: tasha@contoso.com)을 MSA로 설정하지 않은 경우 새 MSA를 만들거나 기존 MSA를 활용할 수 있었습니다. 이로 인해 “로그인 전자 메일 주소”가 “할당 대상 전자 메일 주소”와 달라졌습니다.

> [!NOTE]
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)의 최신 구독자 환경은 회사/학교 및 MSA(Microsoft 계정) ID 유형을 둘 다 지원합니다.

## <a name="solution"></a>솔루션
문제를 해결하려면 **전자 메일 연결** 단추를 선택하면 됩니다. 그러면 시스템에서는 이름과 성이 일치하는지 여부에 따라 MSA가 있는 계정을 조직의 Azure AD(Azure Active Directory)에 있는 기존 사용자와 대조하려고 합니다. 오류가 발생하는 경우 일치 항목 오른쪽의 **X** 를 클릭하여 일치 항목을 제거할 수 있습니다.  

해결하는 방법을 알아보려면 이 비디오를 시청하거나 계속 읽어 보세요. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![전자 메일 연결 단추](_img/connect-emails/connect-emails-button.png "Microsoft 계정을 사용하는 사용자를 Azure Active Directory에 일치시키려면 전자 메일 연결 클릭")

**디렉터리 검색** 을 사용하여 오류를 수정하거나 Azure AD에서 누락된 정보를 입력할 수도 있습니다. 모든 일치 항목이 제대로 표시되면 한 번에 하나씩 선택하는 대신 **현재 ID** 단추를 선택하여 모든 일치 항목을 선택할 수 있습니다.  

> [!div class="mx-imgBorder"]
> ![전자 메일 연결 플라이아웃](_img/connect-emails/connect-emails-flyout.png "Azure AD ID에 일치시키려는 구독자를 선택하고 계속을 클릭합니다.")

그런 다음, **계속** 을 클릭하면 적용할 변경 내용 목록으로 이동합니다. 동의하는 경우 **저장** 을 클릭하면 변경 내용이 적용됩니다. 구독자는 다음에 구독에 로그인할 때 변경 내용을 알리는 메시지도 받게 됩니다.  Azure Active Directory에서 일치한 두 명의 구독자만 해당 목록에 표시됩니다.  이 예제에서 Frederick은 Azure AD에 해당하는 주소가 없으므로 MSA(Microsoft 계정)는 회사 계정과 일치하지 않았습니다. 

> [!div class="mx-imgBorder"]
> ![전자 메일 연결 확인](_img/connect-emails/connect-emails-confirm.png "계속을 클릭하여 제안된 변경 내용을 구현한 다음, 저장을 클릭합니다.") 

> [!NOTE]
> 로그인 전자 메일 주소를 편집하면 구독자가 https://my.visualstudio.com 의 구독에 로그인하는 데 사용하는 전자 메일만 업데이트됩니다. 구독자가 다른 전자 메일 주소를 사용하여 Azure 또는 Pluralsight 같은 혜택을 이미 활성화한 경우 해당 전자 메일 주소를 사용하여 계속 액세스해야 합니다. 사용자가 액세스하는 새로운 혜택에서는 새 전자 메일 주소를 사용해야 합니다. 

## <a name="support-resources"></a>지원 리소스
- Visual Studio 구독 관리에 대한 지원을 받으려면 [Visual Studio 구독 지원](https://aka.ms/vsadminhelp)에 문의하세요.

## <a name="see-also"></a>참고 항목
- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)

##  <a name="next-steps"></a>다음 단계
- 구독자 전자 메일 주소를 업데이트한 후 로그인 정보가 변경되었음을 구독자에게 알려야 할 수 있습니다.  또한 업데이트된 정보가 포함된 전자 메일을 받게 됩니다.
- 변경이 필요할 수 있는 로그인 전자 메일 주소를 찾기 위해 조직의 [구독자 목록을 필터링](search-license.md)하는 것이 유용할 수 있습니다.