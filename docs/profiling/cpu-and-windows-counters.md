---
title: CPU 및 Windows 카운터 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9accd3d0ab5ff1f7a3084d5973cace08e66396b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779552"
---
# <a name="cpu-and-windows-counters"></a>CPU 및 Windows 카운터

Visual Studio 프로파일러를 사용하면 운영 체제(Windows 카운터)에 의해 생성된 성능 데이터 및 프로세서 단위(CPU 카운터)에 의해 생성된 성능 데이터를 수집할 수 있습니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="windows-counters"></a>Windows 카운터

Windows 카운터는 운영 체제, 애플리케이션, 서비스 또는 드라이버의 성능에 대한 정보를 제공하는 Windows 진단 인프라의 일부입니다. Windows 카운터는 현재 컴퓨터의 구성에 따라 다르며 다른 컴퓨터에서 사용하지 못할 수 있습니다. Windows 성능 카운터는 프로파일링 데이터 파일에 프로파일링 표시로 수집되므로 보기 및 보고서를 필터링하는 데 사용할 수 있습니다.

## <a name="cpu-counters"></a>CPU 카운터

CPU 카운터는 하드웨어 관련 이벤트의 수를 저장하는 컴퓨터의 CPU 기능입니다. 계측 프로파일링 방법을 사용하여 CPU 카운터 데이터를 수집하는 경우 데이터는 함수 및 모듈에 대한 데이터에 추가됩니다. 계측 방법을 사용하면 여러 CPU 카운터를 수집할 수 있습니다. 샘플링 방법을 사용하는 경우 하나의 카운터를 선택하여 샘플링할 이벤트로 사용합니다.

성능 카운터는 CPU마다 다릅니다. 다양한 CPU 모델 및 버전이 동일한 성능 카운터를 사용할 수 있도록 크게 다른 구성 설정을 가질 수 있습니다. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 프로파일러 Portable Events는 특정 프로세서에서 몇 가지 일반적인 성능 카운터를 분리하고 일반 성능 이벤트를 수집하거나 샘플링할 수 있도록 합니다.

프로파일러를 사용할 때 L2 캐시 누락과 같은 특정 이벤트의 수를 계산하려는 경우 해당 이벤트 전송자를 중심으로 성능 세션을 빌드할 수 있습니다. L2 캐시가 있는 모든 CPU에서 이를 수행할 수 있습니다. 성능 세션은 수정 없이 플랫폼 간에 이동할 수 있습니다.

Visual Studio 프로파일러는 특정 플랫폼에 대한 특정 이벤트를 계속 지원합니다. 예를 들어 Pentium 4 플랫폼의 개발자가 NetBurst 아키텍처와 관련된 이벤트 수를 계산하려고 할 수 있습니다. 이 이벤트를 이식할 수는 없지만, 특정 플랫폼의 특정 성능 세션에서는 개발자가 계속 사용할 수 있습니다.

## <a name="portable-and-platform-events"></a>Portable Events 및 Platform Events

Portable Events는 특정 프로세서에만 한정되지 않은 CPU 카운터 그룹입니다. 다른 모든 CPU 카운터는 Platform Events라고 하며, 다양한 플랫폼에서 지원되지 않을 수 있습니다.

 Portable Events와 Platform Events 둘 다에 대한 카운터는 카운터와 관련된 구체적인 값을 제공하는 .*xml* 파일에 정의되어 있습니다. 예를 들어 Intel 및 AMD CPU에 대한 데이터가 서로 다르므로 다양한 CPU에 대한 여러 파일이 있습니다. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 프로파일러는 이 정보를 사용하여 성능 측정에 대한 Portable Events와 Platform Events 둘 다의 적절한 카운터를 사용자에게 제공합니다.

### <a name="portable-events"></a>Portable Events

Portable Events에는 다음 이벤트가 포함됩니다.

**일반 이벤트**

|이벤트 이름|이벤트 설명|
|----------------|-----------------------|
|Instructions Retired|이벤트가 완료될 때까지 실행된 명령의 수를 나타냅니다.|
|Non Halted Cycles|프로세서가 중지되지 않은 해당 사이클만 나타냅니다(예: I/O 대기).|

**프런트 엔드 이벤트**

|이벤트 이름|이벤트 설명|
|----------------|-----------------------|
|ITLB Misses|누락을 발생시킨 ITLB(Instruction Translation Lookaside Buffer) 조회의 수를 나타냅니다.|

**분기 이벤트**

|이벤트 이름|이벤트 설명|
|----------------|-----------------------|
|Branches Retired|이벤트가 완료될 때까지 실행된 분기 명령의 수를 나타냅니다.|
|Mis-predicted Branches|프로세서가 잘못된 경로를 예측해서 발생하는 잘못 예측된 분기를 나타냅니다. 잘못 예측된 분기는 프로세서가 수행된 모든 작업을 취소하고 올바른 경로에서 다시 시작해야 하므로 성능에 영향을 줍니다.|

**메모리 이벤트:**

|이벤트 이름|이벤트 설명|
|----------------|-----------------------|
|L2 Cache Read Misses|두 번째 수준의 캐시 읽기 누락의 수를 나타냅니다.|
|L2 Cache Read References|두 번째 수준의 캐시 읽기 참조의 수를 나타냅니다. 소유권(RFO) 누락 및 적중에 대한 로드 누락과 읽기가 포함됩니다.|

## <a name="view-available-counters"></a>사용 가능한 카운터 보기

Visual Studio IDE의 명령 프롬프트 창에서 사용 가능한 CPU 카운터를 나열할 수 있습니다.

### <a name="visual-studio-ui"></a>Visual Studio UI

Visual Studio IDE에서 컴퓨터에 사용 가능한 카운터를 나열하려면 성능 탐색기에서 프로파일러 성능 세션이 열려 있어야 합니다.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>현재 플랫폼에서 지원되는 모든 CPU 카운터의 목록을 보려면

1. 성능 탐색기에서 성능 세션을 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.

2. 다음 작업 중 하나를 수행합니다.

   - **샘플링**을 클릭한 후 **샘플** 이벤트 목록에서 **성능 카운터**를 선택합니다. CPU 카운터가 **사용 가능한 성능 카운터**에 나열됩니다.

      **참고** 이전 샘플링 구성으로 돌아가려면 **취소**를 클릭합니다.

     또는

   - **CPU 카운터**를 선택한 후 **CPU 카운터 수집**을 선택합니다. CPU 카운터가 **사용 가능한 카운터**에 나열됩니다.

      **참고** 이전 카운터 수집 구성으로 돌아가려면 **취소**를 클릭합니다.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>현재 플랫폼에서 지원되는 Windows 카운터의 목록을 보려면

1. 성능 탐색기에서 성능 세션을 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.

2. **Windows 카운터**를 클릭합니다.

3. **Windows 카운터 수집**을 선택합니다.

4. **카운터 범주** 목록에서 카운터 그룹을 선택합니다. 그룹의 Windows 카운터가 목록 상자에 표시됩니다.

     **참고:** 이전 카운터 수집 구성으로 돌아가려면 **취소**를 클릭합니다.

### <a name="command-line"></a>명령줄

[VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구를 사용하면 명령줄에서 컴퓨터에 사용할 수 있는 CPU 카운터를 나열할 수 있습니다.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>현재 플랫폼에서 지원되는 CPU 카운터의 목록을 표시하려면

1. 명령 프롬프트 창을 엽니다.

2. 형식

     **\<Visual Studio 성능 도구 디렉터리>\VSPerfCmd /querycounters**

     여기서 *\<Visual Studio 성능 도구 디렉터리>* 는 Visual Studio 설치의 성능 도구 디렉터리 경로입니다. 성능 도구에 대한 경로를 가져오려면 [명령줄 도구 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요.

## <a name="see-also"></a>참조

[개요](../profiling/overviews-performance-tools.md)
[방법: 샘플링 이벤트 선택](../profiling/how-to-choose-sampling-events.md)
[방법: CPU 카운터 데이터 수집](../profiling/how-to-collect-cpu-counter-data.md)
[방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)
