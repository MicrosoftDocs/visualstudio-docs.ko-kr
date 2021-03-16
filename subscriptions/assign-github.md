---
title: GitHub Enterprise가 포함된 Visual Studio 구독 할당 | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: GitHub Enterprise가 포함된 Visual Studio 구독에서 구독 관리
ms.openlocfilehash: 5837ec33e6f17f0970178a0f1b306960e9c42668
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249690"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>GitHub Enterprise가 포함된 Visual Studio 구독 관리
Microsoft와 EA(기업계약)를 체결한 고객은 Visual Studio 표준 구독과 GitHub Enterprise를 결합한 새 구독 제품을 구매할 수 있습니다. 이는 Visual Studio 구독자가 GitHub Enterprise를 쉽고 경제적으로 구입하는 방법입니다. 

조직에서 GitHub Enterprise가 포함된 Visual Studio 구독을 구입하면 두 부분으로 프로비저닝되고 관리됩니다.

## <a name="manage-visual-studio-subscriptions"></a>Visual Studio 구독 관리
조직에서 GitHub Enterprise가 포함된 Visual Studio 구독을 구입하면 구독의 Visual Studio 부분은 즉시 프로비저닝되고 구독은 Visual Studio [구독 관리](https://manage.visualstudio.com) 포털에서 할당 및 관리에 사용할 수 있습니다. GitHub Enterprise가 포함된 Visual Studio 구독을 할당하면 구독자는 <https://my.visualstudio.com/subscriptions>에서 Visual Studio 구독에 액세스할 수 있음을 알리는 전자 메일을 받게 됩니다.

Visual Studio 구독 관리에 대한 자세한 내용은 다음 항목을 참조하세요.
- [관리 포털 사용](using-admin-portal.md)
- [구독 할당](assign-license.md)
- [구독 편집](edit-license.md)
- [구독 삭제](delete-license.md)
- [초과 할당](handle-overclaimed-license.md)

> [!Important]
> GitHub Enterprise가 포함된 Visual Studio 구독을 구입하지 않고 Visual Studio 구독 관리자가 할당하는 경우 GitHub Enterprise 계정을 만들고자 한다는 알림이 GitHub에 전송되지 않습니다.  구독이 할당되려면 먼저 GitHub Enterprise가 포함된 Visual Studio 구독을 **하나 이상 구입** 해야 합니다.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>GitHub Enterprise가 포함된 Visual Studio로 이동
표준 Visual Studio Enterprise 및 Visual Studio Professional 구독이 할당된 후 조직에서 GitHub Enterprise 번들이 포함된 Visual Studio 구독을 구매한 경우 관리 포털에는 기존 구독자를 GitHub Enterprise가 포함된 Visual Studio Enterprise 및/또는 GitHub Enterprise가 포함된 Visual Studio Professional로 이동할 수 있도록 돕는 기능이 포함되어 있습니다.  예를 들어 Visual Studio Professional 구독을 보유한 구독자는 GitHub Enterprise 구독이 포함된 Visual Studio Professional로 이동합니다. 왼쪽 막대 “개요” 패널에 다음 타일이 표시됩니다.

   > [!div class="mx-imgBorder"]
   > ![지금 이동 단추](_img/assign-github/move-now.png "'지금 이동'을 클릭하여 GitHub Enterprise가 포함된 Visual Studio 구독으로 업그레이드")

> [!IMPORTANT]
> 위에서 언급한 것처럼 기존 구독자 데이터, 기록 및 구독 ID는 유지 관리되며, 이 이동으로 인해 활성화한 혜택은 중단되지 않습니다.  
>
> (이 기능은 단계적으로 배포 중이며 조직에서 바로 사용하지 못할 수 있습니다.)

**지금 이동** 단추를 클릭하면 플라이아웃 패널이 표시되어 Enterprise 및/또는 Professional 구독을 이동하는 것에 대한 권장 사항이 제공됩니다.

   > [!div class="mx-imgBorder"]
   > ![플라이아웃 패널](_img/assign-github/fly-out.png)

이 타일에서 영향을 받는 구독자를 검토하고 이동이 완료된 후 이메일 알림을 보낼지 여부를 지정할 수 있습니다.  이 이메일은 구독자에게 혜택이 변경되지 않은 상태로 유지되고 GitHub에서 현재 상태를 설정하도록 권장합니다.  

**모든 구독자 이동** 단추를 클릭한 후 선택 사항을 확인하고 구독 이동이 완료될 때까지 몇 초 동안 기다립니다.  해당하는 경우 Professional 및 Enterprise에 대해 별도로 이 단계를 수행해야 합니다.  


## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>GitHub Enterprise 설치 프로세스가 포함된 Visual Studio란?
GitHub Enterprise는 Visual Studio 구독과 별도로 설정 및 관리됩니다. GitHub Enterprise가 포함된 Visual Studio 구독을 구입한 이후 GitHub Enterprise 계정 설정 프로세스는 [manage.visualstudio.com](https://manage.visualstudio.com)에서 계약을 설정하는 것과 병렬로 시작되지만 별도의 프로세스입니다. 이 GitHub Enterprise 계정을 설정하는 데 다소 시간이 걸릴 수 있습니다. 

회사에서 GitHub Enterprise 계정을 설정한 후 GitHub Enterprise가 포함된 Visual Studio 구독이 할당된 구독자는 GitHub에서 Visual Studio 구독이 연결되었음을 알리는 전자 메일을 받게 됩니다. 구독자는 이 이메일을 받은 후 GitHub 조직 관리자에게 연락하여 적절한 조직에 대한 초대를 받을 수 있습니다.

GitHub Enterprise 설정에 대한 자세한 내용은 [구독자 설명서](access-github.md)를 참조하세요.   

## <a name="manage-github-enterprise-subscriptions"></a>GitHub Enterprise 구독 관리
GitHub Enterprise 구독을 구매하면 GitHub는 고객과 협력하여 GitHub에 액세스하고 관리자를 식별할 조직을 만들고 구성하도록 돕습니다.  그러면 이러한 관리자는 관리자로 설정되었다는 알림을 받습니다.  

이 프로세스는 매우 복잡하기 때문에 조직 및 관리자가 완전히 설정되기 위해서는 구독을 구매한 후 며칠이 걸릴 수 있습니다.

GitHub는 클라우드 기반 GitHub.com 또는 온-프레미스 GitHub Enterprise 서버로 사용할 수 있습니다.  두 버전을 관리하는 프로세스가 다릅니다.  GitHub는 GitHub Enterprise 구독 관리에 도움이 되는 다양한 도움말 항목과 관리자 가이드를 제공합니다.  아래 선택한 항목의 링크를 제공했습니다.  

## <a name="support-resources"></a>지원 리소스

- [GitHub 문서](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)에서 GitHub 할당에 대해 자세히 알아보기
- [GitHub 도움말](https://help.github.com/en)에서 다양한 GitHub 항목에 대한 질문의 답을 찾습니다.
- [GitHub 커뮤니티 포럼](https://github.community/)에서 다른 GitHub 사용자의 도움을 받으세요.
- Visual Studio 구독에 대한 판매, 구독, 계정 및 요금 청구에 대한 지원을 받으려면 [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/)에 문의하세요.
- Visual Studio IDE, Azure DevOps Services 또는 기타 Visual Studio 제품이나 서비스와 관련하여 궁금한 점이 있나요?  [Visual Studio 지원](https://visualstudio.microsoft.com/support/)을 참조하세요.
- GitHub Enterprise에 대한 [기술 지원](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24)을 받으세요.   

## <a name="see-also"></a>참조

- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)

## <a name="next-steps"></a>다음 단계

Visual Studio 구독 관리에 대해 자세히 알아보세요.
- [개별 구독 할당](assign-license.md)
- [여러 구독 할당](assign-license-bulk.md)
- [구독 편집](edit-license.md)
- [구독 삭제](delete-license.md)
- [최대 사용량 확인](maximum-usage.md)

GitHub Enterprise가 포함된 Visual Studio 구독 관리에 대한 자세한 내용은 Visual Studio [구독 관리자 포털](https://visualstudio.microsoft.com/subscriptions-administration/)을 참조하세요.