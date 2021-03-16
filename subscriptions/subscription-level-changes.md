---
title: Visual Studio 구독 수준 변경의 영향 | Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: bb2fa359-8170-4db0-a0c5-d49fc692b0aa
ms.date: 03/05/2021
ms.topic: conceptual
description: Visual Studio 구독 수준을 업그레이드 또는 다운그레이드할 때의 영향에 대해 알아봅니다.
ms.openlocfilehash: ac4355149ba66cd06ae5c1abaeb57e7065631050
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102250144"
---
# <a name="what-happens-when-you-change-visual-studio-subscription-levels"></a>Visual Studio 구독 수준을 변경하면 어떻게 됩니까?
Visual Studio 구독에서 사용할 수 있는 소프트웨어, 도구, 서비스 및 기타 혜택은 구독 수준에 따라 다릅니다.  일반적으로 구독 수준이 높을수록 제공되는 혜택이 더욱 많습니다.  

하나의 구독 수준에서 시작하여 다른 수준으로 증가(업그레이드) 또는 감소(다운그레이드)하는 시나리오가 있을 수 있습니다.  이러한 시나리오의 예는 다음과 같습니다.
- 보다 완전한 기능을 갖춘 Visual Studio IDE 버전이 필요하거나 더욱 광범위한 소프트웨어 다운로드 선택에 액세스하기로 결정한 경우 업그레이드를 선택합니다. 
- 회사의 구독 관리자는 현재 역할이나 프로젝트, 또는 회사의 구매 계획 변경에 따라 구독 수준을 변경할 수 있습니다. 예를 들어 회사에서 비용 절감을 위해 구매하는 구독의 조합을 변경할 수 있습니다.  

업그레이드 또는 다운그레이드 여부 및 보유한 구독 수준에 따라 새 구독의 혜택을 이용하기 위해 조치를 취해야 할 수 있습니다.

## <a name="how-do-my-benefits-change"></a>혜택은 어떻게 변경됩니까?
특정 혜택에 대한 변경 사항은 혜택 자체에 따라 다릅니다.  몇 가지 예시를 살펴보고 업그레이드 및 다운그레이드의 영향을 각각 설명하겠습니다.

### <a name="visual-studio-ide"></a>Visual Studio IDE
구독에 포함된 Visual Studio 버전에 대한 자세한 내용은 [Visual studio 구독 혜택 페이지](https://visualstudio.microsoft.com/vs/benefits/)를 참조하세요. 구독에 포함된 버전 간의 차이점에 대한 자세한 내용은 [Visual Studio 2019 버전 비교](https://visualstudio.microsoft.com/vs/compare/) 페이지를 참조하세요.
 
업그레이드: 새 구독에서 제공되는 IDE 수준에 액세스할 수 있습니다.  이를 사용하려면 더 낮은 버전을 제거하고 새 버전을 설치하는 것이 좋습니다.  

다운그레이드: 더 높은 구독 수준에서 제공되는 버전에 대한 영구 사용 권한을 계속 보유합니다.  하지만 로그인하여 해당 버전의 IDE에 액세스할 수 없습니다. 따라서 더 높은 수준의 구독에 대한 액세스를 잃기 **전에** 제품 키를 사용하여 활성화해야 합니다.  구독자 포털의 [제품 키 페이지](https://my.visualstudio.com/productkeys)를 방문하여 제품 키를 가져올 수 있습니다.  Visual Studio에 대한 제품 키를 이미 요청한 경우 요청한 키의 목록을 내보낼 수도 있습니다. [제품 키 찾기 및 요청](find-keys.md)에 대해 자세히 알아보세요.

### <a name="individual-azure-credits"></a>개별 Azure 크레딧
개별 Azure 크레딧의 할당량은 구독 수준에 따라 다릅니다.  구독 수준에 따라 매달 크레딧($0~$150)을 받을 수 있습니다.  

Visual Studio 구독을 변경하는 경우 발생할 수 있는 세 가지 시나리오가 있습니다.  잠재적 업그레이드 또는 다운그레이드 외에도, 회사의 구독 관리자는 현재 사용 중인 것과 동일한 수준에서 구독을 할당하지만 다른 구독 ID를 사용할 수 있습니다.  이러한 세 가지 경우 모두 Azure 구독에 대한 영향은 동일 합니다. 개별 크레딧의 양이 변경될 수 있습니다. 

Visual Studio 구독을 변경하면 크레딧을 수령하는 Azure 구독에 대한 연결이 중단되며 새 구독의 혜택을 활성화하면 새 Azure 구독이 생성됩니다.  이러한 상황이 발생하면 이전 Azure 구독은 최종적으로 비활성화됩니다.  이를 방지하려면 다음 해결 방법 중 하나를 사용합니다.
- 구독을 종량제로 변환합니다.  자세한 내용은 [Azure DevTest 종량제 구독 문서](vs-azure-payg.md)를 참조하세요.  신용 카드와 같은 결제 수단을 이 구독에 연결해야 합니다. 
- 새 Visual Studio 구독 혜택을 사용하여 새 Azure 구독을 만들고 이전 Azure 구독의 기존 Azure 자산을 새 Azure 구독에 이동합니다. 
  > [!IMPORTANT]
  > Azure 자산을 새 Azure 구독으로 이동하거나 기존 Azure 구독을 종량제로 변경하여 기존 Azure 자산의 손실을 방지하는 것이 중요합니다. 
 
### <a name="software-downloads"></a>소프트웨어 다운로드
사용 가능한 소프트웨어 다운로드는 구독 수준에 따라 다릅니다.  자세한 내용은 [사용 가능한 소프트웨어 다운로드 목록](software-download-list.md) 문서를 참조하세요. 

  > [!TIP] 
  > [다운로드 페이지](https://my.visualstudio.com/downloads)에 표시되는 소프트웨어 타이틀 목록은 로그인 이메일 주소에 할당한 가장 높은 구독 수준에 따라 다릅니다.  **가장 높은** 구독 수준에서 사용할 수 있는 모든 타이틀이 표시됩니다.  예를 들어 Visual Studio Enterprise 구독과 Visual Studio Dev Essentials 멤버 자격이 있는 경우 Dev Essentials 멤버 자격으로 로그인한 경우에도 Enterprise 구독에 포함된 모든 타이틀이 표시됩니다.  

### <a name="other-benefits"></a>기타 장점 
구독 수준 변경이 다른 혜택에 미치는 영향도 크게 다를 수 있습니다.  

#### <a name="benefits-with-a-fixed-length"></a>고정 기간의 이점
파트너가 제공하는 많은 혜택에는 고정 기간이 있습니다.  구독 수준 변경 전에 이를 활성화한 경우 대부분이 영향을 받지 않으며 정상 기간이 끝날 때까지 계속 사용할 수 있습니다.  예를 들어 Enterprise 구독의 일부로 교육 혜택에 6개월 구독을 활성화하고, Visual Studio 구독이 Visual Studio Professional으로 다운그레이드된 경우 학습 구독의 기간은 그대로 유지됩니다.  

#### <a name="benefits-that-require-authentication"></a>인증을 요구하는 혜택
Visual Studio에 로그인할 때마다 인증된 혜택을 사용하는 경우 구독 수준을 다운그레이드하면 이러한 혜택을 사용할 수 없습니다.  

#### <a name="benefits-that-are-not-available-in-lower-subscription-levels"></a>더 낮은 구독 수준에서 사용할 수 없는 혜택
현재 구독에서 제공되지만 다운그레이드되는 구독에서 제공되지 않는 혜택을 사용하는 경우 이러한 혜택을 이용하지 못할 수 있습니다.  

## <a name="support-resources"></a>지원 리소스
- Visual Studio 구독에 대한 판매, 구독, 계정 및 요금 청구에 대한 지원을 받으려면 Visual Studio [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/)에 문의하세요.
- Visual Studio IDE, Azure DevOps 또는 기타 Visual Studio 제품이나 서비스와 관련하여 궁금한 점이 있나요?  [Visual Studio 지원](https://visualstudio.microsoft.com/support/)을 참조하세요.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)

## <a name="next-steps"></a>다음 단계
- [Azure DevOps](https://azure.microsoft.com/services/devops/) 기능에 대한 자세한 정보
- [버전별 Visual Studio IDE 기능](https://visualstudio.microsoft.com/vs/compare/)에 대한 자세한 정보