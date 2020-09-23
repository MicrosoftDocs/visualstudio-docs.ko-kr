---
title: Visual Studio 구독자용 Azure DevOps 혜택 | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: fe826200-9600-4b29-a64e-0d66ba3caf3d
ms.date: 07/22/2020
ms.topic: conceptual
description: Azure DevOps를 Visual Studio 구독자로 사용할 수 있는 방법을 알아봅니다.
ms.openlocfilehash: f449d39866cb5891f2b378acffdd84b38b6408c7
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005088"
---
# <a name="azure-devops-benefits-for-visual-studio-subscribers"></a>Visual Studio 구독자용 Azure DevOps 혜택
적극적인 Visual Studio 구독자는 구독 혜택에 포함된 Azure DevOps의 다양한 기능을 사용할 수 있습니다. 조직을 직접 만들었든 또는 다른 사용자에 의해 추가되었든, 멤버로 속해 있는 각 Azure DevOps 조직에서 이러한 동일한 기능을 사용할 수 있습니다.

## <a name="sign-in"></a>로그인

   > [!div class="mx-imgBorder"]
   > ![Azure DevOps 타일](_img/vs-azure-devops/vs-azure-devops-tile.png)

   
Visual Studio 구독을 활성화하는 데 사용한 것과 동일한 ID 또는 [대체 ID](vs-alternate-identity.md)를 사용하여 Azure DevOps에 로그인하면 자동으로 인식됩니다.  이 방식으로 회사 또는 학교 계정(Visual Studio, Microsoft 365 또는 회사나 학교 네트워크에 로그인할 때 사용하는 계정)을 추가할 수 있으며, 사용자의 개인 계정과 회사 또는 학교 계정 모두를 사용하여 Azure DevOps에 액세스할 수도 있습니다.

[무료 Azure DevOps 조직에 등록](https://visualstudio.microsoft.com/team-services/)

## <a name="eligibility"></a>자격
| 구독 수준                                                 |     채널                                            | 이점                                                          | 갱신 가능?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise(표준, 월간 클라우드)   | VL, Azure, 일반 정품, 선택한 NFR<sup>1</sup>  | Azure Boards & Repos(Basic<sup>2</sup>), Azure Test Plans, 자체 호스팅 병렬 작업 [자세한 정보](/azure/devops/organizations/security/access-levels?view=azure-devops)     |  예          |
| GitHub Enterprise가 포함된 Visual Studio Enterprise   | VL| Azure Boards & Repos(Basic<sup>2</sup>), Azure Test Plans, 자체 호스팅 병렬 작업 [자세한 정보](/azure/devops/organizations/security/access-levels?view=azure-devops) |  예          |
| Visual Studio Professional(표준, 월간 클라우드) | VL, Azure, 일반 정품                                        | Azure Boards & Repos(Basic<sup>2</sup>) [자세한 정보](/azure/devops/organizations/security/access-levels?view=azure-devops)                                                            |  예          |
| GitHub Enterprise가 포함된 Visual Studio Professional | VL| Azure Boards & Repos(Basic<sup>2</sup>) [자세한 정보](/azure/devops/organizations/security/access-levels?view=azure-devops)                                                            |  예          |
| Visual Studio Test Professional(표준)                         | VL, 일반 정품                                              | Azure Boards & Repos(Basic<sup>2</sup>), Azure Test Plans [자세한 정보](/azure/devops/organizations/security/access-levels?view=azure-devops)                                             |  예          |
| MSDN 플랫폼(표준)                                          | VL, 일반 정품                                              | Azure Boards & Repos(Basic<sup>2</sup>), Azure Test Plans [자세한 정보](/azure/devops/organizations/security/access-levels?view=azure-devops)                                             |  예          |
||

<sup>1</sup>  포함:  *NFR(전매금지), MVP(Most Valuable Professional), RD(Regional Director), VSIP(Visual Studio Industry Partner), Microsoft 파트너 네트워크(Enterprise), BizSpark, MCT Software & Services Developer, FTE. 제외: MCT Software & Services, Imagine.*

<sup>2</sup> Basic 플랜에는 릴리스 파이프라인 및 다단계 CD(지속적인 배포) 파이프라인을 정의하고 승인과 게이트를 사용하여 배포를 제어하는 것이 포함됩니다. Pipelines 미리 보기 기능에 대한 무료 액세스가 사용하도록 설정된 경우 관련자는 모든 Azure Pipelines 기능에 액세스할 수 있습니다. *플랜에 포함된 기능에 대한 자세한 내용은 Azure의 [액세스 수준 정보 페이지](/azure/devops/organizations/security/access-levels?view=azure-devops)를 참조하세요.*

> [!NOTE]
> Microsoft는 더 이상 Visual Studio Professional 연간 구독 및 클라우드 구독에 Visual Studio Enterprise 연간 구독을 제공하지 않습니다. 기존 고객 환경 및 해당 구독의 갱신, 증가, 감소 또는 취소 기능은 변경되지 않습니다. 새 고객은 [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/)으로 이동하여 Visual Studio를 구입하기 위한 다양한 옵션을 살펴보세요.

어떤 구독을 사용하고 있는지 확실하지 않나요?  자신에게 할당된 모든 구독을 보려면 [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs)에 연결합니다.
일부 구독이 표시되지 않으면 하나 이상이 다른 전자 메일 주소에 할당되어 있을 수 있습니다.  해당 구독을 보려면 해당 전자 메일 주소로 로그인해야 합니다.

## <a name="frequently-asked-questions"></a>질문과 대답
### <a name="q-as-a-visual-studio-enterprise-subscriber-do-i-get-additional-parallel-jobs-for-tfs-and-azure-pipelines"></a>Q: Visual Studio Enterprise 구독자는 TFS 및 Azure Pipelines에 대한 추가 병렬 작업을 가져올 수 있나요?
A:  예. Visual Studio Enterprise 구독자는 Team Foundation Server 2017 이상 버전에서 하나의 병렬 작업을, 그리고 자신이 구성원으로 속해 있는 Azure DevOps Services 조직에서 하나의 자체 호스팅 병렬 작업을 가져옵니다.

## <a name="support-resources"></a>지원 리소스
- Visual Studio 구독에 대한 판매, 구독, 계정 및 요금 청구에 대한 지원을 받으려면 Visual Studio [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/)에 문의하세요.
- Visual Studio IDE, Azure DevOps 또는 기타 Visual Studio 제품이나 서비스와 관련하여 궁금한 점이 있나요?  [Visual Studio 지원](https://visualstudio.microsoft.com/support/)을 참조하세요.
- [Azure DevOps 설명서](/azure/devops/)를 참조하세요.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)

## <a name="next-steps"></a>다음 단계
Azure DevOps 기능에 대한 자세한 정보:
- [Azure Boards & Repos(기본 플랜)](https://azure.microsoft.com/services/devops/compare-features/)
- [Azure Test Plans](https://marketplace.visualstudio.com/items?itemName=ms.vss-testmanager-web)
- [Azure Artifacts](https://marketplace.visualstudio.com/items?itemName=ms.feed)

[Azure DevTest 개별 크레딧](vs-azure.md)을 활성화하는 방법을 알아보세요.