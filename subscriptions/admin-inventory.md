---
title: 사전 프로덕션 환경의 인벤토리 | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/06/2020
ms.topic: conceptual
description: 관리자의 사전 프로덕션 인벤토리 수행 책임에 대해 알아봅니다.
ms.openlocfilehash: dc307d9d2f83666c6648a35b3e28a81da2de5c38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80232765"
---
# <a name="inventory-of-pre-production-environment"></a>사전 프로덕션 환경의 파악
Visual Studio 구독은 디바이스가 아닌 사용자를 계산하여 자산 관리를 간소화합니다.

Visual Studio 관리자는 **특정한 명명된 개인**에게 Visual Studio 구독을 할당해야 합니다. Dev1, Dev2 등의 명명 규칙이나 "FeatureTeam" 등의 팀 이름 사용은 **허용되지 않습니다**.

사전 프로덕션 환경의 파악을 단순화하는 몇 가지 방법이 있습니다.
- 사용자 할당을 검토합니다. Microsoft는 Visual Studio 구독 할당을 추적하는 데 도움이 되는 [Visual Studio 관리 포털](https://manage.visualstudio.com/)이라는 웹 사이트를 제공합니다.
- 온-프레미스 또는 클라우드 기반 Active Directory를 사용하여 사용자를 나열합니다. Active Directory를 사용하여 사용자 액세스를 관리하는 경우 해당 디렉터리의 구성원으로 개발 및 테스트 사용자를 식별할 수 있습니다.
- 자동화된 도구를 사용하여 시스템을 파악합니다. 소프트웨어 자산을 관리하고 프로덕션 환경에서 사전 프로덕션 환경을 구별하는 데 도움이 되는 소프트웨어 인벤토리 도구를 사용해야 할 수 있습니다. Microsoft System Center를 이용하는 많은 고객은 인벤토리 프로세스의 이 부분을 자동화하는 데 도움이 되는 명명 규칙을 만듭니다.
- 수동 조정을 통해 도움을 얻습니다. 개발 및 테스트 사용자를 개발 및 테스트 환경과 조정시키는 데 도움이 되도록 직원의 협조를 요청합니다.

## <a name="resources"></a>리소스
- [Visual Studio 라이선스 백서](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Visual Studio 관리 및 구독 지원](https://visualstudio.microsoft.com/support/support-overview-vs)
- [볼륨 라이선스 약관](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>참고 항목
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
관리자의 책임에 대해 자세히 알아봅니다.
- [관리자 책임](admin-responsibilities.md)
- [대규모 팀 및 외부 계약업체 관리](manage-teams.md)
- [사용자 할당 추적 및 주문 처리](assignments-orders.md)
- [최대 사용량](maximum-usage.md)으로 구매 커밋 추적



