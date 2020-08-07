---
title: 초과 할당된 라이선스 처리 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 03/03/2020
ms.topic: conceptual
description: 관리자가 초과 할당된 구독을 해결하는 방법을 알아봅니다.
ms.openlocfilehash: b518dc9300862e7c39af0489734734668097ef9f
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453717"
---
# <a name="over-allocated-subscriptions"></a>초과 할당된 구독
구독자가 추가된 후 주문자가 변경되어 결국 회사가 소유하는 라이선스보다 더 많은 구독이 할당되는 경우가 간혹 있습니다. 이를 "초과 할당"이라고 합니다.  

구독 할당을 보려면 왼쪽에서 맨 위 아이콘을 클릭하여 할당 창을 엽니다.  

> [!NOTE]
> 오픈 라이선스 프로그램에서는 초과 할당이 허용되지 않습니다.  또한 다른 프로그램이 이 정보를 포털에 다르게 표시할 수 있습니다.
>
> [!div class="mx-imgBorder"]
> ![과도하게 요청된 구독 알림](_img/over-claimed/over-claimed-alert.png "초과 할당 수는 개요에 나열되며 각 구독 유형의 그래프에 해시된 막대로 표시됩니다.")

디스플레이는 해시된 막대를 사용하여 초과 할당된 구독을 나타냅니다.  모든 구독 유형의 초과 할당 수가 맨 위의 개요 섹션에 포함되며, 각 구독 수준에도 자체 할당 상태가 표시됩니다.  

## <a name="resolve-over-allocated-subscriptions"></a>초과 할당된 구독 해결
초과 할당을 해결하는 몇 가지 방법은 다음과 같습니다.
- 대리점에 문의하여 추가 구독을 구매합니다.
- 연간 true-up 기간까지 기다렸다가 그 시점에 초과 할당된 구독에 대해 요금을 지불합니다. 
- 일부 구독 할당을 삭제합니다.  (true-up은 연중 어느 시점에서든 할당된 최대 구독 수를 기준으로 발생되므로, 이 경우에도 해당 연간 true-up에 대한 지불이 이루어져야 합니다.)

## <a name="billing-and-true-up"></a>청구 및 true-up
조직에 EA(기업계약)가 있는 경우 관리자는 구매 없이도 구독을 할당할 수 있고, 나중에 "true up"이라고 알려진 조정 프로세스를 통해 구독료를 지불할 수 있습니다.  초과 할당하면 "true-up" 기간 동안 사용자에게 할당된 최대 구독 수에 대한 비용이 조직에 청구됩니다.  이는 true-up이 이루어질 때 할당된 최대 구독 수가 더 이상 없더라도 마찬가지입니다.  최대 사용량 모니터링에 대한 자세한 내용은 [최대 사용량](maximum-usage.md) 항목을 참조하세요.

> [!Important]
> GitHub Enterprise가 포함된 Visual Studio Subscriptions가 Visual Studio 구독 관리자에 의해 할당되고 해당 구독의 구매가 없는 경우 조직 내의 GitHub Enterprise 관리자에게 해당 항목이 표시되지 않습니다. GitHub Enterprise 구독을 표시하려면 구독을 처음 할당할 때 **하나 이상의** GitHub Enterprise가 포함된 Visual Studio Professional 또는 GitHub Enterprise 구독이 포함된 Visual Studio Enterprise를 구매해야 합니다.
>
> 할당된 각 GitHub 구독에 대해 관리 포털에 할당된 GitHub 구독이 있는 해당 Visual Studio가 이 구독에 대한 라이선스 요구 사항을 준수하는지 확인하는 것은 고객의 책임입니다.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
- [GitHub Enterprise가 포함된 Visual Studio 구독](assign-github.md) 관리에 대해 자세히 알아봅니다.
- Visual Studio 구독에 대한 판매, 구독, 계정 및 요금 청구에 대한 지원을 받으려면 Visual Studio [구독 지원](https://visualstudio.microsoft.com/subscriptions/support/)에 문의하세요.