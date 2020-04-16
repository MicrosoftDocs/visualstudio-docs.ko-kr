---
title: 사용자 그룹에 Visual Studio 구독에 대한 라이선스 할당 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: 관리자가 일괄 추가 기능 또는 Microsoft Azure Active Directory 그룹을 사용하여 여러 구독자에게 라이선스를 할당하는 방법을 알아봅니다.
ms.openlocfilehash: a7742049cdda2568504e54d2c83259bb4a262819
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385520"
---
# <a name="assign-subscriptions-to-multiple-users"></a>여러 사용자에게 구독 할당
구독 관리 포털을 사용하면 한 번에 한 명 또는 여러 그룹에 사용자를 추가할 수 있습니다.  개별 사용자를 추가하려면 [단일 사용자 추가](assign-license.md)를 참조하세요.

대규모 사용자 그룹을 추가하려면 일괄 추가 기능을 사용하면 됩니다. 조직에서 Microsoft Azure Active Directory(Azure AD)를 사용하는 경우에는 Azure AD 그룹을 사용할 수 있습니다. 이 문서에서는 두 옵션의 프로세스를 모두 설명합니다. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>일괄 추가를 사용하여 구독 할당
1. https://manage.visualstudio.com 에서 Visual Studio 구독 관리 포털에 로그인합니다.

2. 여러 구독자를 한 번에 추가하려면 **구독자 관리** 탭으로 이동합니다. **추가** 탭을 선택한 다음 드롭다운에서 **일괄 추가**를 선택합니다.  

2. 일괄 추가는 Microsoft Excel 템플릿을 사용하여 구독자 정보를 업로드합니다. [여러 구독자 업로드] 대화 상자에서 **다운로드**를 클릭하여 템플릿을 다운로드합니다.
   > [!div class="mx-imgBorder"]
   > ![Excel 템플릿을 다운로드하여 여러 구독자 업로드](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > 항상 이 템플릿의 최신 버전을 다운로드합니다. 이전 버전을 사용하는 경우 대량 업로드가 실패할 수 있습니다.

3. Excel 스프레드시트에서 구독을 할당하려는 개인에 대한 정보로 필드를 채웁니다. (*참조*는 선택적 필드입니다.) 작업을 마친 후에 파일을 로컬로 저장합니다.

   원활한 업로드를 보장하기 위해 다음 모범 사례를 관찰합니다.

    - 양식 필드에 쉼표가 없는지 확인합니다.
    - 양식 필드 앞뒤의 공백을 제거합니다.
    - 두 부분으로 이루어진 사용자 이름에서 첫 번째 이름과 마지막 이름 사이에 여분의 공백이 포함되지 않아야 합니다(예: 사용자의 첫 번째 이름이 "Maggie May"와 같이 두 부분으로 이루어진 경우 시스템에서 여분의 공백을 제거하지 않으므로 "MaggieMay"로 입력해야 함).
    - 모든 필수 필드가 완료되었는지 확인합니다. 
    - **오류 메시지** 열을 확인합니다.  나열된 오류가 있다면 파일을 업로드하기 전에 오류를 해결합니다. 

4. Visual Studio 구독 관리 포털로 돌아갑니다. **여러 구독자 업로드** 대화 상자에서 **찾아보기**를 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![저장된 템플릿으로 이동하여 여러 구독자 업로드](media/bulk-add-browse-saved-template.png)

5. 저장한 Excel 파일로 이동한 다음, **확인**을 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![Excel 템플릿을 업로드하여 여러 구독자 업로드](media/bulk-upload-subscribers.png)

    업로드 진행률 대화 상자가 표시됩니다.

    템플릿에 오류가 있는 경우 업로드가 실패합니다. 그러면 템플릿을 수정하고 대량 업로드를 다시 시도할 수 있도록 오류 메시지가 표시됩니다.
   > [!div class="mx-imgBorder"]
   > ![여러 구독자 업로드에 실패한 경우 오류 메시지](_img/assign-license-bulk/bulk-add-upload-failure.png)

   오류가 발생하는 경우 다음 단계를 수행합니다.
   1. 만든 Excel 파일을 열고 문제를 해결한 후 파일을 저장합니다.
   0. 관리 포털로 돌아가서 **추가**를 선택합니다.
   0. **대량 추가**를 선택합니다.
   0. Excel 파일을 이미 저장했으므로 템플릿을 다운로드할 필요가 없습니다.  **찾아보기**를 클릭하고 방금 저장한 파일을 찾은 다음 **열기**를 클릭합니다.
   0. **확인**을 클릭합니다.


    업로드가 성공적으로 완료되면 구독자 목록과 확인 메시지가 표시됩니다.
   > [!div class="mx-imgBorder"]
   > ![여러 구독자 업로드에 성공한 경우 확인 메시지](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Azure Active Directory 그룹을 사용하여 구독 할당 
이 기능을 사용하면 구독 할당을 쉽게 파악할 수 있습니다. 구독 관리 포털에서 Azure Active Directory 보안 그룹을 추가하면 그룹의 모든 사용자에게 구독을 할당할 수 있습니다. 조직을 떠나 Azure Active Directory에서 제거되는 사용자는 구독에 대한 액세스 권한도 제거되므로 편리합니다. 


> [!IMPORTANT]
>
> Azure AD 그룹을 사용한 구독자 추가에는 다음 제한 사항이 적용됩니다.
> - 그룹에는 적어도 한 명의 멤버가 포함되어야 합니다.  빈 그룹은 지원되지 않습니다.
> - 그룹의 사용자 수는 1,000명 미만이어야 합니다. 
> - 모든 사용자는 그룹의 최상위 수준에 있어야 합니다.  중첩된 그룹은 지원되지 않습니다.
> - 신뢰할 수 있는 계약만 지원됩니다.
> - 그룹의 모든 멤버에게는 Azure AD 계정에 연결된 전자 메일 주소가 있어야 합니다.
> - Azure AD 그룹을 사용하여 추가한 구독에서는 알림에 별도의 전자 메일 주소를 사용할 수 없습니다.  

1. [https://manage.visualstudio.com](https://manage.visualstudio.com)에서 Visual Studio 구독 관리 포털에 로그인합니다.

2. 여러 구독자를 한 번에 추가하려면 **구독자 관리** 탭으로 이동합니다.

3. **추가** 탭을 선택한 다음 드롭다운에서 **Azure Active Directory 그룹**을 선택합니다.  

   > [!div class="mx-imgBorder"]
   > ![Azure AD를 사용하여 일괄 추가 선택](_img/assign-license-bulk/bulk-add-aad.png)

4. 양식 필드에 추가할 Azure AD 그룹의 이름을 입력하기 시작합니다. 이렇게 하면 조직 내에서 사용할 수 있는 Azure AD 그룹이 검색됩니다. 

5. 그룹을 선택하면 필드에 자동으로 그룹 이름이 채워집니다. 추가하기 전에 해당 그룹의 사용자를 볼 수 있는 옵션이 있습니다. 다음으로 그룹의 구독 수준, 다운로드 권한, 통신 기본 설정을 선택할 수 있습니다. 원한다면 참조 필드에 세부 정보를 추가할 수 있습니다. 

   > [!div class="mx-imgBorder"]
   > ![Azure AD를 사용하여 일괄 추가 선택](_img/assign-license-bulk/bulk-add-aad-details.png)

6. **추가**를 클릭한 다음 **확인**을 클릭합니다. 

7. 추가된 그룹을 보려면 사용자 목록 아래로 스크롤합니다.  

8. 그룹 멤버를 표시하려면 **구독자 보기**를 선택합니다. 그룹의 구독자에 대한 세부 정보를 볼 수 있지만 구독자 또는 구독자에게 할당된 구독은 편집할 수 없습니다.    

> [!NOTE]
> 사용자에게 이미 개별적으로 구독을 할당했고 이후 해당 사용자가 Azure AD 그룹의 일부로 추가되었다면 해당 사용자는 그룹의 일부로 추가되며 더 이상 개인으로 표시되지 않습니다. 그러나 개별 구독이 다른 구독 수준인 경우에는 두 개의 구독을 갖게 됩니다.  예:  개별 Visual Studio Professional 구독이 있는 사용자가 Visual Studio Enterprise 구독이 할당된 그룹의 멤버인 경우 해당 사용자는 두 가지 구독을 모두 갖게 됩니다.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>질문과 대답
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Q: Azure AD 그룹 내에서 할당할 여러 구독 수준을 선택할 수 있나요? 
A: 아니요. 그룹의 모든 사용자는 동일한 구독을 받습니다. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Q: Azure AD 그룹에 추가된 개별 구독자의 구독자 세부 정보를 편집할 수 있나요?  
A: 아니요. 개별 구독자의 정보를 수정하려면 Azure AD 보안 그룹에서 해당 구독자를 제거한 다음 개별적으로 구독에 할당해야 합니다.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Q: Azure AD 보안 그룹에 구독자를 추가했지만 구독 관리 포털에는 추가되었다고 표시되지 않고 구독도 없습니다. 이유는 무엇입니까?  
A: 조직이 Azure AD를 구성한 방식에 따라 사용자가 추가되기까지 최대 24시간 지연될 수 있습니다. 24시간 넘게 지연되면 [고객 지원팀에 문의](https://visualstudio.microsoft.com/support/support-overview-vs)하세요.  

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
- 구독자를 한두 명 정도만 추가하시겠습니까?  [단일 사용자 추가](assign-license.md) 체크 아웃
- 도움 필요 시 [Visual Studio 관리 및 구독 지원](https://visualstudio.microsoft.com/support/support-overview-vs)에 문의하세요.
