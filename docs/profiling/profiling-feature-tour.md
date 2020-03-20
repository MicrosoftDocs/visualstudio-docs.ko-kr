---
title: 프로파일링 도구를 사용하여 성능 측정
description: Visual Studio에서 사용할 수 있는 다른 진단 도구에 대해 간략히 살펴봅니다.
ms.custom: mvc
ms.date: 05/18/2018
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e4868899af67ebeb25ae508cbe7e5b0c83137bf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77578087"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>빠른 시작: 프로파일링 도구 살펴보기

Visual Studio에서는 앱의 유형에 따라 다른 성능 문제를 진단할 수 있는 다양한 프로파일링 도구를 제공합니다.

디버깅 세션 중에 액세스할 수 있는 프로파일링 도구는 [진단 도구] 창에 제공됩니다. 끄지 않았다면 [진단 도구] 창이 자동으로 나타납니다. 창을 표시하려면 **디버그/Windows/진단 도구 표시**를 클릭합니다. 창이 열리면 데이터를 수집할 도구를 선택할 수 있습니다.

![진단 도구 창](../profiling/media/prof-tour-diagnostic-tools.png "진단 도구")

디버그하는 동안 **진단 도구** 창을 사용하여 CPU 및 메모리 사용을 분석하고 성능 관련 정보를 보여주는 이벤트를 확인할 수 있습니다.

![진단 도구 요약 보기](../profiling/media/prof-tour-cpu-and-memory-graph.gif "진단 도구 요약")

기본적으로 **진단 도구** 창을 사용하여 앱을 프로파일링하지만 릴리스 빌드의 경우 앱에 대한 post-mortem 분석을 대신 수행할 수도 있습니다. 다른 방법에 대한 자세한 내용은 [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)을 참조하세요. 다양한 앱 유형에 대한 프로파일링 도구를 보려면 [사용해야 하는 도구](#which-tool-should-i-use)를 참조하세요.

> [!NOTE]
> Windows 7 이상에서 사후 분석 도구를 사용할 수 있습니다. Windows 8 이상에서는 디버거(**진단 도구** 창)를 포함한 프로파일링 도구를 실행해야 합니다.

## <a name="analyze-cpu-usage"></a>CPU 사용 분석

CPU 사용 도구를 사용하여 앱의 성능을 분석하는 것이 좋습니다. 이 도구는 앱에서 사용 중인 CPU 리소스에 대해 자세히 알려줍니다. CPU 사용량 도구에 대한 자세한 연습은 [CPU 사용량을 분석하여 애플리케이션 성능 측정](../profiling/beginners-guide-to-performance-profiling.md)을 참조하세요.

진단 도구의 **요약** 보기에서 **CPU 프로파일링 사용**을 선택합니다(디버깅 세션에 있어야 함).

![진단 도구에서 CPU 사용량 사용](../profiling/media/prof-tour-enable-cpu-profiling.png "진단 도구 CPU 사용량 사용")

도구를 가장 효율적으로 사용하려면 코드에 두 개의 중단점을 설정합니다(함수 또는 분석할 코드 영역의 시작 부분과 끝에 각각 하나씩). 두 번째 중단점에서 일시 중지된 경우에 프로파일링 데이터를 검토하세요.

**CPU 사용량** 보기에는 함수 목록이 오래 실행된 순으로 표시됩니다. 즉, 가장 오래 실행 중인 함수가 맨 위에 표시됩니다. 이 목록에서 성능 병목 현상이 발생 중인 함수를 알 수 있습니다.

![진단 도구 CPU 사용량 보기](../profiling/media/prof-tour-cpu-usage.png "진단 도구 CPU 사용량")

원하는 함수를 두 번 클릭하면 세 개의 창으로 구분된 세부 “나비” 뷰가 표시되고, 창의 가운데에는 선택된 함수, 왼쪽에는 호출 중인 함수, 오른쪽에는 호출된 함수가 표시됩니다. **함수 본문** 섹션에는 또한 호출 함수 및 호출된 함수에 사용된 시간을 제외하고 함수 본문에 사용된 총 시간(및 시간의 백분율)이 표시됩니다. 이 데이터를 사용하여 함수 자체에 성능 병목 현상이 있는지 여부를 평가할 수 있습니다.

![진단 도구 호출자 수신자 "나비" 뷰](../profiling/media/prof-tour-cpu-usage-caller-callee.png "진단 도구 호출자 수신자 뷰")

## <a name="analyze-memory-usage"></a>메모리 사용량 분석

또한 **진단 도구** 창을 사용하여 앱의 메모리 사용량을 평가할 수 있습니다. 예를 들어 힙에 있는 개체의 수와 크기를 확인할 수 있습니다. 메모리 분석에 대한 자세한 지침은 [메모리 사용량 분석](../profiling/memory-usage.md)을 참조하세요.

디버그하는 동안 메모리 사용량을 분석하려면 메모리 스냅샷을 하나 이상 만들어야 합니다. 메모리를 분석하는 가장 좋은 방법은 스냅샷을 두 개(의심되는 메모리 문제가 발생하기 직전과 직후) 만드는 것입니다. 그런 다음 두 스냅샷의 차이점을 보고 변경 내용을 정확히 확인할 수 있습니다.

![진단 도구에서 스냅샷 만들기](../profiling/media/prof-tour-take-snapshots.gif "스냅샷 수행 진단 도구")

화살표 링크 중 하나를 선택하면 힙의 차이 뷰(빨간색 위쪽 화살표 ![메모리 사용량 증가](../profiling/media/prof-tour-mem-usage-up-arrow.png "메모리 사용량 증가")는 증가하는 개체 수(왼쪽)와 증가하는 힙 크기(오른쪽) 표시)가 제공됩니다. 오른쪽 링크를 클릭하면 힙 크기가 가장 많이 증가한 개체순으로 차이 힙 뷰가 표시됩니다. 여기서 메모리 문제를 파악할 수 있습니다. 예를 들어 아래 그림에서 `ClassHandlersStore` 개체에 사용된 바이트 수가 두 번째 스냅샷에서 3,492바이트 증가했습니다.

![진단 도구 힙 차이 뷰](../profiling/media/prof-tour-mem-usage-diff-heap.png "진단 도구 힙 차이 뷰")

대신에 **메모리 사용량** 뷰의 왼쪽 링크를 클릭하면 힙 뷰가 개체 수를 기준으로 구성됩니다. 즉, 숫자가 가장 많이 증가한 특정 유형의 개체가 맨 위에 표시됩니다(**개수 차이** 열을 기준으로 정렬됨).

## <a name="examine-performance-events"></a>성능 이벤트 검사

진단 도구의 **이벤트** 뷰에는 디버그 중에 발생하는 다른 이벤트(예: 중단점 설정, 코드 단계별 실행 작업)가 표시됩니다. 이벤트 기간(디버거가 마지막으로 일시 중지되거나 앱이 시작된 시점부터 측정)과 같은 정보를 확인할 수 있습니다. 예를 들어 (F10, F11) 코드를 단계별로 실행할 경우 **이벤트** 뷰에 앱 런타임 기간(이전 단계 작업부터 현재 단계까지)이 표시됩니다.

![진단 도구 이벤트 뷰](../profiling/media/prof-tour-events.png "진단 도구 보기 이벤트")

 > [!NOTE]
 > Visual Studio Enterprise를 사용하는 경우 이 탭에 [IntelliTrace 이벤트](../debugger/intellitrace.md)가 표시될 수도 있습니다.

동일한 이벤트가 코드 편집기에도 PerfTips로 표시됩니다.

![프로파일링 둘러보기 PerfTips](../profiling/media/prof-tour-perf-tips.png "프로파일링 둘러보기 PerfTips")

## <a name="profile-release-builds-without-the-debugger"></a><a name="post_mortem"></a> 디버거 없이 릴리스 빌드 프로파일링

CPU 사용량 및 메모리 사용량과 같은 프로파일링 도구를 디버거와 함께 사용하거나(이전 섹션 참조) 성능 프로파일러를 통해 프로파일링 도구 사후 분석을 실행하여 **릴리스** 빌드에 대한 분석을 제공할 수 있습니다. 성능 프로파일러에서 앱이 실행 중인 동안 진단 정보를 수집한 다음 앱이 중지된 이후에 수집된 정보를 검사할 수 있습니다. 다른 방법에 대한 자세한 내용을 보려면 [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)을 참조하세요. [.NET 개체 할당 도구](../profiling/dotnet-alloc-tool.md)와 같은 추가 도구는 성능 프로파일러에서도 사용할 수 있습니다.

![성능 프로파일러](../profiling/media/prof-tour-performance-profiler.png "성능 프로파일러")

**디버그** > **성능 프로파일러**를 선택하여 성능 프로파일러를 엽니다.

창에서 여러 프로파일링 도구를 선택할 수 있는 경우도 있습니다. CPU 사용량과 같은 도구는 분석에 유용한 보조 데이터를 제공할 수 있습니다. [명령줄 프로파일러](../profiling/profile-apps-from-command-line.md)를 사용하여 여러 프로파일링 도구를 포함하는 시나리오를 사용하도록 설정할 수도 있습니다.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI 성능 및 접근성 이벤트 검사(UWP)

UWP 앱의 **진단 도구** 창에서 **UI 분석**을 사용하도록 설정할 수 있습니다. 이 도구는 디버그하는 동안 일반 성능 또는 접근성 문제를 검색하여 **이벤트** 뷰에 표시합니다. 이벤트 설명에는 문제를 해결하는 데 유용한 정보가 제공됩니다.

![진단 도구의 UI 분석 이벤트 뷰](../profiling/media/prof-tour-ui-analysis.png "진단 도구 보기 UI 분석 이벤트")

## <a name="analyze-resource-consumption-xaml"></a>리소스 사용 분석(XAML)

XAML 앱(예: Windows 데스크톱 WPF 앱 및 UWP 앱)에서 애플리케이션 타임라인 도구를 사용하여 리소스 사용을 분석할 수 있습니다. 예를 들어 애플리케이션 UI 프레임(레이아웃 및 렌더링)을 준비하고, 네트워크 및 디스크 요청을 처리하여, 애플리케이션 시작, 페이지 로드 및 창 크기 조정과 같은 시나리오에서 애플리케이션이 보낸 시간을 분석할 수 있습니다. 이 도구를 사용하려면 성능 프로파일러에서 **애플리케이션 타임라인**을 선택한 다음 **시작**을 선택합니다. 앱에서 리소스 소비 문제가 의심되는 시나리오를 확인한 다음 **컬렉션 중지**를 선택하여 보고서를 생성합니다.

**시각적 처리량** 그래프에서 낮은 framerate는 앱을 실행할 때 표시되는 시각적 문제에 해당할 수 있습니다. 마찬가지로 **UI 스레드 사용률** 그래프에서 높은 숫자는 UI 응답성 문제에 해당할 수 있습니다. 보고서에서 성능 문제가 의심되는 기간을 선택한 다음 타임라인 세부 정보 뷰(아래쪽 창)에서 세부 UI 스레드 활동을 검사할 수 있습니다.

![애플리케이션 타임라인 프로파일링 도구](../profiling/media/prof-tour-application-timeline.gif "애플리케이션 타임라인 프로파일링 둘러보기")

타임라인 세부 정보 뷰에서 작업 유형 또는 포함된 UI 요소와 작업 기간 등과 같은 정보를 확인할 수 있습니다. 예를 들어 그림에서 표 형태 컨트롤에 대한 **레이아웃** 이벤트는 57.53ms 걸렸습니다.

자세한 내용은 [애플리케이션 타임라인](../profiling/application-timeline.md)을 참조하세요.

## <a name="analyze-gpu-usage-direct3d"></a>GPU 사용량 분석(Direct3D)

Direct3D 앱(Direct3D 구성 요소가 C++에 있어야 함)에서 GPU에 대한 활동을 검사하고 성능 문제를 분석할 수 있습니다. 자세한 내용은 [GPU 사용량](/visualstudio/debugger/graphics/gpu-usage)을 참조하세요. 이 도구를 사용하려면 성능 프로파일러에서 **GPU 사용량**을 선택한 다음 **시작**을 선택합니다. 앱에서 프로파일링에 관심 있는 시나리오를 확인한 다음 **컬렉션 중지**를 선택하여 보고서를 생성합니다.

그래프에서 기간을 선택하고 **자세히 보기**를 선택하면 상세 보기가 아래쪽 창에 나타납니다. 상세 보기에서 각 CPU 및 GPU에서 얼마나 많은 활동이 발생하는지를 확인할 수 있습니다. 맨 아래 창에서 이벤트를 선택하면 타임라인에 팝업이 표시됩니다. 예를 들어 **현재** 이벤트를 선택하면 **현재** 호출 팝업이 표시됩니다. 연한 회색 Vsync 세로줄을 참조로 사용하여 특정 **현재** 호출에 Vsync가 누락되었는지 여부를 확인할 수 있습니다. 앱이 60 FPS를 꾸준히 적중하려면 두 Vsyncs마다 하나의 **현재** 호출이 있어야 합니다.

![GPU 사용량 프로파일링 도구](../profiling/media/prof-tour-gpu-usage.png "Diag GPU Usage")

또한 그래프를 사용하여 CPU 바인딩 또는 GPU 바인딩 성능 병목 현상이 있는지 여부를 확인할 수 있습니다.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>성능 분석(JavaScript UWP)

UWP 앱의 경우 JavaScript 메모리 도구 및 HTML UI 응답성 도구를 사용할 수 있습니다.

JavaScript 메모리 도구는 다른 앱 유형에 사용할 수 있는 메모리 사용량 도구와 비슷합니다. 이 도구를 사용하여 앱에서 메모리 사용량을 확인하고 메모리 누수를 파악할 수 있습니다. 도구에 대한 자세한 내용은 [JavaScript 메모리](../profiling/javascript-memory.md)를 참조하세요.

![JavaScript 메모리 프로파일링 도구](../profiling/media/diagjsmemory.png "DiagJSMemory")

UWP 앱에서 UI 응답성, 느린 로드 시간 및 느린 시각적 업데이트를 진단하려면 HTML UI 응답성 도구를 사용합니다. 사용량은 다른 앱 유형의 애플리케이션 타임라인 도구와 비슷합니다. 자세한 내용은 [HTML UI 응답성](../profiling/html-ui-responsiveness.md)을 참조하세요.

![HTML UI 응답성 프로파일링 도구](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>네트워크 사용량 분석(UWP)

UWP 앱에서 `Windows.Web.Http` API를 사용하여 수행된 네트워크 작업을 분석할 수 있습니다. 이 도구를 사용하면 액세스 및 인증 문제, 잘못된 캐시 사용, 잘못된 표시 및 다운로드 성능 등과 같은 문제를 해결할 수 있습니다. 이 도구를 사용하려면 성능 프로파일러에서 **네트워크**를 선택한 다음 **시작**을 선택합니다. 앱에서 `Windows.Web.Http`를 사용하는 시나리오를 확인한 다음 **컬렉션 중지**를 선택하여 보고서를 생성합니다.

![네트워크 사용량 프로파일링 도구](../profiling/media/prof-tour-network-usage.png "Diag Network Usage")

요약 뷰에서 작업을 선택하여 세부 정보를 확인할 수 있습니다.

![네트워크 사용량 도구의 세부 정보](../profiling/media/prof-tour-network-usage-details.png "Diag Network Usage Details")

자세한 내용은 [네트워크 사용량](../profiling/network-usage.md)을 참조하세요.
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>성능 분석(레거시 도구)

::: moniker range="vs-2017"
CPU 사용량 또는 메모리 사용량 도구에 현재 표시되지 않는 계측과 같은 기능이 필요하고 데스크톱 또는 ASP.NET 앱을 실행 중인 경우 성능 탐색기를 사용하여 프로파일링할 수 있습니다. (UWP 앱에서 지원되지 않음). 자세한 내용은 [성능 탐색기](../profiling/performance-explorer.md)를 참조하세요.
::: moniker-end

::: moniker range=">=vs-2019"
Visual Studio 2019에서는 레거시 성능 탐색기 및 성능 마법사와 같은 관련 프로파일링 도구가 성능 프로파일러로 중첩되었습니다. 이 프로파일러는 **디버그** > **성능 프로파일러**를 사용하여 열 수 있습니다. 성능 프로파일러에서 사용 가능한 진단 도구는 선택한 대상 및 현재 열려 있는 시작 프로젝트에 따라 달라집니다. CPU 사용량 도구는 이전에 성능 마법사에서 지원되었던 샘플링 기능을 제공합니다. 계측 도구는 성능 마법사에 있던 계측된 프로파일링 기능(정확한 호출 수 및 기간을 알 수 있는)을 제공합니다. 추가 메모리 도구가 성능 프로파일러에도 표시됩니다.
::: moniker-end

![성능 탐색기 도구](../profiling/media/prof-tour-performance-explorer.png "성능 탐색기")

## <a name="which-tool-should-i-use"></a>어떤 도구를 사용해야 하나요?

다음 테이블에는 Visual Studio가 제안하는 다양한 도구 및 그와 함께 사용할 수 있는 다양한 프로젝트 형식이 나열되어 있습니다.

::: moniker range=">=vs-2019"
|성능 도구|Windows 데스크톱|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU 사용량](../profiling/cpu-usage.md)|예|예|예|
|[메모리 사용량](../profiling/memory-usage.md)|예|예|예|
|[.NET 개체 할당](../profiling/dotnet-alloc-tool.md)|예(.NET만 해당)|예|예|
|[GPU 사용량](/visualstudio/debugger/graphics/gpu-usage)|예|예|아니요|
|[애플리케이션 타임라인](../profiling/application-timeline.md)|예|예|아니요|
|[PerfTips](../profiling/perftips.md)|예|XAML은 예, HTML은 no|예|
|[성능 탐색기](../profiling/performance-explorer.md)|예|아니요|예|
|[IntelliTrace](../debugger/intellitrace.md)|Visual Studio Enterprise만 포함된 .NET|Visual Studio Enterprise만 포함된 .NET|Visual Studio Enterprise만 포함된 .NET|
::: moniker-end

::: moniker range="vs-2017"
|성능 도구|Windows 데스크톱|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU 사용량](../profiling/cpu-usage.md)|예|예|예|
|[메모리 사용량](../profiling/memory-usage.md)|예|예|예|
|[GPU 사용량](/visualstudio/debugger/graphics/gpu-usage)|예|예|아니요|
|[애플리케이션 타임라인](../profiling/application-timeline.md)|예|예|아니요|
|[PerfTips](../profiling/perftips.md)|예|XAML은 예, HTML은 no|예|
|[성능 탐색기](../profiling/performance-explorer.md)|예|아니요|예|
|[IntelliTrace](../debugger/intellitrace.md)|Visual Studio Enterprise만 포함된 .NET|Visual Studio Enterprise만 포함된 .NET|Visual Studio Enterprise만 포함된 .NET|
|[네트워크 사용량](../profiling/network-usage.md)|아니요|예|아니요|
|[HTML UI 응답성](../profiling/html-ui-responsiveness.md)|아니요|HTML은 예, XAML은 no|아니요|
|[JavaScript 메모리](../profiling/javascript-memory.md)|아니요|HTML은 예, XAML은 no|아니요|
::: moniker-end


## <a name="see-also"></a>참고 항목
- [Visual Studio의 디버깅](../debugger/debugger-feature-tour.md)
