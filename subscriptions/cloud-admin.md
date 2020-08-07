---
title: 월간 구독에 대한 관리자 설정 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: how-to
description: 월간 구독에 대한 관리자 설정
ms.openlocfilehash: 7a0d28e4cd75749db430353234060f72a8f86485
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87434311"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Visual Studio 월간 구독에 대한 관리자 설정

Visual Studio 월간 구독은 관리자에 의해 관리됩니다. 이러한 개인들은 구독을 할당하고 할당을 편집하고 구독을 추가 또는 삭제하고 다른 구독 관리 작업을 수행할 수 있습니다.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Azure 구독 소유자가 첫 번째 관리자

Visual Studio 월간 구독을 구매하는 경우 구매하는 데 사용된 Azure 구독의 소유자로서 해당 구독에 대한 관리자로 자동 설정됩니다.

[Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)를 통하거나 클라우드 솔루션 공급자에게 문의하여 월간 구독을 구매할 수 있습니다. Visual Studio Marketplace를 통해 구매하는 경우 구매 경험 끝에 사용자를 관리할 기회가 제공됩니다. 해당 옵션을 선택하면 Visual Studio 구독 관리 포털([https://manage.visualstudio.com](https://manage.visualstudio.com))로 이동합니다.

구독을 구입했다면 언제든 [관리 포털](https://manage.visualstudio.com)을 방문할 수 있습니다. 포털에 로그인하고 왼쪽 위 모서리에서 적절한 Azure 구독을 선택합니다.

월간 구독을 구매하는 데 사용된 Azure 구독의 소유자로서 추가 관리자를 할당할 수 있습니다.

## <a name="add-administrators"></a>관리자 추가

관리자를 추가하려면

1. [portal.azure.com](https://portal.azure.com)에서 Azure Portal에 연결합니다.
2. Visual Studio 월간 구독을 구매하는 데 사용된 계정으로 로그인합니다.
3. **Azure 서비스**에서 **비용 관리 + 청구**를 선택합니다.
   > [!div class="mx-imgBorder"]
   > ![Azure 서비스에서 비용 관리 + 청구 선택](_img/cloud-admin/azure-cost-billing.png "Azure 서비스 그룹에서 Cost Management 선택")
4. **내 구독** 목록에서 구매하는 데 사용한 Azure 구독을 선택합니다.
   > [!div class="mx-imgBorder"]
   > ![구독 선택](_img/cloud-admin/subscription-list.png "구입 시 사용할 Azure 구독을 선택합니다.")
5. 왼쪽 탐색 창에서 목록의 상단 부근에 있는 **IAM(액세스 제어)** 을 클릭합니다.
6. 창의 상단에 있는 **추가** 탭을 클릭합니다.
7. **역할 할당 추가**를 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![액세스 제어, 추가, 역할 할당 추가 선택](_img/cloud-admin/access-control-add.png "왼쪽 목록에서 액세스 제어를 선택하고 추가를 선택합니다.")
8. 오른쪽에 있는 플라이아웃 창에서 창 상단의 **역할** 드롭다운 목록을 클릭하고 아래로 스크롤하여 **사용자 액세스 관리자**를 선택합니다.
9. 사용자 목록에서 아래로 스크롤해 관리자로 만들려는 사용자를 선택합니다. 
   > [!div class="mx-imgBorder"]
   > ![역할, 사용자 액세스 관리 선택](_img/cloud-admin/add-role-user-access-admin.png "역할을 선택하고 사용자 액세스 관리자를 선택한 다음 사용자의 이름을 선택하여 관리자로 지정합니다.")
10. **저장**을 클릭합니다.
11. **역할 할당** 탭을 클릭하여 선택된 사용자가 사용자 액세스 관리자로 표시되는지 확인합니다.

새 관리자는 이제 [관리 포털](https://manage.visualstudio.com)에 로그인하여 페이지의 왼쪽 위 모서리에 있는 목록에서 월간 구독을 구매하는 데 사용된 동일한 Azure 구독을 선택하고 이러한 구독을 관리할 수 있습니다.

> [!NOTE]
> 관리자로 설정하지 않은 월간 구독을 편집할 수 있는 액세스 권한이 사용자에게 있는 경우에는 사용자는 기본 Azure 구독에서 구독을 관리할 수 있는 역할을 가질 수 있습니다. 해당 역할에는 소유자, 기여자, 서비스 관리자 또는 공동 관리자가 포함됩니다. 자세한 내용은 [청구 관리자 추가](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts)를 참조하세요.

Visual Studio 월간 구독에 대한 자세한 내용은 구독 구입에서 [개요](vscloud-overview.md)를 참조하세요. Visual Studio 월간 구독을 구매하려면 [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)에서 Visual Studio Marketplace를 방문하세요.

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



