---
title: Visual Studio 구독자용 ID
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 07/19/2019
ms.topic: conceptual
description: Azure DevOps 및 Azure를 사용하기 위해 Visual Studio 구독에 대한 대체 ID를 추가하는 방법
ms.openlocfilehash: 5eee6c1d59141c1975a6039f2ab9256b4c9dc735
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005716"
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio 구독자용 ID
Visual Studio 구독을 활성화하면 Visual Studio 구독을 사용하여 활성화하는 동안 사용했던 ID(또는 로그인)을 연결합니다. 이러한 방식으로 [Visual Studio 구독자 포털](https://my.visualstudio.com?wt.mc_id=o~msft~docs), Azure DevOps 및 Azure에서 사용자를 인식할 수 있습니다.

Azure DevOps에서는 로그인할 때마다 Visual Studio 구독 상태를 확인하고 멤버인 사용자의 각 조직 내에서 자동으로 사용자에게 기능을 부여합니다.
이러한 기능은 구독자 혜택으로 포함되므로 Visual Studio 구독에 연결된 ID를 사용하는 경우 모든 Azure DevOps 조직의 멤버로 사용자를 무료로 추가합니다.

Azure에서 구독자 혜택인 [월간 Azure DevTest 개별 크레딧](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)을 활성화하는 경우 Visual Studio 구독 상태를 확인합니다.

[Visual Studio 구독자 포털](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 내에서 활성화 동안 사용했던 ID 외에도 **대체 ID**를 추가할 수 있습니다. 구독을 활성화하기 위해 Microsoft 계정을 사용하는 경우 대체 ID를 추가할 수 있습니다. 이 방식으로 회사 또는 학교 계정(Visual Studio, Microsoft 365 또는 회사나 학교 네트워크에 로그인할 때 사용하는 계정)을 추가할 수 있으며, 사용자의 개인 계정과 회사 또는 학교 계정 모두를 사용하여 Azure DevOps에 액세스할 수도 있습니다.

## <a name="add-an-alternate-account-to-your-subscription"></a>구독에 대체 계정 추가
대체 계정을 Visual Studio 구독에 추가하면 구독이 할당된 ID 외에 다른 ID로 Azure DevOps 및 Azure 같은 구독 혜택에 액세스할 수 있습니다. 이전에 이 기능은 VS(Visual Studio) 구독이 MSA(Microsoft 계정)에 할당된 경우에만 사용할 수 있었습니다. Azure AD(Azure Active Directory)에서 회사 또는 학교 계정에 대해 이 기능을 확장했습니다.

이 경우 다른 계정에 구독의 복사본을 제공하는 것이 아니라 대체 계정으로 두 가지 혜택에 액세스하는 기능만 제공합니다.

모든 구독에 대해 “회사 또는 학교 계정”을 추가할 수 있으므로 로그인이 필요한 혜택(VS IDE, Azure DevOps 및 Azure)으로 해당 계정을 사용할 수 있습니다.

### <a name="add-the-alternate-account"></a>대체 계정 추가
1. Microsoft 계정(https://my.visualstudio.com) 을 사용하여 Visual Studio 구독자 포털에 로그인합니다.
2. **구독** 탭을 선택합니다.
3. **대체 계정 추가**를 선택합니다.
4. 회사 또는 학교 계정을 추가합니다.
    > [!div class="mx-imgBorder"]
    > ![회사 또는 학교 계정 추가](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. 회사 또는 학교 계정을 사용하여 Azure DevOps(https://{youraccount}.visualstudio.com)에 로그인합니다.

대체 계정이 Visual Studio 구독에 추가되어 두 ID가 대체 계정으로 로그인해야 하는 구독의 혜택(IDE, Azure DevOps 및 Azure)을 활용할 수 있습니다.

## <a name="faq"></a>FAQ

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Q:  Azure DevOps에서 나를 Visual Studio 구독자로 인식하지 못하는 것은 무엇 때문인가요?

A: 기본 또는 대체 ID를 사용하여 로그인할 때 Azure DevOps는 사용자의 구독을 자동으로 인식해야 합니다. 그렇지 않다면 몇 가지를 시도해볼 수 있습니다.

* [Azure DevOps](vs-azure-devops.md#eligibility)를 혜택으로 포함하는 활성화된 Visual Studio 구독이 있는지 확인합니다.

* 사용하는 로그인/ID가 Visual Studio 구독을 위한 기본 또는 대체 ID인지 확인합니다.

* Azure DevOps에 로그인하기 전에 한 번 이상 [Visual Studio 구독자 포털](https://my.visualstudio.com?wt.mc_id=o~msft~docs)을 방문합니다.

그래도 Azure DevOps에서 여전히 사용자의 구독을 인식하지 못하는 경우 [Azure DevOps 고객 지원팀](https://azure.microsoft.com/support/devops/)에 문의하세요.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)

## <a name="next-steps"></a>다음 단계 
Azure, Azure DevOps 또는 Visual Studio IDE 사용에 대한 자세한 내용은 다음 리소스를 참조하세요.
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)