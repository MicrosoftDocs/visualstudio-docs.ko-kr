---
title: Azure 애플리케이션 게시 마법사 사용 | Microsoft Docs
description: Visual Studio Azure 애플리케이션 게시 마법사에서 다양한 설정을 구성하는 방법에 대해 알아봅니다.
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: a75e83e3fb2ac43b4fa1d658c7e2a08ec1ae3c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62831345"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Visual Studio Azure 애플리케이션 게시 마법사 사용

Visual Studio에서 웹 애플리케이션을 개발한 후 **Azure 애플리케이션 게시** 마법사를 사용하여 해당 애플리케이션을 Azure 클라우드 서비스에 게시할 수 있습니다.

> [!Note]
> 이 문서는 웹 사이트가 아닌 클라우드 서비스에 배포에 대한 것입니다. 웹 사이트에 배포에 대한 자세한 내용은 [Azure 웹 사이트에 배포하는 방법](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false)을 참조하세요.

## <a name="accessing-the-publish-azure-application-wizard"></a>Azure 애플리케이션 게시 마법사 액세스

사용하는 Visual Studio 프로젝트 형식에 따라 다음 두 가지 방법으로 Azure 애플리케이션 게시 마법사에 액세스할 수 있습니다.

**Azure 클라우드 서비스 프로젝트가 있는 경우:**

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **게시**를 선택합니다.

**Azure에서 사용되지 않는 웹 애플리케이션 프로젝트가 있는 경우:**

1. Visual Studio에서 Azure 클라우드 서비스 프로젝트를 만들거나 엽니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **변환** > **Azure 클라우드 서비스 프로젝트로 변환**을 선택합니다.

1. **솔루션 탐색기**에서 새로 만든 Azure 프로젝트를 마우스 오른쪽 단추로 클릭하고, 상황에 맞는 메뉴에서 **게시**를 선택합니다.

## <a name="sign-in-page"></a>로그인 페이지

![로그인 페이지](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**계정** - 계정을 선택하거나 계정 드롭다운 목록에서 **계정 추가**를 선택합니다.

**구독 선택** - 배포에 사용할 구독을 선택합니다.

## <a name="settings-page---common-settings-tab"></a>설정 페이지 - 일반 설정 탭

![일반 설정](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**클라우드 서비스** - 드롭다운을 사용하여 기존 클라우드 서비스를 선택하거나 **&lt;새로 만들기>** 를 선택하고 클라우드 서비스를 만듭니다. 데이터 센터가 각 클라우드 서비스에 대한 괄호 안에 표시됩니다. 클라우드 서비스의 데이터 센터 위치는 스토리지 계정의 데이터 센터 위치와 동일하게 설정(고급 설정)하는 것이 좋습니다.

**환경** - **프로덕션** 또는 **스테이징** 중 하나를 선택합니다. 테스트 환경에 애플리케이션을 배포하려면 스테이징 환경을 선택합니다.

**빌드 구성** - **디버그** 또는 **릴리스** 중 하나를 선택합니다.

**서비스 구성** - **클라우드** 또는 **로컬** 중 하나를 선택합니다.

**모든 역할에 대해 원격 데스크톱 사용** - 원격으로 서비스에 연결하려면 이 옵션을 선택합니다. 이 옵션은 주로 문제 해결을 위해 사용됩니다. 자세한 내용은 [Visual Studio를 사용하여 Azure Cloud Services에서 역할에 대한 원격 데스크톱 연결 사용](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)을 참조하세요.

**모든 웹 역할에 대해 웹 배포 사용** - 서비스에 웹 배포를 사용하도록 설정하려면 이 옵션을 선택합니다. 이 기능을 사용하려면 **모든 역할에 대해 원격 데스크톱 사용** 옵션도 선택해야 합니다. 자세한 내용은 [Visual Studio를 사용 하 여 클라우드 서비스 게시](vs-azure-tools-publishing-a-cloud-service.md)를 참조 하세요.

## <a name="settings-page---advanced-settings-tab"></a>설정 페이지 - 고급 설정 탭

![고급 설정](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**배포 레이블** - 기본 이름을 그대로 사용하거나 선택한 이름을 입력합니다. 배포 레이블에 날짜를 추가하려면 확인란을 선택한 상태로 둡니다.

**Storage 계정** - 이 배포에 사용할 Storage 계정을 선택하거나 ** &lt;새로 만들기>를 사용하여 Storage 계정을 만듭니다. 데이터 센터가 각 스토리지 계정에 대한 괄호 안에 표시됩니다. 스토리지 계정의 데이터 센터 위치는 클라우드 서비스의 데이터 센터 위치와 동일하게 설정(일반 설정)하는 것이 좋습니다.

Azure Storage 계정은 애플리케이션 배포용 패키지를 저장합니다. 애플리케이션이 배포된 후 패키지는 스토리지 계정에서 제거됩니다.

**실패 시 배포 삭제** - 게시 중에 오류가 발생한 배포를 삭제하려면 이 옵션을 선택합니다. 클라우드 서비스의 상수 가상 IP 주소를 유지하려면 이 옵션을 선택 취소해야 합니다.

**배포 업데이트** - 업데이트된 구성 요소만 배포하려면 이 옵션을 선택합니다. 이 유형의 배포는 전체 배포보다 빠를 수 있습니다. 클라우드 서비스의 상수 가상 IP 주소를 유지하려면 이 옵션을 선택해야 합니다.

**배포 업데이트 - 설정** - 이 대화 상자는 역할을 업데이트하는 방법을 자세히 지정하는 데 사용됩니다. **증분 업데이트**를 선택하면 애플리케이션의 각 인스턴스가 하나씩 차례로 업데이트되므로 해당 애플리케이션을 항상 사용할 수 있습니다. **동시 업데이트**를 선택하면 애플리케이션의 모든 인스턴스가 동시에 업데이트됩니다. 동시 업데이트는 신속하게 진행되지만 업데이트 과정 중에 서비스를 사용할 수 없습니다.

![배포 설정](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace 사용** - IntelliTrace를 사용하도록 설정할지 여부를 지정합니다. IntelliTrace를 사용하여 Azure에서 실행할 때 역할 인스턴스에 대한 광범위한 정보를 기록할 수 있습니다. 문제의 원인을 찾아야 하는 경우 Azure에서 실행 중인 것처럼 Visual Studio에서 코드를 단계별로 실행하는 데 IntelliTrace 로그를 사용할 수 있습니다. IntelliTrace 사용에 대한 자세한 내용은 [IntelliTrace 및 Visual Studio를 사용하여 게시된 Azure 클라우드 서비스 디버깅](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)을 참조하세요.

**프로파일링 사용** - 성능 프로파일링을 사용하도록 설정할지 여부를 지정합니다. Visual Studio 프로파일러를 사용하면 클라우드 서비스가 실행되는 방식의 계산 측면을 자세히 분석할 수 있습니다. Visual Studio 프로파일러 사용에 대한 자세한 내용은 [Azure 클라우드 서비스의 성능 테스트](./vs-azure-tools-performance-profiling-cloud-services.md)를 참조하세요.

**모든 역할에 대해 원격 디버거 사용** - 원격 디버깅을 사용하도록 설정할지 여부를 지정합니다. Visual Studio를 사용하여 클라우드 서비스를 디버그하는 방법에 대한 자세한 내용은 [Visual Studio에서 Azure 클라우드 서비스 또는 가상 머신 디버깅](./vs-azure-tools-debug-cloud-services-virtual-machines.md)을 참조하세요.

## <a name="diagnostics-settings-page"></a>진단 설정 페이지

![진단 설정](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

진단을 통해 Azure 클라우드 서비스(또는 Azure 가상 머신)의 문제를 해결할 수 있습니다. 진단에 대한 자세한 내용은 [Azure Cloud Services 및 Virtual Machines에서 진단 구성](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)을 참조하세요. Application Insights에 대한 자세한 내용은 [Application Insights란?](/azure/application-insights/app-insights-overview)을 참조하세요.

## <a name="summary-page"></a>요약 페이지

![요약](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**대상 프로필** - 선택한 설정에서 게시 프로필을 만들도록 선택할 수 있습니다. 예를 들어, 테스트 환경에 대한 하나의 프로필을 만들고 프로덕션용으로 다른 하나를 만들 수 있습니다. 이 프로파일을 저장하려면 **저장** 아이콘을 선택합니다. 마법사는 프로필을 만들고 Visual Studio 프로젝트에 저장합니다. 프로필 이름을 수정하려면 **대상 프로필** 목록을 연 다음 **&lt;관리...&gt;** 를 선택합니다.

   > [!Note]
   > 게시 프로필은 Visual Studio의 솔루션 탐색기에 나타나며 프로필 설정은 확장명이 .azurePubxml인 파일로 기록됩니다. 설정은 XML 태그의 특성으로 저장됩니다.

## <a name="publishing-your-application"></a>애플리케이션 게시

프로젝트 배포에 대한 설정을 모두 구성했으면 대화 상자의 아래쪽에서 **게시**를 선택합니다. Visual Studio의 **출력** 창에서 프로세스 상태를 모니터링할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [Visual Studio에서 Azure 클라우드 서비스로 웹 애플리케이션 마이그레이션 및 게시](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Visual Studio를 사용하여 Azure 클라우드 서비스 게시](./vs-azure-tools-publishing-a-cloud-service.md)

- [IntelliTrace 및 Visual Studio를 사용하여 게시된 Azure 클라우드 서비스 디버깅](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Azure 클라우드 서비스의 성능 테스트](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Azure Cloud Services 및 Virtual Machines에 대 한 진단 구성](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)

- [Application Insights란?](/azure/application-insights/app-insights-overview)