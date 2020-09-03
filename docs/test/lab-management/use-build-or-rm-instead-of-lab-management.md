---
title: 자동화된 테스트를 위해 Azure Pipelines 사용
ms.date: 10/19/2018
ms.topic: how-to
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 37455c05a010681eac343287abf25aad642328c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286845"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>자동화된 테스트를 위해 Lab Management 대신 Azure Test Plans 사용

자동화된 테스트 또는 빌드-배포-테스트 자동화에 Microsoft Test Manager 및 Lab Management를 사용할 경우, 이 항목에서는 Azure Pipelines 및 TFS(Team Foundation Server)의 [빌드 및 릴리스](/azure/devops/pipelines/index?view=vsts) 기능을 사용하여 동일한 목표를 달성하는 방법을 설명합니다.

> [!NOTE]
> Microsoft Test Manager는 Visual Studio 2017에서 사용이 중단되었으며, Visual Studio 2019에서 제거되었습니다.

## <a name="build-deploy-test-automation"></a>빌드-배포-테스트 자동화

Microsoft Test Manage 및 Lab Management는 XAML 빌드 정의를 사용하여 애플리케이션의 빌드, 배포 및 테스트를 자동화합니다. XAML 빌드는 랩 환경, 테스트 도구 모음 및 테스트 설정과 같은 Microsoft Test Manager에서 만들어진 다양한 생성자와 빌드 컨트롤러, 빌드 에이전트, 테스트 컨트롤 및 테스트 에이전트와 같은 다양한 인프라 구성 요소를 사용하여 이 목표를 달성합니다. Azure Pipelines 또는 TFS를 사용하여 더 적은 단계로 동일하게 수행할 수 있습니다.

| 단계 | XAML 빌드 사용 | 빌드 또는 릴리스에서 |
|-------|----------------------|-----------------|
| 빌드를 배포하고 테스트를 실행할 컴퓨터를 식별합니다. | 해당 머신을 사용하여 Microsoft Test Manager의 표준 랩 환경을 만듭니다. | N/A |
| 실행할 테스트를 식별합니다. | Microsoft Test Manager에서 테스트 도구 모음을 만들고, 테스트 사례를 만들고, 각 테스트 사례와 자동화를 연결합니다. 테스트를 실행할 랩 환경에서 머신의 역할을 식별하는 테스트 설정을 Microsoft Test Manager에서 만듭니다. | 테스트 계획을 통해 테스트를 관리하려면 같은 방식으로 Microsoft Test Manager에서 자동화된 테스트 도구 모음을 만듭니다. 또는 빌드에서 생성된 테스트 이진 파일에서 직접 테스트를 실행하려면 이 단계를 건너뛸 수 있습니다. 어느 경우에도 테스트 설정을 만들 필요가 없습니다. |
| 배포 및 테스트를 자동화합니다. | LabDefaultTemplate.*.xaml을 사용하여 XAML 빌드 정의를 만듭니다. 빌드 정의에서 빌드, 테스트 도구 모음 및 랩 환경을 지정합니다. | 단일 환경을 사용하여 [빌드 또는 릴리스 파이프라인](/azure/devops/pipelines/index?view=vsts)을 만듭니다. 명령줄 작업을 사용하여 XAML 빌드 정의에서 동일한 배포 스크립트를 실행하고 테스트 에이전트 배포 및 기능 테스트 실행 작업을 사용하여 자동화된 테스트를 실행합니다. 컴퓨터 및 해당 자격 증명 목록을 이러한 작업의 입력으로 지정합니다. |

이 시나리오에 대한 Azure Pipelines 또는 TFS를 사용하여 얻을 수 있는 이점 중 일부는 다음과 같습니다.

* 빌드 컨트롤러 또는 테스트 컨트롤러가 필요하지 않습니다.
* 테스트 에이전트는 빌드 또는 릴리스에 포함된 작업을 통해 설치됩니다.
* 배포 단계를 쉽게 사용자 지정할 수 있습니다. 더 이상 단일 스크립트를 사용하도록 제한되지 않습니다. Visual Studio Marketplace 및 제품에서 제공되는 많은 작업을 활용할 수도 있습니다.
* 테스트 도구 모음을 유지 관리할 필요가 없습니다. 이진 파일에서 직접 테스트를 실행할 수 있습니다.
* 각 빌드 또는 릴리스 내에서 실행된 테스트에 대한 더 풍부한 인라인 보고 환경을 얻을 수 있습니다.
* 각 환경에서 현재 배포 및 테스트되는 자산(릴리스, 빌드, 작업 항목, 커밋)을 추적할 수 있습니다.
* 자동화를 사용자 지정하고 확장하여 여러 테스트 환경뿐 아니라 프로덕션 환경에도 쉽게 배포할 수 있습니다.
* 체크 인 또는 커밋이 있을 때마다 또는 매일 특정 시간에 발생하도록 자동화를 예약할 수 있습니다.

## <a name="self-service-management-of-scvmm-environments"></a>SCVMM 환경의 셀프 서비스 관리

[Microsoft Test Manager의 Test Center](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts)는 [SCVMM 서버](/system-center/vmm/overview?view=sc-vmm-1801)를 사용하여 요청 시 환경을 프로비저닝하고 환경 템플릿의 라이브러리를 관리하는 기능을 지원합니다.

Lab Center의 셀프 서비스 프로비전 기능에는 두 가지 목표가 있습니다.

* 인프라를 관리하는 더 간단한 방법을 제공합니다. 예를 들어 인프라 관리를 위해 VM 및 환경 템플릿을 관리하고 서로 환경 복제본을 격리하는 개인 네트워크를 자동으로 만들었습니다.

* 팀이 테스트 및 배포 활동에서 가상 컴퓨터를 사용할 수 있는 더 간단한 방법을 제공합니다. 예를 들어 간편한 사용을 위해 동일한 프로젝트 보안 모델을 통해 랩 환경에 액세스할 수 있고 테스트 시나리오에서 해당 가상 머신을 통합 사용하도록 했습니다.

그러나 [Microsoft Azure](https://azure.microsoft.com/) 및 [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/)과 같은 더 다양한 퍼블릭 및 프라이빗 클라우드 관리 시스템의 발전을 고려한다면 TFS 2017 이상에는 인프라 관리 기능의 발전이 없습니다. 대신에 해당 클라우드 인프라를 통해 관리되는 리소스의 간편한 사용에 계속 초점을 맞춥니다.

다음 표에는 랩 센터에서 수행하는 일반적인 활동과 SCVMM 또는 Azure(인프라 관리 활동인 경우)를 통해서 또는 TFS 및 Azure DevOps Services(테스트 또는 배포 활동인 경우)를 통해 해당 활동을 수행하는 방법이 요약되어 있습니다.

| 단계 | Lab Center 사용 | 빌드 또는 릴리스에서 |
|-------|-----------------|-----------------------|
| 환경 템플릿 라이브러리를 관리합니다. | 랩 환경을 만듭니다. 가상 컴퓨터에 필요한 소프트웨어를 설치합니다. 환경을 Sysprep하고 라이브러리의 템플릿으로 저장합니다. | SCVMM 관리 콘솔을 사용하여 직접 가상 머신 템플릿 또는 서비스 템플릿을 만들고 관리합니다. Azure를 사용하는 경우 [Azure 빠른 시작 템플릿](https://azure.microsoft.com/resources/templates/)중 하나를 선택합니다. |
| 랩 환경을 만듭니다. | 라이브러리에서 환경 템플릿을 선택하고 배포합니다. 가상 머신 구성을 사용자 지정하는데 필요한 매개 변수를 제공합니다. | SCVMM 관리 콘솔을 사용하여 직접 템플릿을 기반으로 VM 또는 서비스 인스턴스를 만듭니다. Azure Portal을 사용하여 직접 리소스를 만듭니다. 또는 환경을 사용하여 릴리스 정의를 만듭니다. Azure 작업 또는 [SCVMM 통합 확장](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)의 작업을 사용하여 새 가상 컴퓨터를 만듭니다. 이 정의의 새 릴리스를 만드는 것은 Lab Center에서 새 환경을 만드는 것과 같습니다. |
| 컴퓨터에 연결합니다. | 환경 뷰어에서 랩 환경을 엽니다. | SCVMM 관리 콘솔을 사용하여 직접 가상 컴퓨터에 연결합니다. 또는 가상 컴퓨터의 IP 주소 또는 DNS 이름을 사용하여 원격 데스크톱 세션을 엽니다. |
| 환경 검사점을 만들거나 환경을 새로운 검사점으로 복원합니다. | 환경 뷰어에서 랩 환경을 엽니다. 검사점을 만들거나 이전 검사점으로 복원하는 옵션을 선택합니다. | SCVMM 관리 콘솔을 사용하여 컴퓨터에서 이러한 작업을 수행합니다. 또는 더 큰 자동화의 일부로 이러한 단계를 수행하려면 [SCVMM 통합 확장](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp)의 검사점 작업을 환경의 일부로 릴리스 정의에 포함합니다. |

## <a name="create-network-isolated-environments"></a>네트워크 격리 환경 만들기

네트워크 격리 랩 환경은 네트워크 충돌 없이 안전하게 복제할 수 있는 SCVMM 가상 컴퓨터 그룹입니다. 이 작업은 네트워크 인터페이스 집합을 사용하여 개인 네트워크에서 가상 컴퓨터를 구성하고 또 다른 네트워크 인터페이스 카드 집합을 사용하여 공용 네트워크에서 가상 컴퓨터를 구성한 일련의 명령을 사용하여 MTM에서 수행되었습니다.

그러나 Azure Pipelines 및 TFS를 SCVMM 빌드 및 배포 작업과 함께 사용하여 SCVMM 환경을 관리하고 격리된 가상 네트워크를 프로비전하고 빌드-배포-테스트 시나리오를 구현할 수 있습니다. 예를 들어 이 작업을 사용하여 다음을 수행할 수 있습니다.

* 검사점 만들기, 복원 및 삭제
* 템플릿을 사용하여 새 가상 머신 만들기
* 가상 머신 시작 및 중지
* SCVMM에 대한 사용자 지정 PowerShell 스크립트 실행

자세한 내용은 [빌드-배포-테스트 시나리오에 대한 가장 네트워크 격리 환경 만들기](/azure/devops/pipelines/targets/create-virtual-network?view=vsts)를 참조하세요.
