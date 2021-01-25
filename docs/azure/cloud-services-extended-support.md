---
title: Cloud Services 사용 (확장 지원) (미리 보기)
description: 이제 Visual Studio에서 Azure Resource Manager를 사용 하 여 Cloud Services (확장 지원)를 만들고 배포 하는 방법을 알아봅니다.
author: ghogen
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: ff45cf05a6811c02881c26f76193d4c1f5a5e735
ms.sourcegitcommit: 7d34ab111614ae6bde5fb3c2bb91dd79e29a0a78
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98750234"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio-preview"></a>Visual Studio에서 Cloud Services (확장 지원) 만들기 및 배포 (미리 보기)

[Visual Studio 2019 버전 16.9](https://visualstudio.microsoft.com/vs/preview) (현재 미리 보기 상태)부터 Azure Resource Manager를 사용 하 여 클라우드 서비스에 대 한 작업을 수행할 수 있습니다 .이를 통해 Azure 리소스의 유지 관리 및 관리를 대폭 간소화 하 고 당국 수 있습니다. 이는 *Cloud Services (확장 지원)* 이라고 하는 새로운 Azure 서비스에서 사용 하도록 설정 됩니다. 기존 클라우드 서비스를 Cloud Services (확장 지원)에 게시할 수 있습니다. 이 Azure 서비스에 대 한 자세한 내용은 [Cloud Services (확장 지원) 설명서](/azure/cloud-services-extended-support/overview)를 참조 하세요.

## <a name="publish-to-cloud-services-extended-support"></a>Cloud Services에 게시 (확장 지원)

Cloud Services (연장 지원)에 기존 Azure 클라우드 서비스 프로젝트를 게시 하는 경우 클래식 Azure 클라우드 서비스에 게시 하는 기능을 계속 유지 합니다. Visual Studio 2019 버전 16.9 Preview 3 이상에서는 클래식 클라우드 서비스 프로젝트에 **게시 명령의 특수** 버전 **(확장 된 지원)** 이 있습니다. 이 명령은 **솔루션 탐색기** 의 바로 가기 메뉴에 표시 됩니다.

Cloud Services (확장 지원)에 게시 하는 경우 몇 가지 차이점이 있습니다. 예를 들어 **스테이징** 또는 **프로덕션** 에 게시 하 고 있는지 여부를 묻는 메시지는 표시 되지 않습니다. 이러한 배포 슬롯은 확장 지원 게시 모델에 포함 되지 않기 때문입니다. 대신 Cloud Services (확장 지원)을 사용 하 여 여러 배포를 설정 하 고 Azure Portal 배포를 교환할 수 있습니다. Visual Studio 도구를 사용 하면 16.9 Preview 3에서이를 설정할 수 있지만 이후 버전의 Cloud Services (확장 된 지원)를 사용할 때까지 교환 기능을 사용할 수 없으며 미리 보기 중에 배포 시 오류가 발생할 수 있습니다.

클래식 Azure 클라우드 서비스를 Cloud Services (확장 지원)에 게시 하기 전에 프로젝트에서 사용 하는 저장소 계정을 확인 하 고 저장소 V1 또는 저장소 V2 계정 인지 확인 합니다. 클래식 저장소 계정 유형은 배포 시 오류 메시지와 함께 실패 합니다. 진단에서 사용 하는 저장소 계정을 확인 해야 합니다. 진단 저장소 계정을 확인 하려면 [Azure Cloud Services 및 가상 컴퓨터에 대 한 진단 설정](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)을 참조 하세요. 서비스에서 클래식 저장소 계정을 사용 하는 경우 업그레이드할 수 있습니다. 범용 [v2 저장소 계정으로 업그레이드를](/azure/storage/common/storage-account-upgrade?tabs=azure-portal)참조 하세요.  저장소 계정 유형에 대 한 일반 정보는 [storage 계정 개요](/azure/storage/common/storage-account-overview)를 참조 하세요.

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Cloud Services에 클래식 Azure 클라우드 서비스 프로젝트를 게시 하려면 (확장 지원)

1. Cloud Services (확장 지원)는 현재 미리 보기 상태입니다. 다음과 같이 구독에 대한 기능을 등록합니다.

   ```azurepowershell-interactive
   Register-AzProviderFeature -FeatureName CloudServices -ProviderNamespace Microsoft.Compute
   ```

1. Azure Cloud Service (클래식) 프로젝트에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **게시 (확장 된 지원)**...을 선택 합니다. 첫 번째 화면에서 **게시 마법사** 가 열립니다.

   ![메뉴에서 게시 (확장 된 지원)를 선택 합니다.](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   **게시** 마법사가 나타납니다.

   ![로그인 페이지](./media/cloud-services-extended-support/publish-step1.png)

1. **계정** - 계정을 선택하거나 계정 드롭다운 목록에서 **계정 추가** 를 선택합니다.

1. **구독 선택** - 배포에 사용할 구독을 선택합니다.

1. **다음** 을 선택 하 여 **설정** 페이지로 이동 합니다.

   ![일반 설정](./media/cloud-services-extended-support/publish-settings.png)

1. **클라우드 서비스 (연장 지원)** -드롭다운을 사용 하 여 기존 클라우드 서비스 (확장 지원)를 선택 하거나 **새로 만들기** 를 선택 하 여 만듭니다. 데이터 센터는 각 클라우드 서비스 (확장 지원)에 대 한 괄호 안에 표시 됩니다. 클라우드 서비스의 데이터 센터 위치 (확장 지원)는 저장소 계정의 데이터 센터 위치와 동일 하 게 하는 것이 좋습니다.

   새 서비스를 만들도록 선택 하는 경우 **클라우드 서비스 만들기 (확장 지원)** 대화 상자가 표시 됩니다. 클라우드 서비스 (확장 지원)에 사용할 위치 및 리소스 그룹을 지정 합니다.

   ![클라우드 서비스 만들기 (확장 지원)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **빌드 구성** - **디버그** 또는 **릴리스** 중 하나를 선택합니다.

1. **서비스 구성** - **클라우드** 또는 **로컬** 중 하나를 선택합니다.

1. **저장소 계정** -이 배포에 사용할 저장소 계정을 선택 하거나 **새로 만들기를 만들어** 저장소 계정을 만듭니다. 지역은 각 저장소 계정에 대 한 괄호 안에 표시 됩니다. 스토리지 계정의 데이터 센터 위치는 클라우드 서비스의 데이터 센터 위치와 동일하게 설정(일반 설정)하는 것이 좋습니다.

   Azure Storage 계정은 애플리케이션 배포용 패키지를 저장합니다.

1. **Key vault** -이 클라우드 서비스에 대 한 암호를 포함 하는 주요 자격 증명 모음을 지정 합니다 (연장 지원). 이는 원격 데스크톱을 사용 하도록 설정 하거나 인증서를 구성에 추가 하는 경우에 사용할 수 있습니다.

1. **모든 역할에 대해 원격 데스크톱 사용** - 원격으로 서비스에 연결하려면 이 옵션을 선택합니다. 자격 증명을 지정 하 라는 메시지가 표시 됩니다.

   ![원격 데스크톱 설정](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. **다음** 을 선택 하 여 **진단 설정** 페이지로 이동 합니다.

   ![진단 설정](./media/cloud-services-extended-support/diagnostics-settings.png)

   진단을 사용 하면 Azure 클라우드 서비스 (연장 지원)의 문제를 해결할 수 있습니다. 진단에 대한 자세한 내용은 [Azure Cloud Services 및 Virtual Machines에서 진단 구성](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)을 참조하세요. Application Insights에 대한 자세한 내용은 [Application Insights란?](/azure/application-insights/app-insights-overview)을 참조하세요.

1. **다음** 을 선택 하 여 **요약** 페이지로 이동 합니다.

   ![요약](./media/cloud-services-extended-support/publish-summary.png)

1. **대상 프로필** - 선택한 설정에서 게시 프로필을 만들도록 선택할 수 있습니다. 예를 들어, 테스트 환경에 대한 하나의 프로필을 만들고 프로덕션용으로 다른 하나를 만들 수 있습니다. 이 프로파일을 저장하려면 **저장** 아이콘을 선택합니다. 마법사는 프로필을 만들고 Visual Studio 프로젝트에 저장합니다. 프로필 이름을 수정하려면 **대상 프로필** 목록을 연 다음 **관리...** 를 선택합니다.

   > [!Note]
   > 게시 프로필은 Visual Studio의 솔루션 탐색기에 표시 되 고 프로필 설정은 *azurepubxml* 확장이 있는 파일에 기록 됩니다. 설정은 XML 태그의 특성으로 저장됩니다.

1. 프로젝트 배포에 대한 설정을 모두 구성했으면 대화 상자의 아래쪽에서 **게시** 를 선택합니다. Visual Studio의 **Azure 활동 로그** 출력 창에서 프로세스 상태를 모니터링할 수 있습니다. **포털에서 열기** 링크를 선택 합니다. 

축하합니다! 클라우드 서비스 (확장 지원) 프로젝트를 Azure에 게시 했습니다. 동일한 설정으로 다시 게시 하려면 게시 프로필을 다시 사용 하거나 이러한 단계를 반복 하 여 새 항목을 만들 수 있습니다. 배포에 사용 되는 Azure Resource Manager (ARM) 템플릿 및 매개 변수는 *bin// \<configuration\> 게시* 폴더에 저장 됩니다.

## <a name="clean-up-azure-resources"></a>Azure 리소스 정리

이 자습서에 따라 만든 Azure 리소스를 정리 하려면 [Azure Portal](https://portal.azure.com)으로 이동 하 여 **리소스 그룹** 을 선택 하 고 클라우드 서비스를 만드는 데 사용한 리소스 그룹 (확장 지원)을 찾아 연 후 **리소스 그룹 삭제** 를 선택 합니다.

## <a name="next-steps"></a>다음 단계

**게시** 화면에서 **구성** 단추를 사용 하 여 CI (지속적인 통합)를 설정 합니다. 자세한 내용은 [Azure Pipelines 설명서](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)를 참조 하세요.
