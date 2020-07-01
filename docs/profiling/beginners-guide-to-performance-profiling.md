---
title: 앱에서 CPU 사용량 측정
description: 디버거 통합 진단 도구를 사용하여 애플리케이션에서 CPU 성능 문제를 분석합니다.
ms.custom: seodec18
ms.date: 04/03/2019
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3a7c5eb8aa489da9ced0803e0f83855734825ff
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537373"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>CPU 사용량을 분석하여 애플리케이션 성능 측정

Visual Studio 프로파일링 도구를 사용하여 애플리케이션의 성능 문제를 분석할 수 있습니다. 이 문서에서는 진단 도구의 **CPU 사용량** 탭을 사용하여 앱의 성능 데이터를 가져오는 방법을 보여 줍니다.

디버거가 일시 중지되면 **CPU 사용량** 도구는 애플리케이션에서 실행되는 함수에 대한 정보를 지정된 간격으로 수집합니다. 또한 이 도구에는 작업을 수행하는 함수가 표시되고 샘플링 세션의 특정 세그먼트를 집중적으로 확인할 수 있는 타임라인 그래프도 표시됩니다.

진단 허브에서는 진단 세션을 실행하고 관리할 수 있는 여러 가지 다른 옵션을 제공합니다. **CPU 사용량**으로 필요한 데이터를 얻지 못할 경우 [다른 프로파일링 도구](../profiling/profiling-feature-tour.md)로 유용한 다른 종류의 정보를 얻을 수 있습니다. 많은 경우 메모리, UI 렌더링 또는 네트워크 요청 시간 등 CPU가 아닌 곳에서 애플리케이션의 성능 병목 현상이 발생할 수 있습니다. 진단 허브는 이러한 종류의 데이터를 기록 및 분석하기 위한 다른 여러 옵션을 제공합니다.

> [!Important]
> 진단 도구는 ASP.NET을 포함한 Visual Studio의 .NET 개발 및 네이티브/C++ 개발에 사용할 수 있습니다.

이 문서에서는 일반적인 디버깅 워크플로에서의 CPU 사용량 분석에 대해 설명합니다. 디버거를 연결하지 않고, 또는 실행 중인 앱을 대상으로 하여 CPU 사용량을 분석할 수도 있습니다. 자세한 내용은 [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)을 참조하세요. 또 다른 프로파일링 도구인 [PerfTips](../profiling/perftips.md)를 사용하여 코드를 단계별로 실행하며 특정 함수나 코드 블록이 완료되는 데 소요되는 시간을 확인할 수 있습니다.

Windows 7 이상에서 디버거 없이 프로파일링 도구를 사용할 수 있습니다. Windows 8 이상에서는 디버거(**진단 도구** 창)를 포함한 프로파일링 도구를 실행해야 합니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * CPU 사용량 데이터 수집
> * CPU 사용량 데이터 분석

## <a name="step-1-collect-profiling-data"></a>1단계: 프로파일링 데이터 수집

1. Visual Studio에서 디버그할 프로젝트를 열고 CPU 사용량을 검사할 지점에서 앱에 중단점을 설정합니다.

2. 분석할 함수 또는 코드 영역 끝에 두 번째 중단점을 설정합니다.

    두 개의 중단점을 설정하여, 분석하려는 코드 부분으로 데이터 수집을 제한할 수 있습니다.

3. 끄지 않았다면 **진단 도구** 가 자동으로 나타납니다. 창을 다시 표시하려면 **디버그** > **Windows** > **진단 도구 표시**를 클릭합니다.

4. 도구 모음의 **도구 선택** 설정을 사용하여 **CPU 사용량**을 표시할지, [메모리 사용량](../profiling/Memory-Usage.md)을 표시할지, 아니면 둘 다 표시할지를 선택할 수 있습니다. 또한 Visual Studio Enterprise를 실행 중인 경우 **도구** > **옵션** > **IntelliTrace**에서 IntelliTrace를 사용하거나 사용하지 않도록 설정할 수 있습니다.

     ![진단 도구 표시](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     주로 CPU 사용률을 살펴볼 것이므로 **CPU 사용량**을 사용하도록 설정했는지(기본적으로 사용됨) 확인하세요.

5. **디버그** > **디버깅 시작**을 클릭합니다(또는 도구 모음의 **시작** 또는 **F5** 키 누름).

     앱 로드가 완료되면 진단 도구의 요약 보기가 나타납니다. 창을 열어야 하는 경우 **디버그** > **Windows** > **진단 도구 표시**를 클릭합니다.

     ![진단 도구 요약 탭](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     이벤트에 대한 자세한 내용은 [진단 도구 창의 이벤트 탭 검색 및 필터링](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)을 참조하세요.

6. 첫 번째 중단점이 발생할 시나리오를 실행합니다.

7. 디버거가 일시 중지된 동안 CPU 사용량 데이터 수집을 사용하도록 설정한 다음 **CPU 사용량** 탭을 엽니다.

     ![진단 도구에서 CPU 프로파일링을 사용하도록 설정](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     **CPU 프로파일 기록**을 선택하면 Visual Studio는 함수 및 함수 실행에 걸리는 시간의 기록을 시작합니다. 애플리케이션이 중단점에서 멈추면 이렇게 수집된 데이터만 볼 수 있습니다.

8. 두 번째 중단점까지 앱을 실행하려면 F5 키를 누릅니다.

     이제 구체적으로 두 개의 중단점 사이에서 실행되는 코드 영역에 대한 애플리케이션의 성능 데이터가 제공됩니다.

     프로파일러는 스레드 데이터 준비를 시작합니다. 끝날 때까지 기다립니다.

     ![스레드를 준비하는 진단 도구](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     CPU 사용량 도구는 **CPU 사용량** 탭에 보고서를 표시합니다.

     ![진단 도구 CPU 사용량 탭](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. 분석할 코드의 특정 영역을 더 많이 선택하려면 CPU 타임라인에서 영역을 선택합니다(프로파일링 데이터를 표시하는 영역이어야 함).

     ![시간 세그먼트를 선택하는 진단 도구](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     이 시점에서 데이터 분석을 시작할 수 있습니다.

     > [!TIP]
     >  성능 문제를 조사할 때는 측정을 여러 번 진행하세요. 성능은 본질적으로 각 실행마다 다르게 나타나며 코드 경로는 보통 DLL 로드, JIT 컴파일 메서드, 캐시 초기화와 같은 일회성 초기화 작업으로 인해 처음 실행될 때 가장 느리게 실행됩니다. 측정을 여러 번 진행하면 조사하려는 메트릭의 범위와 중앙값을 더 잘 파악하여 해당 코드 영역의 첫 번째 실행 성능과 정상 상태 성능을 비교할 수 있습니다.

## <a name="step-2-analyze-cpu-usage-data"></a>2단계: CPU 사용량 데이터 분석

CPU 사용량 아래의 함수 목록을 검사하고, 가장 많은 작업을 수행하는 함수를 확인한 다음, 각 함수를 자세히 살펴보는 방식으로 데이터 분석을 시작하는 것이 좋습니다.

1. 함수 목록에서 가장 많은 작업을 수행하는 함수를 검사합니다.

    ![진단 도구 CPU 사용량 함수 목록](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > 함수는 가장 많은 작업을 수행하는 것부터 나열됩니다(호출 순서가 아님). 따라서 가장 오래 실행된 함수를 빠르게 식별할 수 있습니다.

2. 함수 목록에서 많은 작업을 수행한 앱 함수 중 하나를 두 번 클릭합니다.

    함수를 두 번 클릭하면 **호출자/호출 수신자** 뷰가 왼쪽 창에 열립니다.

    ![진단 도구 호출자/호출 수신자 뷰](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    이 뷰에서는 선택한 함수가 제목 및 **현재 함수** 상자에 표시됩니다(이 예제의 경우 GetNumber). 현재 함수를 호출한 함수는 **호출 함수** 아래 왼쪽에 표시되고, 현재 함수에 의해 호출된 함수는 오른쪽의 **호출된 함수** 상자에 표시됩니다. 두 상자 중 하나를 선택하여 현재 함수를 변경할 수 있습니다.

    이 뷰는 함수를 완료하는 데 걸린 총 시간(ms) 및 전체 앱 실행 시간의 백분율을 표시합니다.
    **함수 본문**은 또한 호출 함수 및 호출된 함수에 사용된 시간을 제외하고 함수 본문에 사용된 총 시간(및 시간의 백분율)을 표시합니다. 이 예제에서는 2389ms 중 2367ms가 함수 본문에 사용되었고 나머지 22ms는 이 함수에 의해 호출된 외부 코드에 사용되었습니다.

    > [!TIP]
    > **함수 본문**의 값이 높으면 함수 자체 내에서 성능 병목 현상이 있는 것일 수 있습니다.

3. 함수 호출 순서를 표시하는 상위 수준 보기를 보려면 창 위쪽의 드롭다운 목록에서 **호출 트리**를 선택합니다.

    그림에서 번호가 매겨진 각 영역은 절차의 단계와 관련되어 있습니다.

    ::: moniker range=">=vs-2019"
    ![진단 도구 호출 트리](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![진단 도구 호출 트리](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |이미지|설명|
    |-|-|
    |![1단계](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU 사용량 호출 트리의 최상위 노드는 의사 노드입니다.|
    |![2단계](../profiling/media/ProcGuid_2.png "ProcGuid_2")|대다수 앱에서 [외부 코드 포시](#view-external-code) 옵션이 사용하지 않도록 설정되어 있는 경우 두 번째 수준 노드는 앱을 시작/중지하고, UI를 그리며, 스레드 일정을 제어하고, 앱에 다른 낮은 수준 서비스를 제공하는 시스템과 프레임워크 코드가 포함된 **[External Code]** 노드입니다.|
    |![3단계](../profiling/media/ProcGuid_3.png "ProcGuid_3")|두 번째 수준 노드의 자식은 두 번째 수준 시스템과 프레임워크 코드가 호출하거나 만드는 사용자 코드 메서드 및 비동기 루틴입니다.|
    |![4단계](../profiling/media/ProcGuid_4.png "ProcGuid_4")|메서드의 자식 노드에는 부모 메서드 호출에 대한 데이터만 포함되어 있습니다. **외부 코드 표시** 가 사용하지 않도록 설정되어 있으면 앱 메서드에 **[External Code]** 노드를 포함할 수 있습니다.|

    열 값에 대한 자세한 내용은 다음과 같습니다.

    - **총 CPU**는 해당 함수와 이 함수에 의해 호출된 함수가 수행한 작업의 양을 나타냅니다. 총 CPU 값이 높으면 전반적인 비용이 가장 많이 드는 함수인 것입니다.

    - **셀프 CPU**는 호출된 함수에 의해 수행된 작업은 제외하고 함수 본문의 코드에 의해 수행된 작업의 양을 나타냅니다. **셀프 CPU** 값이 높으면 함수 자체 내에서 성능 병목 현상이 있는 것일 수 있습니다.

    - **모듈** 함수가 포함된 모듈의 이름 또는 [External Code] 노드에 함수가 포함된 모듈의 수입니다.

    ::: moniker range=">=vs-2019"
    호출 트리 뷰에서 CPU 사용률이 가장 높은 함수 호출을 보려면 **실행 부하 과다 경로 확장**을 클릭합니다.

    ![진단 도구 실행 부하 과다 경로](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > 호출 트리에서 코드가 “손상됨” 또는 “탐색 불가능 스택”으로 표시되는 경우 ETW(Windows용 이벤트 추적) 이벤트가 삭제되었을 가능성이 높음을 나타냅니다. 문제를 해결하려면 동일한 추적을 다시 수집해 보세요.

## <a name="view-external-code"></a>외부 코드 보기

외부 코드는 사용자가 작성한 코드에서 실행되는 시스템 및 프레임워크 구성 요소의 함수입니다. 외부 코드에는 앱을 시작 및 중지하고, UI를 그리며, 스레딩을 제어하고, 앱에 다른 낮은 수준 서비스를 제공하는 함수가 포함되어 있습니다. 대부분의 경우 외부 코드에 관심이 없으므로 CPU 사용량 도구에서 사용자 메서드의 외부 함수를 하나의 **[External Code]** 노드로 수집합니다.

외부 코드의 호출 경로를 보려면 **필터 뷰** 목록에서 **외부 코드 표시**를 선택한 다음 **적용**을 선택합니다.

![필터 뷰 선택 후 외부 코드 표시](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

여러 외부 코드 호출 체인은 깊이 중첩되어 있으므로 함수 이름 열의 너비가 컴퓨터 모니터의 거의 최대 화면 너비를 초과할 수 있습니다. 이런 경우 함수 이름은 다음과 같이 **[…]** 로 표시됩니다.

검색 상자를 사용하여 검색 중인 노드를 찾은 다음, 가로 스크롤 막대를 사용하여 데이터를 뷰로 가져옵니다.

> [!TIP]
> Windows 함수를 호출하는 외부 코드를 프로파일링하는 경우 가장 최근의 .*pdb* 파일이 있는지 확인해야 합니다. 이 파일이 없으면 보고서 뷰에 암호화되어 이해하기 어려운 Windows 함수 이름이 표시됩니다. 필요한 파일이 있는지 확인하는 방법에 대한 자세한 내용은 [디버거에서 기호(.pdb) 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 CPU 사용량 데이터를 수집하고 분석하는 방법을 배웠습니다. 이미 [프로파일링 도구 개요](../profiling/profiling-feature-tour.md)를 완료한 경우 앱에서 메모리 사용량을 분석하는 방법을 빠르게 확인하는 것이 좋습니다.

> [!div class="nextstepaction"]
> [Visual Studio에서 프로필 메모리 사용량](../profiling/memory-usage.md)
