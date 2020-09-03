---
title: Azure Cloud Services 및 가상 머신에 대한 진단 설정 | Microsoft Docs
description: Visual Studio에서 Azure Cloud Services 및 VM(가상 머신) 디버깅을 위해 진단을 설정하는 방법을 설명합니다.
author: mikejo5000
manager: jillfra
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d7099eb47007b1fc657164d085e8a5bb6f09e1db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75915648"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Azure Cloud Services 및 Virtual Machines에 대한 진단 설정
Azure 클라우드 서비스 또는 가상 머신 문제를 해결해야 하는 경우 Visual Studio를 사용하여 Azure Diagnostics를 보다 쉽게 설정할 수 있습니다. 진단은 클라우드 서비스를 실행하는 가상 머신 및 가상 머신 인스턴스에서 시스템 데이터와 로깅 데이터를 캡처합니다. 진단 데이터는 사용자가 선택한 스토리지 계정으로 전송됩니다. Azure의 진단 로깅에 대한 자세한 내용은 [Azure App Service에서 웹앱에 대해 진단 로깅 사용](/azure/app-service/web-sites-enable-diagnostic-log)을 참조하세요.

이 문서에서는 Visual Studio를 사용하여 배포 전후에 Azure Diagnostics를 켜고 설정하는 방법을 보여줍니다. Azure Virtual Machines에서 진단을 설정하는 방법, 수집할 진단 정보 유형을 선택하는 방법 및 수집한 후에 정보를 확인하는 방법을 알아봅니다.

Azure Diagnostics를 설정하려면 다음 옵션 중 하나를 사용할 수 있습니다.

* Visual Studio의 **진단 구성** 대화 상자에서 진단 설정을 변경합니다. 설정은 diagnostics.wadcfgx(Azure SDK 2.4 이하에서는 diagnostics.wadcfg)라는 파일에 저장됩니다. 구성 파일을 직접 수정할 수도 있습니다. 파일을 수동으로 업데이트하는 경우 다음에 클라우드 서비스를 Azure에 배포하거나 에뮬레이터에서 서비스를 실행할 때 변경 사항이 적용됩니다.
* Visual Studio에서 클라우드 탐색기 또는 서버 탐색기를 사용하여 실행 중인 클라우드 서비스 또는 가상 머신에 대한 진단 설정을 변경합니다.

## <a name="azure-sdk-26-diagnostics-changes"></a>Azure SDK 2.6 진단 변경
다음 변경 내용은 Visual Studio의 Azure SDK 2.6 이상 프로젝트에 적용됩니다.

* 이제 로컬 에뮬레이터에서 진단을 지원합니다. 따라서 Visual Studio에서 개발 및 테스트하는 동안 진단 데이터를 수집하고 애플리케이션에서 올바른 추적을 생성하고 있는지 확인할 수 있습니다. 연결 문자열 `UseDevelopmentStorage=true`는 Azure Storage 에뮬레이터를 사용하여 Visual Studio에서 클라우드 서비스 프로젝트를 실행하는 동안 진단 데이터 수집을 켭니다. 모든 진단 데이터는 개발 스토리지의 스토리지 계정에 수집됩니다.
* 진단 스토리지 계정 연결 문자열 `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString`은 서비스 구성(.cscfg) 파일에 저장됩니다. Azure SDK 2.5에서는 진단 스토리지 계정이 diagnostics.wadcfgx 파일에 지정됩니다.

이 연결 문자열은 Azure SDK 2.6 이상과 Azure SDK 2.4 이하 버전에서 주요 작동 방식이 약간 다릅니다.

* Azure SDK 2.4 이하 버전에서는 진단 로그를 전송하기 위한 스토리지 계정 정보를 가져오기 위해 진단 플러그인에 의해 런타임으로 연결 문자열이 사용되었습니다.
* Azure SDK 2.6 이상 버전에서 Visual Studio는 게시하는 동안 진단 연결 문자열을 사용하여 적절한 스토리지 계정 정보로 Azure Diagnostics 확장을 설정합니다. 연결 문자열을 사용하여 Visual Studio에서 게시하는 동안 사용하는 다양한 서비스 구성에 대해 서로 다른 스토리지 계정을 정의할 수 있습니다. 그러나 Azure SDK 2.5 이후에는 진단 플러그 인을 사용할 수 없으므로 .cscfg 파일 자체만으로 진단 확장을 설정할 수 없습니다. Visual Studio 또는 PowerShell과 같은 도구를 사용하여 확장을 별도로 설정해야 합니다.
* PowerShell을 사용한 진단 확장 설정 프로세스를 단순화하기 위해 Visual Studio의 패키지 출력에 각 역할에 대한 진단 확장의 공용 구성 XML이 포함됩니다. Visual Studio에서는 진단 연결 문자열을 사용하여 공용 구성의 스토리지 계정 정보를 채웁니다. 공용 구성 파일은 Extensions 폴더에 만들어집니다. 공용 구성 파일은 명명 패턴 PaaSDiagnostics.&lt;\>.PubConfig.xml을 사용합니다. 모든 PowerShell 기반 배포에서 이 패턴을 사용하여 각 구성을 역할에 매핑합니다.
* [Azure Portal](https://portal.azure.com/)은 .cscfg 파일의 연결 문자열을 사용하여 진단 데이터에 액세스합니다. 데이터는 **모니터링** 탭에 나타납니다. 연결 문자열은 포털에서 자세한 모니터링 데이터를 표시 하도록 서비스를 설정 하는 데 필요 합니다.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Azure SDK 2.6 이상으로 프로젝트 마이그레이션
Azure SDK 2.5에서 Azure SDK 2.6 이상으로 마이그레이션하는 경우 .wadcfgx 파일에 진단 스토리지 계정이 지정된 경우 스토리지 계정은 해당 파일에 계속 유지됩니다. 서로 다른 스토리지 구성에 대해 서로 다른 스토리지 계정을 유연성 있게 사용하려면 프로젝트에 연결 문자열을 수동으로 추가합니다. Azure SDK 2.4 또는 이전 버전에서 Azure SDK 2.6으로 프로젝트를 마이그레이션하는 경우 진단 연결 문자열이 유지됩니다. 그러나 이전 섹션에서 설명된 Azure SDK 2.6에서 연결 문자열을 처리하는 방식이 변경되었음을 유의하세요.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Visual Studio에서 진단 스토리지 계정을 결정하는 방법
* 진단 연결 문자열이 .cscfg 파일에 지정된 경우 Visual Studio에서는 게시할 때와 패키징 동안 공용 구성 xml 파일을 생성할 때 이 연결 문자열을 사용하여 진단 확장을 설정합니다.
* 진단 연결 문자열이 .cscfg 파일에 지정되지 않은 경우 Visual Studio에서는 게시할 때와 패키징 동안 공용 구성 XML 파일을 생성할 때 .wadcfgx 파일에 지정된 스토리지 계정을 대신 사용하여 진단 확장을 설정합니다.
* .cscfg 파일의 진단 연결 문자열은 .wadcfgx 파일의 스토리지 계정보다 우선합니다. 진단 연결 문자열이.cscfg 파일에 지정된 경우, Visual Studio에서는 이 연결 문자열을 사용하고 .wadcfgx의 스토리지 계정은 무시합니다.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>&quot;개발 스토리지 연결 문자열 업데이트...&quot; 확인란의 기능은 무엇인가요?
**Microsoft Azure에 게시할 때 Microsoft Azure Storage 계정 자격 증명을 사용하여 진단 및 캐싱을 위한 개발 스토리지 연결 문자열 업데이트** 확인란은 게시하는 동안 지정된 Azure Storage 계정으로 개발 스토리지 계정 연결 문자열을 업데이트하는 편리한 방법입니다.

예를 들어 이 확인란을 선택하며 진단 연결 문자열이 `UseDevelopmentStorage=true`를 지정하면 Azure에 프로젝트를 게시할 때 Visual Studio는 게시 마법사에 지정한 스토리지 계정으로 진단 연결 문자열을 자동으로 업데이트합니다. 그러나 실제 스토리지 계정을 진단 연결 문자열로 지정한 경우 해당 계정이 대신 사용됩니다.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Azure SDK 2.4 및 이전 버전과 Azure SDK 2.5 이상에서 진단 기능 차이점
Azure SDK 2.4 및 이전 버전에서 Azure SDK 2.5 이상으로 프로젝트를 업그레이드하는 경우 다음 진단 기능 차이점을 명심해야 합니다.

* **구성 API가 더 이상 사용되지 않음**. 진단의 프로그래밍 방식 구성은 Azure SDK 2.4 이하 버전에서는 사용할 수 있지만 Azure SDK 2.5 이상 버전에서는 더 이상 사용되지 않습니다. 코드에 진단 구성이 현재 정의된 경우 계속해서 진단하려면 마이그레이션된 프로젝트에서 해당 설정을 처음부터 다시 구성해야 합니다. Azure SDK 2.4용 진단 구성 파일은 diagnostics.wadcfg입니다. Azure SDK 2.5 이상용 진단 구성 파일은 diagnostics.wadcfg입니다.
* **클라우드 서비스 애플리케이션에 대한 진단은 역할 수준에서만 구성할 수 있음**. Azure SDK 2.5 이상 버전에서는 인스턴스 수준에서 클라우드 서비스 애플리케이션에 대한 진단을 설정할 수 없습니다.
* **앱을 배포할 때마다 진단 구성이 업데이트됨**. 이로 인해 Visual Studio 서버 탐색기에서 진단 구성을 변경한 후 앱을 다시 배포하는 경우 패리티 문제가 발생할 수 있습니다.
* **Azure SDK 2.5 이상에서는 크래시 덤프가 코드가 아닌 진단 구성 파일에 구성됨**. 크래시 덤프가 코드에 구성된 경우 수동으로 코드의 구성을 구성 파일로 전송해야 합니다. Azure SDK 2.6으로 마이그레이션하는 동안에는 크래시 덤프가 전송되지 않습니다.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>배포 전에 클라우드 서비스 프로젝트에서 진단 켜기
Visual Studio에서는 배포하기 전에 에뮬레이터에서 서비스를 실행할 때 Azure에서 실행되는 역할에 대한 진단 데이터를 수집할 수 있습니다. Visual Studio에서 진단 설정의 모든 변경 내용은 diagnostics.wadcfgx 구성 파일에 저장됩니다. 이러한 설정은 클라우드 서비스를 배포할 때 진단 데이터가 저장되는 스토리지 계정을 지정합니다.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>배포하기 전에 Visual Studio에서 진단을 켜려면

1. 역할에 대한 바로 가기 메뉴에서 **속성**을 선택합니다. 역할의 **속성** 대화 상자에서 **구성** 탭을 선택합니다.
2. **진단** 섹션에서 **진단 사용** 확인란이 선택되어 있는지 확인합니다.

    ![진단 사용 옵션에 액세스](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. 진단 데이터에 대한 스토리지 계정을 지정하려면 줄임표(...) 단추를 선택합니다.

    ![사용할 스토리지 계정 지정](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. **스토리지 연결 문자열 만들기** 대화 상자에서 Azure Storage 에뮬레이터, Azure 구독을 사용하여 연결할지, 아니면 직접 자격 증명을 입력할지 여부를 지정합니다.

    ![Storage 계정 대화 상자](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * **Microsoft Azure Storage 에뮬레이터**를 선택하면 연결 문자열은 `UseDevelopmentStorage=true`로 설정됩니다.
   * **구독**을 선택하는 경우 사용할 Azure 구독을 선택하고 계정 이름을 입력할 수 있습니다. Azure 구독을 관리하려면 **계정 관리**를 선택합니다.
   * **수동으로 입력한 자격 증명**을 선택하는 경우 사용할 Azure 계정의 이름 및 키를 입력합니다.
5. **진단 구성** 대화 상자를 표시하려면 **구성**을 선택합니다. **일반** 및 **로그 디렉터리**를 제외한 각 탭은 수집할 수 있는 진단 데이터 원본을 나타냅니다. 기본 **일반** 탭은 **오류만**, **모든 정보** 및 **사용자 지정 계획**의 진단 데이터 컬렉션 옵션을 제공합니다. 기본 **오류만** 옵션은 경고 또는 추적 메시지를 전송하지 않으므로 최소한의 스토리지를 사용합니다. **모든 정보** 옵션은 대부분의 정보를 전송하고, 대부분의 스토리지를 사용하므로 비용이 가장 많이 드는 옵션입니다.

   > [!NOTE]
   > "디스크 할당량(MB)"에 지원되는 최소 크기는 4GB입니다. 그러나 메모리 덤프를 수집하는 경우 이 값을 10GB까지 늘릴 수 있습니다.
   >

    ![Azure 진단 및 구성 사용](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. 이 예제에서는 **사용자 지정 계획** 옵션을 선택하여 수집된 데이터를 사용자 지정할 수 있습니다.
7. **디스크 할당량(MB)** 상자에서는 진단 데이터를 위한 스토리지 계정에 할당할 공간을 설정할 수 있습니다. 기본값을 변경하거나 그대로 사용할 수 있습니다.
8. 수집 하려는 진단 데이터의 각 탭에서 **전송 \<log type\> 사용** 확인란을 선택 합니다. 예를 들어 애플리케이션 로그를 수집하려는 경우 **애플리케이션 로그** 탭에서 **애플리케이션 로그 전송 사용** 확인란을 선택합니다. 또한 각 진단 데이터 형식에 필요한 기타 정보를 지정합니다. 각 탭에 대한 구성 정보는 이 문서 뒷부분에 있는 **진단 데이터 원본 설정** 섹션을 참조하세요.
9. 원하는 모든 진단 데이터의 컬렉션을 사용하도록 설정한 후에는 **확인**을 선택합니다.
10. 평상시처럼 Visual Studio에서 Azure 클라우드 서비스 프로젝트를 실행합니다. 애플리케이션을 사용함에 따라 Azure Storage 계정으로 사용하도록 설정한 로그 정보가 지정한 Azure Storage 계정에 저장됩니다.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Azure Virtual Machines에서 진단 켜기
Visual Studio에서 Azure Virtual Machines에 대한 진단 데이터를 수집할 수 있습니다.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Azure Virtual Machines에서 진단을 켜려면

1. 서버 탐색기에서 Azure 노드를 선택하고 아직 연결되어 있지 않은 경우 Azure 구독에 연결합니다.
2. **가상 컴퓨터** 노드를 확장합니다. 새 가상 머신을 만들거나 기존 노드를 선택할 수 있습니다.
3. 원하는 가상 컴퓨터에 대한 바로 가기 메뉴에서 **구성**을 선택합니다. 가상 머신 구성 대화 상자가 나타납니다.

    ![Azure Virtual Machine 구성](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. 아직 설치되어 있지 않은 경우 Microsoft Monitoring Agent 진단 확장을 추가 합니다. 이 확장을 통해 Azure Virtual Machine에 대한 진단 데이터를 수집할 수 있습니다. **설치된 확장**의 **사용 가능한 확장 선택** 드롭다운 목록 상자에서 **Microsoft Monitoring Agent 진단**을 선택합니다.

    ![Azure 가상 머신 확장 설치](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > 다른 진단 확장은 가상 머신에 대해 사용할 수 있습니다. 자세한 내용은 [Windows용 가상 머신 확장 및 기능](/azure/virtual-machines/windows/extensions-features)을 참조하세요.
   >
   >
5. 확장을 추가하고 해당 **진단 구성** 대화 상자를 표시하려면 **추가**를 선택합니다.
6. 스토리지 계정을 지정하려면 **구성**을 선택한 후 **확인**을 선택합니다.

    **일반** 및 **로그 디렉터리**를 제외한 각 탭은 수집할 수 있는 진단 데이터 원본을 나타냅니다.

    ![Azure 진단 및 구성 사용](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    기본 탭인 **일반**은 **오류만**, **모든 정보** 및 **사용자 지정 계획**의 진단 데이터 컬렉션 옵션을 제공합니다. 기본 옵션인 **오류만**은 경고 또는 추적 메시지를 전송하지 않기 때문에 가장 적은 저장소 공간을 사용합니다. **모든 정보** 옵션은 대부분의 정보를 전달하므로 저장소 측면에서 볼 때 비용이 가장 많이 드는 옵션입니다.
7. 이 예에서는 수집한 데이터를 사용자 지정할 수 있도록 **사용자 지정 계획** 옵션을 선택합니다.
8. **디스크 할당량(MB)** 상자는 진단 데이터에 대해 저장소 계정에 할당할 공간 크기를 지정합니다. 원하는 경우 기본값을 변경할 수 있습니다.
9. 수집할 진단 데이터의 각 탭에서 **\<log type\> 전송 사용** 확인란을 선택합니다.

    예를 들어 응용 프로그램 로그를 수집 하려는 **경우 응용 프로그램 로그 탭에서** **응용 프로그램 로그 전송 사용** 확인란을 선택 합니다. 또한 각 진단 데이터 형식에 필요한 기타 정보를 지정 합니다. 각 탭에 대한 구성 정보는 이 문서 뒷부분에 있는 **진단 데이터 원본 설정** 섹션을 참조하세요.
10. 원하는 모든 진단 데이터의 컬렉션을 사용하도록 설정한 후에는 **확인**을 선택합니다.
11. 업데이트된 프로젝트를 저장합니다.

    **Microsoft Azure 활동 로그** 창에 가상 머신이 업데이트되었다는 메시지가 표시됩니다.

## <a name="set-up-diagnostics-data-sources"></a>진단 데이터 원본 설정
진단 데이터 컬렉션을 사용하도록 설정했으면 수집할 데이터 원본과 수집되는 정보를 정확하게 선택할 수 있습니다. 다음 섹션에서는 **진단 구성** 대화 상자에 있는 탭 목록과 각 구성 옵션의 의미를 설명합니다.

### <a name="application-logs"></a>애플리케이션 로그 전송 사용
애플리케이션 로그는 웹 애플리케이션에서 생성된 진단 정보를 포함합니다. 응용 프로그램 로그를 캡처하려면 **응용 프로그램 로그 전송 사용** 확인란을 선택합니다. 스토리지 계정으로의 애플리케이션 로그 전송 간격을 늘리거나 줄이려면 변경 된 **전송 기간(분)** 값을 변경합니다. 또한 **로그 수준** 값을 설정하여 로그에 캡처되는 정보의 양을 변경할 수도 있습니다. 예를 들어 **자세히**를 선택하여 자세한 정보를 얻거나 **중요**를 선택하여 중요한 오류만 캡처하도록 선택합니다. 애플리케이션 로그를 생성하는 특정 진단 공급자가 있는 경우 공급자의 GUID를 **공급자 GUID** 상자에 추가하여 캡처할 수 있습니다.

  ![애플리케이션 로그 전송 사용](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

애플리케이션 로그에 대한 자세한 내용은 [Azure App Service에서 웹앱에 대한 진단 로깅 설정](/azure/app-service/web-sites-enable-diagnostic-log)을 참조하세요.

### <a name="windows-event-logs"></a>Windows 이벤트 로그
Windows 이벤트 로그를 캡처하려면 **Windows 이벤트 로그 전송 사용** 확인란을 선택합니다. 스토리지 계정으로의 이벤트 로그 전송 간격을 늘리거나 줄이려면 변경 된 **전송 기간(분)** 값을 변경합니다. 추적하려는 이벤트 유형에 대한 확인란을 선택 합니다.

![이벤트 로그](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Azure SDK 2.6 이상을 사용 중인 경우 사용자 지정 데이터 원본을 지정 하려면 텍스트 상자에 입력 한 **\<Data source name\>** 다음 **추가**를 선택 합니다. 데이터 원본이 diagnostics.cfcfg 파일에 추가됩니다.

Azure SDK 2.5를 사용 중이고 사용자 지정 데이터 원본을 지정하려면 다음 예와 같이 diagnostics.wadcfgx 파일의 `WindowsEventLog` 섹션에 추가하면 됩니다.

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>성능 카운터
성능 카운터 정보는 시스템 병목 지점을 찾고 시스템 및 애플리케이션 성능을 미세하게 조정하는 데 도움이 될 수 있습니다. 자세한 내용은 [Azure 애플리케이션에서 성능 카운터 만들기 및 사용](https://msdn.microsoft.com/library/azure/hh411542.aspx)을 참조하세요. 성능 카운터를 캡처하려면 **성능 카운터 전송 사용** 확인란을 선택합니다. 스토리지 계정으로의 이벤트 로그 전송 간격을 늘리거나 줄이려면 변경 된 **전송 기간(분)** 값을 변경합니다. 추적하려는 성능 카운터에 대한 확인란을 선택 합니다.

![성능 카운터](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

나열되지 않은 성능 카운터를 추적하려면 제안된 구문을 사용하여 성능 카운터를 입력합니다. 그런 후 **추가**를 선택합니다. 가상 컴퓨터의 운영 체제에서 추적할 수 있는 성능 카운터를 결정 합니다. 구문에 대 한 자세한 내용은 [카운터 경로 지정](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx)을 참조 하세요.

### <a name="infrastructure-logs"></a>인프라 로그
인프라 로그는 Azure 진단 인프라, RemoteAccess 모듈 및 RemoteForwarder 모듈에 대한 정보를 포함합니다. 인프라 로그에 대한 정보를 수집하려면 **인프라 로그 전송 사용** 확인란을 선택합니다. 스토리지 계정으로의 인프라 로그 전송 간격을 늘리거나 줄이려면 변경 된 **전송 기간(분)** 값을 변경합니다.

![진단 인프라 로그](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

자세한 내용은 [Azure 진단를 사용 하 여 로깅 데이터 수집](https://msdn.microsoft.com/library/azure/gg433048.aspx)을 참조 하세요.

### <a name="log-directories"></a>로그 디렉터리
로그 디렉터리는 IIS(인터넷 정보 서비스) 요청, 실패한 요청 또는 사용자가 선택한 폴더에 대한 로그 디렉터리에서 수집한 데이터를 포함합니다. 로그 디렉터리를 캡처하려면 **로그 디렉터리 전송 사용** 확인란을 선택합니다. 스토리지 계정으로의 로그 전송 간격을 늘리거나 줄이려면 변경 된 **전송 기간(분)** 값을 변경합니다.

**IIS 로그** 및 **실패한 요청** 로그처럼 수집할 로그의 확인란을 선택합니다. 기본 스토리지 컨테이너 이름이 제공되지만 이 이름은 변경할 수 있습니다.

모든 폴더에서 로그를 캡처할 수 있습니다. **절대 디렉터리에서 로그** 섹션에 경로를 지정한 후 **디렉터리 추가**를 선택합니다. 로그는 지정된 컨테이너에 캡처됩니다.

![로그 디렉터리](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW 로그
[Windows용 이벤트 추적](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx)(ETW)을 사용하고 ETW 로그를 캡처하려는 경우 **ETW 로그 전송 사용** 확인란을 선택합니다. 스토리지 계정으로의 로그 전송 간격을 늘리거나 줄이려면 변경 된 **전송 기간(분)** 값을 변경합니다.

사용자가 지정한 이벤트 원본과 이벤트 매니페스트에서 이벤트가 캡처됩니다. 이벤트 원본을 지정하려면 **이벤트 원본** 섹션에 이름을 입력한 후 **이벤트 원본 추가**를 선택합니다. 마찬가지로, **이벤트 매니페스트** 섹션에 이벤트 매니페스트를 지정한 후 **이벤트 매니페스트 추가**를 선택할 수 있습니다.

![ETW 로그](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ETW 프레임워크는 [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) 네임스페이스의 클래스를 통해 ASP.NET에서 지원됩니다. Microsoft.WindowsAzure.Diagnostics 네임스페이스는 표준 [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) 클래스에서 상속 및 확장하며 Azure 환경에서 로깅 프레임워크로 [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110))를 사용하도록 설정합니다. 자세한 내용은 [Microsoft Azure에서 로깅 및 추적 관리](https://msdn.microsoft.com/magazine/ff714589.aspx) 및 [Azure Cloud Services 및 Virtual Machines에서 진단 사용](/azure/cloud-services/cloud-services-dotnet-diagnostics)을 참조하세요.

### <a name="crash-dumps"></a>크래시 덤프
역할 인스턴스가 충돌하는 경우에 대한 정보를 캡처하려면 **크래시 덤프 전송 사용** 확인란을 선택합니다. ASP.NET는 대부분의 예외를 처리 하기 때문에이는 일반적으로 작업자 역할에만 유용 합니다. 크래시 덤프에 할당 된 저장소 공간의 비율을 늘리거나 줄이려면 **디렉터리 할당량 (%)** 값을 변경 합니다. 크래시 덤프가 저장되는 스토리지 컨테이너를 변경하고 **전체** 또는 **미니** 덤프를 캡처할지 여부를 선택할 수 있습니다.

현재 추적 중인 프로세스가 다음 스크린샷에 나열됩니다. 캡처하려는 프로세스에 대한 확인란을 선택합니다. 다른 프로세스를 목록에 추가하려면 프로세스 이름을 입력하고 **프로세스 추가**를 선택합니다.

![크래시 덤프](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

자세한 내용은 [Microsoft Azure에서 로깅 및 추적 관리](https://msdn.microsoft.com/magazine/ff714589.aspx) 및 [Microsoft Azure Diagnostics 4부: 사용자 지정 로깅 구성 요소 및 Azure Diagnostics 1.3 변경 내용](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/)을 참조하세요.

## <a name="view-the-diagnostics-data"></a>진단 데이터 보기
클라우드 서비스 또는 가상 머신에 대한 진단 데이터를 수집한 후에 이를 볼 수 있습니다.

### <a name="to-view-cloud-service-diagnostics-data"></a>클라우드 서비스 진단 데이터를 보려면
1. 일반적인 방법으로 클라우드 서비스를 배포하고 실행합니다.
2. Visual Studio에서 생성하는 보고서 또는 스토리지 계정의 테이블 형태로 진단 데이터를 볼 수 있습니다. 보고서로 데이터를 보려면 클라우드 탐색기 또는 서버 탐색기를 열고 원하는 역할에 대한 노드의 바로 가기 메뉴를 열고 **진단 데이터 보기**를 선택합니다.

    ![진단 데이터 보기](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    사용 가능한 데이터를 표시하는 보고서가 나타납니다.

    ![Visual Studio의 Microsoft Azure Diagnostics 보고서](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    가장 최근 데이터가 나타나지 않는 경우 전송 기간이 경과할 때까지 기다려야 할 수 있습니다.

    데이터를 즉시 업데이트하려면 **새로 고침** 링크를 선택합니다. 데이터를 자동으로 업데이트하려면 **자동 새로 고침** 드롭다운 목록 상자에서 간격을 선택합니다. 오류 데이터를 내보내려면 **CSV로 내보내기** 단추를 선택하여 Excel 워크시트에서 열 수 있는 쉼표로 구분된 값 파일을 만듭니다.

    클라우드 탐색기 또는 서버 탐색기에서 배포와 관련된 스토리지 계정을 엽니다.
3. 테이블 뷰어에서 진단 테이블을 열고 수집한 데이터 검토 합니다. IIS 로그 및 사용자 지정 로그인 경우 BLOB 컨테이너를 열 수 있습니다. 다음 표에는 다른 로그 파일에 대한 데이터를 포함하는 테이블 또는 Blob 컨테이너가 나와 있습니다. 해당 로그 파일에 대한 데이터 외에도 테이블 항목에는 **EventTickCount**, **DeploymentId**, **Role** 및 **RoleInstance**가 포함되어 데이터가 생성된 가상 머신 및 역할과 데이터가 생성된 시기를 파악할 수 있습니다.

   | 진단 데이터 | 설명 | 위치 |
   | --- | --- | --- |
   | 애플리케이션 로그 전송 사용 |코드에서 **Diagnostics. Trace** 클래스의 메서드를 호출 하 여 생성 하는 로그입니다. |WADLogsTable |
   | 이벤트 로그 |가상 머신에서 Windows 이벤트 로그에서 가져온 데이터입니다. Windows에서는 이러한 로그에 정보를 저장하지만 애플리케이션 및 서비스에서는 로그를 사용하여 오류 또는 로그 정보를 보고합니다. |WADWindowsEventLogsTable |
   | 성능 카운터 |가상 머신에서 사용할 수 있는 성능 카운터에서 데이터를 수집할 수 있습니다. 운영 체제에서 메모리 사용량 및 프로세서 시간 등의 다양한 통계를 포함하는 성능 카운터를 제공합니다. |WADPerformanceCountersTable |
   | 인프라 로그 |진단 인프라 자체에서 생성되는 로그입니다. |WADDiagnosticInfrastructureLogsTable |
   | IIS 로그 |웹 요청을 기록하는 로그입니다. 클라우드 서비스에 상당한 양의 트래픽이 들어오는 경우 이러한 로그 시간이 오래 걸릴 수 있습니다. 데이터를 필요할 때만 수집하고 저장하는 것이 좋습니다. |배포, 역할 및 인스턴스에 대한 경로의 wad-iis-failedreqlogs 아래에 있는 Blob 컨테이너에서 실패한 요청 로그를 찾을 수 있습니다. 전체 로그는 wad-iis-logfiles 아래에서 찾을 수 있습니다. 각 파일에 대한 항목은 WADDirectories 테이블에서 생성됩니다. |
   | 크래시 덤프 |클라우드 서비스 프로세스의 이진 이미지를 제공합니다(일반적으로 작업자 역할). |wad-crush-dumps BLOB 컨테이너 |
   | 사용자 지정 로그 파일 |미리 정의된 데이터의 로그입니다. |스토리지 계정의 사용자 지정 로그 파일의 위치를 코드에 지정할 수 있습니다. 예를 들어, 사용자 지정 BLOB 컨테이너를 지정할 수 있습니다. |
4. 임의 형식의 데이터가 잘린 경우 해당 데이터 형식에 대한 버퍼를 늘리거나 가상 컴퓨터에서 스토리지 계정 간에 데이터 전송 간격을 단축하려고 시도할 수 있습니다.
5. (선택 사항) 스토리지 계정에서 데이터를 삭제하여 전체 스토리지 비용을 절감하는 경우도 있습니다.
6. 전체 배포를 수행하면 Azure에서 diagnostics.cscfg 파일(Azure SDK 2.5의 경우 wadcfgx)이 업데이트되고 클라우드 서비스가 진단 구성에 대한 변경 내용을 선택합니다. 대신, 기존 배포를 업데이트하는 경우 Azure에서 .cscfg 파일은 업데이트되지 않습니다. 다음 섹션의 단계에 따라 계속해서 진단 설정을 변경할 수 있습니다. 전체 배포 및 기존 배포 업데이트에 대한 자세한 내용은 [Azure 애플리케이션 게시 마법사](vs-azure-tools-publish-azure-application-wizard.md)를 참조하세요.

### <a name="to-view-virtual-machine-diagnostics-data"></a>가상 머신 진단 데이터를 보려면
1. 가상 머신에 대한 바로 가기 메뉴에서 **진단 데이터 보기**를 선택합니다.

    ![Azure Virtual Machine에서 진단 데이터 보기](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    **진단 요약** 대화 상자가 나타납니다.

    ![Azure 가상 머신 진단 요약](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    가장 최근 데이터가 나타나지 않는 경우 전송 기간이 경과할 때까지 기다려야 할 수 있습니다.

    데이터를 즉시 업데이트하려면 **새로 고침** 링크를 선택합니다. 데이터를 자동으로 업데이트하려면 **자동 새로 고침** 드롭다운 목록 상자에서 간격을 선택합니다. 오류 데이터를 내보내려면 **CSV로 내보내기** 단추를 선택하여 Excel 워크시트에서 열 수 있는 쉼표로 구분된 값 파일을 만듭니다.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>배포 후 클라우드 서비스 진단 설정
이미 실행 중인 클라우드 서비스로 문제를 조사하는 경우 처음에 역할을 배포한 후에 지정한 데이터를 수집하려 할 수 있습니다. 이 경우 서버 탐색기에서 설정을 변경하여 해당 데이터의 수집을 시작할 수 있습니다. 인스턴스 또는 역할에 대한 바로 가기 메뉴에서 **진단 구성** 대화 상자를 여는지 여부에 따라 역할에서는 단일 인스턴스 또는 모든 인스턴스에 대한 진단을 설정할 수 있습니다. 역할 노드를 구성하는 경우 수행하는 모든 변경 내용이 모든 인스턴스에 적용됩니다. 인스턴스 노드를 구성하는 경우 모든 변경 내용이 해당 인스턴스에만 적용됩니다.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>실행 중인 클라우드 서비스에 대한 진단을 설정하려면
1. 서버 탐색기에서 **Cloud Services** 노드를 확장한 후 노드 목록을 확장하여 조사할 역할이나 인스턴스 또는 둘 다를 찾습니다.

    ![진단 구성](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. 인스턴스 노드나 역할 노드에 대한 바로 가기 메뉴에서 선택 **진단 설정 업데이트**를 선택한 후 수집할 진단 설정을 선택합니다.

    구성 설정에 대한 자세한 내용은 이 문서의 **진단 데이터 원본 설정** 섹션을 참조하세요. 진단 데이터를 보는 방법에 대한 자세한 내용은 이 문서의 **진단 데이터 보기** 섹션을 참조하세요.

    서버 탐색기에서 데이터 컬렉션을 변경하는 경우 클라우드 서비스를 완전히 다시 배포할 때까지 이 변경 내용이 계속 적용됩니다. 기본 게시 설정을 사용하는 경우 변경 내용을 덮어쓰지 않습니다. 기본 게시 설정은 전체 다시 배포를 수행하는 것이 아니라 기존 배포를 업데이트하는 것입니다. 배포 시 설정을 지우려면 게시 마법사의 **고급 설정** 탭으로 이동하고 **배포 업데이트** 확인란을 선택 취소합니다. 해당 확인란이 선택 취소된 상태에서 재배포하는 경우 역할에 대한 **속성** 편집기를 통해 설정된 대로 .wadcfgx(또는 .wadcfg) 파일의 내용으로 설정을 되돌립니다. 배포를 업데이트하는 경우 Azure는 이전 설정을 유지합니다.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Azure 클라우드 서비스 문제 해결
"사용 중" 상태에 고착된 역할, 반복적인 재활용 또는 내부 서버 오류 throw와 같은 클라우드 서비스 프로젝트에서 문제가 발생하는 경우 이러한 문제를 진단하고 해결하는 데 사용할 수 있는 도구와 기술이 있습니다. 일반적인 문제 및 해결 방법에 대한 구체적인 예제와 이러한 오류를 진단 및 해결하는 데 사용되는 개념 및 도구에 대한 개요는 [Azure PaaS Compute 진단 데이터](https://blogs.msdn.microsoft.com/kwill/2013/08/09/windows-azure-paas-compute-diagnostics-data/)를 참조하세요.

## <a name="q--a"></a>Q & A
**버퍼 크기란 무엇이고 얼마나 클 수 있습니까?**

각 가상 머신 인스턴스에서 로컬 파일 시스템에 저장할 수 있는 진단 데이터의 양에 대한 할당량 제한입니다. 또한 사용할 수 있는 진단 데이터의 각 형식에 대해 버퍼 크기를 지정합니다. 이 버퍼 크기는 해당 형식의 데이터에 대해 개별 할당량과 같은 역할을 합니다. 전체 할당량과 남은 메모리의 양을 확인하려면 진단 데이터 형식에 대한 대화 상자의 아래쪽을 확인하세요. 버퍼 크기를 크게 지정하거나 더 많은 데이터 형식을 지정할 경우 전체 할당량에 근접하게 됩니다. diagnostics.wadcfg 또는 .wadcfgx 구성 파일을 수정하여 전체 할당량을 변경할 수 있습니다. 진단 데이터는 애플리케이션 데이터와 같은 파일 시스템에 저장됩니다. 애플리케이션이 많은 양의 디스크 공간을 사용하는 경우 전체 진단 할당량을 늘리지 말아야 합니다.

**전송 기간이란 무엇이고 얼마나 기간이 깁니까?**

전송 기간은 데이터 캡처 간에 경과되는 시간의 양입니다. 각 전송 기간 후 데이터는 가상 머신의 로컬 파일 시스템에서 스토리지 계정의 테이블로 이동합니다. 전송 기간이 끝나기 전에 수집되는 데이터 양이 할당량을 초과하는 경우 오래된 데이터가 삭제됩니다. 데이터가 버퍼 크기 또는 전체 할당량을 초과하기 때문에 데이터가 손실되는 경우 전송 기간을 줄일 수 있습니다.

**타임 스탬프는 어떤 표준 시간대를 기준으로 합니까?**

타임스탬프는 클라우드 서비스를 호스팅하는 데이터 센터의 현지 표준 시간대를 기준으로 합니다. 로그 테이블에는 다음 세 타임 스탬프 열이 사용됩니다.

* **PreciseTimeStamp**: 이벤트의 ETW 타임스탬프입니다. 즉, 클라이언트에서 이벤트가 로깅된 시간입니다.
* **TIMESTAMP**: 업로드 빈도 경계로 내림되는 **PreciseTimeStamp** 값입니다. 예를 들어 업로드 빈도가 5분이고 이벤트 시간이 00:17:12이면 TIMESTAMP는 00:15:00가 됩니다.
* **Timestamp**: Azure 테이블에서 엔터티가 생성된 타임스탬프입니다.

**진단 정보를 수집할 때 비용은 어떻게 관리합니까?**

비용을 최소화하도록 기본 설정(**로그 수준**은 **오류**로, **전송 기간**은 **1분**으로 설정)이 지정됩니다. 더 많은 진단 데이터를 수집하거나 전송 기간을 줄이는 경우 컴퓨팅 비용이 늘어납니다. 불필요한 데이터를 수집하지 마세요. 더 이상 필요하지 않을 때는 데이터 컬렉션을 해제하는 것을 잊지 마세요. 이 문서 앞부분에 설명된 대로 런타임 중에도 항상 다시 사용하도록 설정할 수 있습니다.

**IIS에서 실패한 요청 로그를 수집하려면 어떻게 합니까?**

기본적으로 IIS는 실패한 요청 로그를 수집하지 않습니다. 웹 역할에 대한 web.config 파일을 편집하여 실패한 요청 로그를 수집하도록 IIS를 설정할 수 있습니다.

**OnStart 같은 RoleEntryPoint 메서드에서 추적 정보를 얻을 수 없습니다. 무엇이 문제입니까?**

**RoleEntryPoint** 메서드는 IIS가 아닌, WAIISHost.exe 컨텍스트에서 호출됩니다. 일반적으로 추적을 사용하는 web.config의 구성 정보는 적용되지 않습니다. 이 문제를 해결 하려면 웹 역할 프로젝트에 .config 파일을 추가 하 고 **Roleentrypoint** 코드가 포함 된 출력 어셈블리와 일치 하도록 파일의 이름을로 합니다. 기본 웹 역할 프로젝트에서 .config 파일의 이름을 WAIISHost.exe.config 해야 합니다. 이 파일에 다음 줄을 추가 합니다.

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

**속성** 창에서 **출력 디렉터리로 복사** 속성을 **항상 복사**로 설정합니다.

## <a name="next-steps"></a>다음 단계
Azure에서 로깅 진단에 대한 자세한 내용은 [Azure Cloud Services 및 Virtual Machines에서 진단 사용](/azure/cloud-services/cloud-services-dotnet-diagnostics) 및 [Azure App Service에서 웹앱에 대한 진단 로깅 설정](/azure/app-service/web-sites-enable-diagnostic-log)을 참조하세요.
