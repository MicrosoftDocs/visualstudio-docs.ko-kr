---
title: Visual Studio + GitHub Enterprise 제품 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Visual Studio + GitHub Enterprise 제품에서 구독 관리
ms.openlocfilehash: e48b047862daa80452e1b2128dc74fee8bd1039e
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263333"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>GitHub Enterprise가 포함된 Visual Studio 구독 관리
Microsoft와 EA(기업계약)를 체결한 고객은 Visual Studio 표준 구독과 GitHub Enterprise를 결합한 새 구독 제품을 구매할 수 있습니다. 이는 Visual Studio 구독자가 GitHub Enterprise를 쉽고 경제적으로 구입하는 방법입니다. 

조직에서 GitHub Enterprise가 포함된 Visual Studio Subscriptions를 구입하면 두 부분으로 프로비저닝되고 관리됩니다.

## <a name="manage-visual-studio-subscriptions"></a>Visual Studio 구독 관리
조직에서 GitHub Enterprise가 포함된 Visual Studio 구독을 구입하면 구독의 Visual Studio 부분이 즉시 프로비저닝되고 Visual Studio [구독 관리](https://manage.visualstudio.com) 포털에서 할당 및 관리에 구독을 사용할 수 있습니다. 

구독 관리에 대한 자세한 내용은 다음 항목을 참조하세요.
- [관리 포털 사용](using-admin-portal.md)
- [구독 할당](assign-license.md)
- [구독 편집](edit-license.md)
- [구독 삭제](delete-license.md)
- [초과 할당](handle-overclaimed-license.md)

> [!Important]
> GitHub Enterprise가 포함된 Visual Studio Subscriptions가 Visual Studio 구독 관리자에 의해 할당되고 해당 구독의 구매가 없는 경우 조직 내의 GitHub Enterprise 관리자에게 해당 항목이 표시되지 않습니다. GitHub Enterprise 구독을 표시하려면 구독을 처음 할당할 때 **하나 이상의** GitHub Enterprise가 포함된 Visual Studio Professional 또는 GitHub Enterprise 구독이 포함된 Visual Studio Enterprise를 구매해야 합니다.  
>
> 할당된 GitHub 구독마다 Visual Studio 구독 관리 포털에 GitHub 구독이 할당된 해당 Visual Studio가 있고 이 구독의 라이선스 요구 사항을 준수하는지 확인하는 것은 고객의 책임입니다.

## <a name="manage-github-enterprise-subscriptions"></a>GitHub Enterprise 구독 관리
GitHub Enterprise 구독을 구매할 때 GitHub에 액세스하고 관리자를 식별하는 조직을 만들고 구성할 수 있도록 고객과 GitHub 파트너 관계를 맺습니다.  그런 다음, 이러한 관리자는 관리자로 설정되었다는 알림을 받습니다.  

이 프로세스는 매우 복잡하기 때문에 조직 및 관리자가 완전히 설정되기 위해서는 구독을 구매한 후 며칠이 걸릴 수 있습니다.

GitHub는 클라우드 기반 GitHub.com 또는 온-프레미스 GitHub Enterprise 서버로 사용할 수 있습니다.  두 버전을 관리하는 프로세스가 다릅니다.  GitHub는 GitHub Enterprise 구독을 관리하는 데 도움이 되는 다양한 도움말 항목과 관리자 가이드를 제공합니다.  아래 선택한 항목의 링크를 제공했습니다.  

### <a name="githubcom"></a>GitHub.com 
GitHub.com 관리에 대한 자세한 내용은 [GitHub 도움말](https://help.github.com/en)에서 다음 항목을 체크 아웃하세요.
+ [도움말 항목의 전체 목록](https://help.github.com/en)
+ [조직의 멤버 자격 관리](https://help.github.com/en/articles/managing-membership-in-your-organization)
+ [조직에 조인하도록 사용자 초대](https://help.github.com/en/articles/inviting-users-to-join-your-organization)
    - [팀/조직에서 사용자 제거](https://help.github.com/en/articles/removing-a-member-from-your-organization)
    - [조직의 이전 멤버 복원](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization)
+ [역할을 사용하여 액세스 관리](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles)
+ [사용자를 팀으로 구성](https://help.github.com/en/articles/organizing-members-into-teams)
+ [조직의 리포지토리에 대한 액세스 관리](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories)

### <a name="github-enterprise-server"></a>GitHub Enterprise 서버
GitHub 도움말은 질문에 답하고 조직의 GitHub Enterprise 서버 구현 관리에 대한 팁을 제공하는 다양한 관리자 가이드를 제공합니다.

+ [모든 관리자 가이드 보기](https://help.github.com/en/enterprise/2.16/admin)
+ [사용자 관리](https://help.github.com/en/enterprise/2.16/admin/user-management)
    - [조직 및 팀](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams)
        - [조직 만들기](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations)
        - [팀 만들기](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams)
        - [팀에 사용자 추가](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams)
        - [팀 및 조직에서 사용자 제거](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations)
    - [사용자 보안](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security)
+ [GitHub Enterprise 서버 설치 및 구성](https://help.github.com/en/enterprise/2.16/admin/installation)

## <a name="support-resources"></a>지원 리소스
- [GitHub 도움말](https://help.github.com/en)에서 다양한 GitHub 항목에 대한 질문의 답을 찾을 수 있습니다.
- [GitHub 커뮤니티 포럼](https://github.community/)에서 다른 GitHub 사용자의 도움을 받으세요.
- Visual Studio 구독에 대한 판매, 구독, 계정 및 요금 청구에 대한 지원을 받으려면 Visual Studio [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/)에 문의하세요.
- Visual Studio IDE, Azure DevOps Services 또는 기타 Visual Studio 제품이나 서비스와 관련하여 궁금한 점이 있나요?  [Visual Studio 지원](https://visualstudio.microsoft.com/support/)을 참조하세요.
- GitHub Enterprise에 대한 [기술 지원](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24)을 받으세요.   

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
- [구독 삭제](delete-license.md)
- [최대 사용량 확인](maximum-usage.md)

GitHub Enterprise가 포함된 Visual Studio Subscriptions를 관리하는 방법에 대한 자세한 내용은 Visual Studio [구독 관리자 포털](https://visualstudio.microsoft.com/subscriptions-administration/)을 참조하세요.


