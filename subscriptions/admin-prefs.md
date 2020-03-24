---
title: 관리 포털에서 계약 기본 설정 지정
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/17/2020
ms.topic: conceptual
description: 관리 포털에서 언어, 연락처, 구독 수준 등에 대한 기본 설정을 지정하는 방법 알아보기
ms.openlocfilehash: cbcf532620e958ca408d43295d2d4200d12ee0cd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508760"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>관리 포털에서 계약 기본 설정 지정
슈퍼 관리자는 관리 포털에서 각 계약에 전역으로 적용될 특정 기본 설정을 지정할 수 있습니다.  이 기본 설정은 관리자가 구독자를 추가할 때 구독 세부 정보를 자동으로 채우며 슈퍼 관리자만 전역으로 수정할 수 있습니다.  

## <a name="access-preferences"></a>기본 설정에 액세스
기본 설정을 보거나 수정하려면 계약에 대한 슈퍼 관리자 권한이 있는 로그인 ID를 사용하여 [관리자 포털](https://manage.visualstudio.com)에 로그인해야 합니다.  

기본 설정을 지정하려면 다음을 수행합니다.
1. 슈퍼 관리자 권한이 있는 ID로 관리 포털에 로그인합니다.
2. **관리자 관리** 탭을 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![관리자 기본 설정 단추](_img/admin-prefs/admin-prefs-button.png)

3. **계약 기본 설정**을 클릭합니다.
패널이 오른쪽에서 열리고 사용 가능한 기본 설정이 표시됩니다. 

   > [!div class="mx-imgBorder"]
   > ![관리자 기본 설정 플라이아웃 대화 상자](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>기본 설정 지정
사용 가능한 각 기본 설정과 해당 결과를 살펴보겠습니다. 

### <a name="agreement"></a>계약
슈퍼 관리자 역할을 하는 여러 계약을 보유한 경우 드롭다운에서 원하는 계약을 선택할 수 있습니다.  설정하는 기본 설정은 해당 계약에만 적용됩니다.  개별 관리자는 구독을 할당할 때 사례별로 이 기본 설정 중 일부를 재정의할 수 있습니다. 

로그인하는 데 사용한 전자 메일 주소와 연결된 계약이 하나만 있는 경우에는 해당 계약이 표시되고 드롭다운이 사용하지 않도록 설정됩니다. 

### <a name="contact-email-address"></a>연락처 전자 메일 주소
이 기본 설정은 구독자가 구독자 포털의 [구독 페이지](https://my.visualstudio.com/subscriptions)에서 **내 관리자에게 문의** 단추를 사용하여 관리자에게 연락하는 방법을 제공합니다.  이 기본 설정을 비워 두면 구독자 메시지가 계약의 모든 관리자 및 슈퍼 관리자에게 전달됩니다.  그룹 전자 메일 별칭 또는 보안 그룹을 사용하여 이 연락처 전자 메일의 대상 그룹을 조정하는 것이 좋습니다. 원하는 경우 개별 전자 메일 주소를 입력하도록 선택할 수도 있습니다.

> [!NOTE]
> 여기에 나열한 전자 메일 주소는 구독자에게 제공되지 않습니다.  구독자가 구독자 포털에서 **내 관리자에게 문의** 요청을 제출하면 해당 메시지는 구독자에게 공개하지 않고 별칭으로 전달됩니다. 

### <a name="default-external-subscribers-setting"></a>기본 외부 구독자 설정
이 기본 설정을 사용하여 관리자가 조직의 테넌트/디렉터리 외부에서 구독자를 추가할 수 있는지 여부를 결정할 수 있습니다.  이 기능을 끄면 외부 구독자가 허용되지 않습니다.  이 기능을 사용하도록 설정하고 관리자가 외부 구독자를 추가하려고 하면 선택을 확인하는 메시지가 표시되고 구독을 할당할 수 있습니다. 관리자는 이 설정을 재정의할 수 없습니다. 

### <a name="default-downloads-setting"></a>기본 다운로드 설정
기본적으로 켜지는 이 설정을 사용하도록 설정하면 관리자가 새 구독을 만들 때 구독자가 다운로드에 액세스할 수 있습니다.  관리자가 개별 구독을 기준으로 다운로드를 사용하지 않도록 설정할 수 있습니다.  

### <a name="default-subscription-level"></a>기본 구독 수준
이 설정을 사용하여 구독이 사용자에게 할당될 때 기본적으로 선택되는 계약에 포함된 구독 수준을 결정할 수 있습니다.  관리자는 이 설정을 계약의 구독 수준으로 변경할 수 있습니다. 이렇게 하면 가장 일반적인 선택을 반복할 필요가 없습니다. 

### <a name="default-communication-preferences"></a>기본 통신 기본 설정
기본 통신 언어 및 로캘을 설정하면 구독을 할당하는 절차를 간소화할 수 있습니다.  예를 들어 개발 팀이 관리 팀과 다른 국가에 있는 경우 구독자 위치에 가장 적합한 기본 설정을 지정할 수 있습니다. 개별 구독자의 모든 관리자가 이 설정을 변경할 수 있습니다. 

## <a name="frequently-asked-questions"></a>질문과 대답
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>Q:  구독자가 관리자에게 문의할 수 없도록 **연락처 전자 메일 주소**를 사용하지 않도록 설정할 수 있나요?
A:  아니요 - 보안 그룹, 그룹 전자 메일 별칭 또는 개별 전자 메일 주소를 사용하여 연락하는 관리자를 확인하는 동안에는 기능을 사용하지 않도록 설정할 수 없습니다.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>Q: 구독자의 전자 메일에 응답하면 구독자가 내 전자 메일 주소를 알게 되나요?
A:  사용 중인 모든 전자 메일 클라이언트에서 응답이 제공되므로 구독자가 받는 응답에는 사용 중인 모든 전자 메일 주소가 표시됩니다.  따라서 그룹 별칭에서 응답하는 경우 그룹 별칭이 표시됩니다.  자신의 전자 메일 주소에서 응답하면 해당 주소가 표시됩니다.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>Q: 구독자 포털에서 **내 관리자에게 문의** 기능에 대한 자세한 정보는 어디에서 찾을 수 있나요?
A:  [내 관리자에게 문의](contact-my-admin.md) 문서를 참조하세요. 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Q: **연락처 전자 메일 주소**가 완성되지 않고 구독자가 **내 관리자에게 문의** 기능을 사용하는 경우에는 누가 해당 요청을 받나요?
A:  **연락처 전자 메일 주소** 기본 설정에 특정 전자 메일 주소가 설정되어 있지 않으면 계약의 모든 관리자가 요청을 받게 됩니다. 

## <a name="resources"></a>리소스
- [Visual Studio 관리 및 구독 지원](https://visualstudio.microsoft.com/support/support-overview-vs)

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



