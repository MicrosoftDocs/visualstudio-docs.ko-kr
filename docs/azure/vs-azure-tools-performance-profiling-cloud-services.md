---
title: 클라우드 서비스의 성능 테스트 | Microsoft Docs
description: Visual Studio 프로파일러를 사용하여 클라우드 서비스의 성능을 테스트합니다.
author: mikejo5000
manager: jillfra
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.openlocfilehash: 04e3ee89498447f7743fc1b5119e129f046b4fcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911773"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>클라우드 서비스의 성능 테스트
## <a name="overview"></a>개요
다음과 같은 방법으로 클라우드 서비스의 성능을 테스트할 수 있습니다.

* 요청과 연결에 대한 정보를 수집하고 서비스를 고객 관점에서 수행하는 방법을 보여주는 사이트 통계를 검토하려면 Azure Diagnostics를 사용합니다. 시작하려면 [Azure Cloud Services 및 Virtual Machines에서 진단 구성](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)을 참조하십시오.
* Visual Studio 프로파일러를 사용하여 서비스 실행 방식의 계산 측면에 대한 심층 분석을 가져옵니다. 이 항목에서 알 수 있듯이 Azure에서 서비스가 실행될 때 성능을 측정하기 위해 프로파일러를 사용할 수 있습니다. 컴퓨팅 에뮬레이터에서 서비스가 로컬로 실행될 때 성능을 측정하는 프로파일러를 사용하는 방법에 대한 정보는 [Visual Studio 프로파일러를 사용하여 컴퓨팅 에뮬레이터에서 로컬로 Azure Cloud Services의 성능 테스트](/azure/cloud-services/cloud-services-performance-testing-visual-studio-profiler)를 참조하세요.

## <a name="choosing-a-performance-testing-method"></a>성능 테스트 방법 선택
### <a name="use-azure-diagnostics-to-collect"></a>수집할 Azure Diagnostics 사용:
* 웹 페이지 또는 요청 및 연결 등의 서비스에 대한 통계.
* 역할이 재시작되는 빈도 등의 역할에 대한 통계.
* 가비지 수집기에 걸리는 시간 백분율 또는 실행 중인 역할의 메모리 집합 등 메모리 사용량에 관한 전체 정보.

### <a name="use-the-visual-studio-profiler-to"></a>Visual Studio 프로파일러를 사용하여 다음을 수행하십시오.
* 어떤 함수가 가장 많은 시간이 걸리는지 결정합니다.
* 계산이 많은 프로그램의 각 부분에는 얼마나 많은 시간이 걸리는지 측정합니다.
* 서비스의 두 버전에 대한 자세한 성능 보고서를 비교합니다.
* 개별 메모리 할당 수준보다 메모리 할당을 더 자세히 분석합니다.
* 다중스레드 코드에서 동시성 문제를 분석합니다.

프로파일러를 사용하는 경우에 로컬로 또는 Azure에서 클라우드 서비스를 실행하는 경우 데이터를 수집할 수 있습니다.

### <a name="collect-profiling-data-locally-to"></a>로컬로 프로파일링 데이터를 수집합니다.
* 현실적인 시뮬레이션된 부하가 필요하지 않은 특정 작업자 역할의 실행 같은 클라우드 서비스의 일부 성능을 테스트합니다.
* 제어된 조건의 격리 상태에서 클라우드 서비스의 성능을 테스트합니다.
* Azure에 배포하기 전에 클라우드 서비스의 성능을 테스트합니다.
* 기존 배포를 방해하지 않고 클라우드 서비스의 성능을 개인적으로 테스트합니다.
* Azure에서 실행하는데 드는 비용 없이 서비스의 성능을 테스트합니다.

### <a name="collect-profiling-data-in-azure-to"></a>Azure에서 프로파일링 데이터를 수집하여 다음을 수행합니다.
* 시뮬레이션된 부하나 실제 부하에서 클라우드 서비스의 성능을 테스트합니다.
* 이 항목 뒷부분 설명에 따라 프로파일링 데이터 수집의 계측 방법을 사용합니다.
* 서비스가 프로덕션 환경에서 실행되는 때와 동일한 환경에서 서비스의 성능을 테스트합니다.

일반적인 조건 또는 스트레스 조건에서 클라우드 서비스를 테스트하는 부하를 일반적으로 시뮬레이트합니다.

## <a name="profiling-a-cloud-service-in-azure"></a>Azure에서 클라우드 서비스 프로파일링
Visual Studio에서 클라우드 서비스를 게시할 때에 서비스를 프로파일링하고 원하는 정보를 제공하는 프로파일링 설정을 지정할 수 있습니다. 역할의 각 인스턴스에 대한 프로파일링 세션이 시작됩니다. Visual Studio에서 서비스를 게시하는 방법에 대한 자세한 내용은 [Visual Studio에서 Azure 클라우드 서비스에 게시](vs-azure-tools-publishing-a-cloud-service.md)를 참조하십시오.

Visual Studio에서 성능을 프로파일링하는 방법을 알아보려면 [성능 프로파일링 초보자 가이드](https://msdn.microsoft.com/library/azure/ms182372.aspx) 및 [프로파일링 도구를 사용하여 애플리케이션 성능 분석](https://msdn.microsoft.com/library/azure/z9z62c29.aspx)을 참조하세요.

> [!NOTE]
> 응용 프로그램을 게시할 때 IntelliTrace 또는 프로파일링을 사용할 수 있습니다. 둘 다 사용할 수는 없습니다.
>
>

### <a name="profiler-collection-methods"></a>프로파일러 컬렉션 방법
프로파일링을 위해 성능 문제에 따라 여러 수집 방법을 사용할 수 있습니다.

* **CPU 샘플링** - 이 방법은 CPU 이용률 문제의 초기 분석에 유용한 애플리케이션 통계를 수집합니다. CPU 샘플링은 대부분의 성능 조사를 시작하기 위한 권장 방법입니다. CPU 샘플링 데이터를 수집할 때 프로파일링하는 애플리케이션에 많은 영향을 미치지 않습니다.
* **계측** - 이 방법은 집중된 분석 및 입/출력 성능 문제 분석에 유용한 자세한 타이밍 데이터를 수집합니다. 계측 방법은 프로파일링 실행 중 모듈의 각 항목, 종료 및 함수 호출 함수를 기록합니다. 이 방법은 코드의 한 섹션에 대한 자세한 타이밍 정보를 수집하고 입력 및 출력 작업이 애플리케이션 성능에 미치는 영향을 이해하는 데 유용합니다. 이 방법은 32비트 운영 체제를 실행하는 컴퓨터에 사용되지 않습니다. 이 옵션은 컴퓨팅 에뮬레이터에서 로컬이 아닌 Azure에서 클라우드 서비스를 실행하는 경우에만 사용할 수 있습니다.
* **.NET 메모리 할당** - 이 방법은 샘플링 프로파일링 방법을 사용하여 .NET Framework 메모리 할당 데이터를 수집합니다. 수집된 데이터에 할당된 개체의 수와 크기가 포함됩니다.
* **동시성** - 이 방법은 리소스 경합 데이터와 프로세스 및 멀티스레드와 멀티 프로세스 애플리케이션 분석에 유용한 스레드 실행 데이터를 수집합니다. 동시성 방법은 스레드가 해제될 애플리케이션 리소스에 대한 잠긴 액세스에 대해 대기하는 경우와 같은 코드의 실행을 차단하는 각 이벤트에 대한 데이터를 수집합니다. 이 메서드는 다중 스레드 애플리케이션을 분석하는 데 유용합니다.
* 하나 이상의 데이터베이스와 통신하는 다중 계층 애플리케이션의 함수에서 동기 ADO.NET 호출의 실행 시간에 관한 추가 정보를 제공하는 **계층 상호작용 프로파일링**을 사용할 수도 있습니다. 프로파일링 방법을 사용하여 계층 상호작용 데이터를 수집할 수 있습니다. 계층 상호작용 프로파일링에 대한 자세한 내용은 [계층 상호작용 보기](https://msdn.microsoft.com/library/azure/dd557764.aspx)를 참조하십시오.

## <a name="configuring-profiling-settings"></a>프로파일링 설정 구성
다음 그림은 Azure 애플리케이션 게시 대화 상자에서 프로파일링 설정을 구성하는 방법을 나타냅니다.

![프로파일링 설정 구성](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> **프로파일링 사용** 확인란을 활성화하려면 클라우드 서비스를 게시하는 데 사용하는 로컬 컴퓨터에 프로파일러가 설치되어 있어야 합니다. 기본적으로 프로파일러는 Visual Studio를 설치할 때 설치됩니다.
>
>

### <a name="to-configure-profiling-settings"></a>프로파일링 설정 구성
1. 솔루션 탐색기에서 Azure 프로젝트에 대한 바로 가기 메뉴를 열고 **게시**를 선택합니다. 클라우드 서비스를 게시하는 방법에 대한 자세한 단계는 [Azure 도구를 사용하여 클라우드 서비스 게시](vs-azure-tools-publishing-a-cloud-service.md)를 참조하세요.
2. **Azure 응용 프로그램 게시** 대화 상자에서 **고급 설정** 탭을 선택합니다.
3. 프로파일링을 사용하려면 **프로파일링 사용** 확인란을 선택합니다.
4. 프로파일링 설정을 구성하려면 **설정** 하이퍼링크를 선택합니다. 프로파일링 설정 대화 상자가 나타납니다.
5. **사용할 프로파일링 방법** 옵션 단추에서 필요한 프로파일링 유형을 선택합니다.
6. 계층 상호 작용 프로파일링 데이터를 수집하려면 **계층 상호 작용 프로파일링 사용** 확인란을 선택합니다.
7. 설정을 저장하려면 **확인** 단추를 선택합니다.

    이 애플리케이션을 게시할 때 각 역할에 대한 프로파일링 세션을 만들기 위해 이러한 설정이 사용됩니다.

## <a name="viewing-profiling-reports"></a>프로파일링 보고서 보기
프로파일링 세션은 클라우드 서비스에서 역할의 각 인스턴스에 대해 생성됩니다. Visual Studio에서 각 세션의 프로파일링 보고서를 보려면 서버 탐색기 창에서 볼 수 있으며 Azure Compute 노드를 선택하여 역할 인스턴스를 선택할 수 있습니다. 그런 다음 그림에서와 같이 프로파일링 보고서를 볼 수 있습니다.

![Azure에서 프로파일링 보고서 보기](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>프로파일링 보고서 보기
1. Visual Studio에서 서버 탐색기 창을 보려면 메뉴 모음에서 보기, 서버 탐색기를 선택합니다.
2. Azure Compute 노드를 선택한 다음, Visual Studio에서 게시할 때 프로파일링하도록 선택한 클라우드 서비스에 대한 Azure 배포 노드를 선택합니다.
3. 인스턴스에 대한 프로파일링 보고서를 보려면 서비스에서 역할을 선택하고 특정 인스턴스에 대한 바로 가기 메뉴를 연 다음 **프로파일링 보고서 보기**를 선택합니다.

    .vsp 파일인 보고서가 이제 Azure에서 다운로드되며 Azure 활동 로그에 다운로드 상태가 표시됩니다. 다운로드가 완료되면 프로파일링 보고서가 <Role name\>*<Instance Number\>*<identifier\>.vsp라는 Visual Studio에 대한 편집기의 탭에 나타납니다. 보고서에 대한 요약 데이터가 표시됩니다.
4. 현재 보기 목록에서 보고서의 다른 보기를 표시하려면 원하는 보기의 유형을 선택합니다. 자세한 내용은 [프로파일링 도구 보고서 보기](https://msdn.microsoft.com/library/azure/bb385755.aspx)를 참조하세요.

## <a name="next-steps"></a>다음 단계
[Cloud Services 디버깅](vs-azure-tools-debug-cloud-services-virtual-machines.md)

[Visual Studio에서 Azure 클라우드 서비스에 게시](vs-azure-tools-publishing-a-cloud-service.md)
