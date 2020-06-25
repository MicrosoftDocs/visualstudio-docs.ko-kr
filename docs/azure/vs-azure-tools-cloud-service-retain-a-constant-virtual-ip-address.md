---
title: Azure 클라우드 서비스의 가상 IP 주소를 일정하게 유지
description: Azure 클라우드 서비스의 가상 IP 주소(VIP)가 변경되지 않도록 하는 방법에 대해 알아봅니다.
author: ghogen
manager: jillfra
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e7e7d9a6c1c417b3802ef1f94ac51fec14bf682a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280852"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Azure 클라우드 서비스의 가상 IP 주소를 일정하게 유지
Azure에서 호스팅되는 클라우드 서비스를 업데이트하는 경우 서비스의 가상 IP 주소(VIP)가 변경되지 않는지 확인해야 할 수 있습니다. 많은 도메인 관리 서비스에서 도메인 이름을 등록하는 데 도메인 이름 시스템(DNS)을 사용합니다. DNS는 VIP가 동일하게 유지되는 경우에만 작동합니다. Azure 도구에서 **게시 마법사** 를 사용하여 클라우드 서비스를 업데이트할 때 VIP가 변경되지 않는지 확인할 수 있습니다. 클라우드 서비스에 대한 DNS 도메인 관리를 사용하는 방법에 대한 자세한 내용은 [Azure 클라우드 서비스에 대한 사용자 지정 도메인 이름 구성](/azure/cloud-services/cloud-services-custom-domain-name-portal)을 참조하세요.

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>VIP를 변경하지 않고 클라우드 서비스 게시
클라우드 서비스의 VIP는 프로덕션 환경과 같은 특정 환경에서 Azure에 처음 배포할 때 할당됩니다. VIP는 배포를 명시적으로 삭제하거나 배포 업데이트 프로세스에 의해 암시적으로 삭제된 경우에만 변경됩니다. VIP를 유지하려면 배포를 삭제해서는 안되며 Visual Studio에서 배포를 자동으로 삭제하지 않는지 확인해야 합니다.

여러 배포 옵션을 지원하는 **게시 마법사**에서 배포 설정을 지정할 수 있습니다. 새로 배포 또는 업데이트 배포를 증분 또는 동시에 진행하도록 지정할 수 있습니다. 두 종류의 업데이트 배포 모두 VIP를 유지합니다. 이러한 다양한 유형의 배포에 대한 정의는 [Azure 애플리케이션 게시 마법사](vs-azure-tools-publish-azure-application-wizard.md)를 참조하세요. 또한 오류가 발생하는 경우 클라우드 서비스의 이전 배포를 삭제할지 제어할 수 있습니다. 해당 옵션을 바르게 설정하지 않은 경우 VIP가 예기치 않게 변경될 수 있습니다.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>VIP를 변경하지 않고 클라우드 서비스 업데이트
1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

2. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭합니다. 바로 가기 메뉴에서 **게시**를 선택합니다.

    ![게시 메뉴](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. **Azure 애플리케이션 게시** 대화 상자에서 배포할 구독을 선택하고 필요합니다. 필요한 경우 로그인하고 **다음**을 선택합니다.

    ![Azure 애플리케이션 게시 로그인 페이지](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. **일반 설정** 탭에서 배포 중인 클라우드 서비스의 이름, **환경**, **빌드 구성**및 **서비스 구성** 이 모두 올바른지 확인 합니다.

    ![Azure 애플리케이션 게시 일반 설정 탭](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. **고급 설정** 탭에서 **배포 레이블** 및 **Storage 계정**이 올바른지 확인합니다. **실패 시 배포 삭제** 확인란의 선택을 취소했는지 확인하고, **배포 업데이트** 확인란을 선택했는지 확인합니다. **실패 시 배포 삭제** 확인란의 선택을 취소 하 여 배포 중에 오류가 발생 하는 경우 VIP가 손실 되지 않도록 합니다. **배포 업데이트** 확인란을 선택하면 애플리케이션을 다시 게시할 때 배포가 삭제되지 않고 VIP가 손실되지 않았는지 확인할 수 있습니다.

    ![Azure 애플리케이션 게시 고급 설정 탭](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. 역할을 업데이트하는 방법을 자세히 지정하려면 **배포 업데이트** 옆의 **설정**을 선택합니다. **증분 업데이트** 또는 **동시 업데이트**를 선택한 다음 **확인**을 선택합니다. **증분 업데이트**를 선택하면 애플리케이션의 각 인스턴스를 하나씩 차례로 업데이트하므로 해당 애플리케이션을 항상 사용할 수 있습니다. **동시 업데이트**를 선택하면 애플리케이션의 모든 인스턴스를 동시에 업데이트합니다. 동시 업데이트는 신속하게 진행되지만 업데이트 과정 중에 서비스를 사용할 수 없습니다. 작업을 마쳤으면 **다음**을 선택합니다.

    ![Azure 애플리케이션 게시 배포 설정 페이지](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. **Azure 애플리케이션 게시** 대화 상자에서 **요약** 페이지가 표시될 때까지 **다음**을 선택합니다. 설정을 확인한 다음 **게시**를 선택합니다.

    ![Azure 애플리케이션 게시 요약 페이지](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>다음 단계
- [Visual Studio Azure 애플리케이션 게시 마법사 사용](vs-azure-tools-publish-azure-application-wizard.md)
