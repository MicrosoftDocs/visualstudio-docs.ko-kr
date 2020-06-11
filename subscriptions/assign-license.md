---
title: Visual Studio 구독에 라이선스 할당 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: 관리자가 구독자에게 라이선스를 할당하는 방법을 알아봅니다.
ms.openlocfilehash: a90d6f3fec1f619cda397788c130f7514307effd
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183472"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio 구독 관리 포털에서 라이선스 할당
Visual Studio 구독 관리자는 관리 포털을 사용하여 개별 사용자 또는 사용자 그룹에 구독을 할당할 수 있습니다.

사용자 그룹의 경우 구독을 할당하는 방법을 선택할 수 있습니다.  
- 한 번에 하나씩 구독을 할당하거나
- [일괄 추가](assign-license-bulk.md) 기능을 사용하여 구독자 목록과 해당 구독 정보를 쉽고 빠르게 업로드할 수 있습니다.
- 조직에서 Microsoft Azure Active Directory(Azure AD)를 사용하는 경우 [Azure AD 그룹을 사용하여 구독을 사용자 그룹에 할당](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions)할 수 있습니다.  


## <a name="add-a-single-subscriber"></a>단일 구독자 추가
구독 혜택에 액세스할 수 있도록 새 사용자에게 Visual Studio 구독을 할당하는 방법은 다음과 같습니다.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. [관리 포털](https://manage.visualstudio.com)에 로그인합니다.
2. 단일 Visual Studio 구독자에게 라이선스를 할당하려면 테이블 맨 위에서 **추가**를 선택한 다음 **개별 구독자**를 선택합니다.
   > [!div class="mx-imgBorder"]
   > ![단일 구독자 추가](_img/assign-license-add/add-subscriber-individual.png)
3. 새 구독자에 대한 정보를 양식 필드에 입력합니다. 조직에서 Azure Active Directory를 사용하는 경우 **이름** 필드는 현재 디렉터리에 있는 사람을 찾는 검색 기능 역할을 하므로 검색 결과에서 올바른 사용자를 선택할 수 있습니다. 해당 사용자를 선택하면 로그인 전자 메일 및 알림 전자 메일이 자동으로 채워집니다.
   > [!div class="mx-imgBorder"]
   > ![구독자 세부 정보](_img/assign-license-add/subscriber-details.png)

    > [!NOTE]
    > 구독자 이름을 입력할 때 Azure Active Directory 테넌트의 멤버가 표시되려면 관리자가 테넌트의 멤버여야 합니다. 


    구독자가 [Visual Studio 구독 포털](https://my.visualstudio.com?wt.mc_id=o~msft~docs)에 로그인할 때 소프트웨어 다운로드에 액세스할 수 있도록 하려면 **다운로드 설정**에서 다운로드 토글을 사용하도록 설정된 상태로 둡니다. 다운로드를 사용하지 않도록 설정하면 사용자는 소프트웨어 다운로드에 액세스할 수 없게 됩니다.  제품 키에 대한 액세스도 사용하지 않도록 설정됩니다.  구독자는 구독에 포함된 다른 모든 혜택에 계속 액세스할 수 있습니다.
   > [!div class="mx-imgBorder"]
   > ![다운로드 액세스 권한](media/access-to-downloads.png)

    구독에 고유한 참조 정보를 추가하려는 경우 **참조 추가** 섹션에서 수행할 수 있습니다.
   > [!div class="mx-imgBorder"]
   > ![각 구독에 고유한 참조 정보 추가](media/add-subscriber-reference-notes.png)

    옵션 선택 및 구독자에 대한 데이터 입력을 완료한 경우 **구독자 추가** 플라이아웃 맨 아래에 **추가**를 선택합니다.
   > [!div class="mx-imgBorder"]
   > ![추가 단추 선택](media/add-button.png)

## <a name="resend-assignment-emails"></a>할당 전자 메일 다시 보내기
구독자를 추가한 후 새 구독자에게 추가 지침이 있는 할당 전자 메일이 자동으로 전송됩니다. 구독자를 선택하고 위쪽 메뉴의 **다시 보내기** 단추를 클릭하여 언제든지 할당 전자 메일을 다시 보낼 수 있습니다.  여러 사용자에게 전자 메일을 다시 보내려면 구독자를 선택 하는 동안 **Ctrl** 키를 누르고 있습니다.  **다시 보내기** 단추를 클릭하면 해당 구독자에게 다시 보낼 것인지 확인하는 대화 상자가 표시됩니다.  

## <a name="see-also"></a>참고 항목
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>다음 단계
- 추가할 사용자가 많은가요?  [여러 구독자](assign-license-bulk.md)에게 구독을 할당하는 방법을 알아보세요.
- 도움 필요 시  [Visual Studio 관리 및 구독 지원](https://visualstudio.microsoft.com/support/support-overview-vs)에 문의하세요.


