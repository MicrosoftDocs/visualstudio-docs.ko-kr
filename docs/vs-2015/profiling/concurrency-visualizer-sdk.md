---
title: 동시성 시각화 도우미 SDK | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ed93d852e385a6130cd37b0f66c99b4f0ab467bc
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586806"
---
# <a name="concurrency-visualizer-sdk"></a>동시성 시각화 도우미 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미에서 추가 정보를 표시하도록 동시성 시각화 도우미 SDK를 사용하여 소스 코드를 계측할 수 있습니다. 코드의 단계 및 이벤트와 추가 데이터를 연결할 수 있습니다. 이러한 추가 시각화를 *표식*이라고 합니다.  소개 연습에 대해서는 [Introducing the Concurrency Visualizer SDK](https://docs.microsoft.com/archive/blogs/visualizeparallel/introducing-the-concurrency-visualizer-sdk)(동시성 시각화 도우미 SDK 소개)를 참조하세요.

## <a name="properties"></a>속성
 각 플래그, 범위 및 메시지에는 두 개의 속성인 범주와 중요도가 있습니다. [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자에서, 이러한 속성을 사용하여 표시되는 표식의 집합을 필터링할 수 있습니다. 또한 이러한 속성은 표식의 시각적 표시에 영향을 줍니다. 예를 들어 플래그의 크기는 중요도를 나타내는 데 사용됩니다. 또한 색은 범주를 나타내는 데 사용됩니다.

## <a name="basic-usage"></a>기본 사용
 동시성 시각화 도우미에서 표식을 생성하는 데 사용할 수 있는 기본 공급자를 표시합니다. 공급자는 이미 동시성 시각화 도우미에 등록되어 있으며 표식을 UI에 표시하기 위해 다른 작업을 수행할 필요가 없습니다.

### <a name="c-and-visual-basic"></a>C# 및 Visual Basic

C#, Visual Basic 및 기타 관리 코드에서 [Markers](/previous-versions/hh694099(v=vs.140)) 클래스의 메서드를 호출하여 기본 공급자를 사용하세요. 그러면 표식을 생성하는 네 가지 메서드 [WriteFlag](/previous-versions/hh694185(v=vs.140)), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140)) 및 [WriteAlert](/previous-versions/hh694180(v=vs.140))가 표시됩니다. 속성에 대한 기본값을 사용하려는지 여부에 따라 이러한 함수에 대한 오버로드가 여러 개 있습니다.  가장 간단한 오버로드는 이벤트에 대한 설명을 지정하는 문자열 매개 변수만 사용합니다. 설명은 동시성 시각화 보고서에 표시됩니다.

#### <a name="add-sdk-support-to-a-c-or-visual-basic-project"></a>C # 또는 Visual Basic 프로젝트에 SDK 지원 추가

1. 메뉴 모음에서 **분석**, **동시성 시각화 도우미**, **프로젝트에 SDK 추가**를 선택합니다.

2. SDK에 액세스하려는 프로젝트를 선택한 다음 **선택한 프로젝트에 SDK 추가** 단추를 선택합니다.

3. Imports 또는 using 문을 코드에 추가합니다.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 C++에서 [marker_series 클래스](../profiling/marker-series-class.md) 개체를 만들고 이를 사용하여 함수를 호출합니다.  `marker_series` 클래스는 [marker_series:: write_flag 메서드](../profiling/marker-series-write-flag-method.md), [marker_series:: write_message 메서드](../profiling/marker-series-write-message-method.md) 및 [marker_series:: write_alert 메서드](../profiling/marker-series-write-alert-method.md) 표식을 생성하기 위한 세 가지 함수를 표시합니다.

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>C++ 또는 C 프로젝트에 SDK 지원을 추가하려면

1. 메뉴 모음에서 **분석**, **동시성 시각화 도우미**, **프로젝트에 SDK 추가**를 선택합니다.

2. SDK에 액세스하려는 프로젝트를 선택한 다음 **선택한 프로젝트에 SDK 추가** 단추를 선택합니다.

3. C++의 경우 `cvmarkersobj.h`를 포함합니다. C의 경우 `cvmarkers.h`를 포함합니다.

4. using 문을 코드에 추가합니다.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. `marker_series` 개체를 만들고 이를 `span` 생성자에 전달합니다.

    ```cpp
    marker_series mySeries;
    span s(mySeries, _T("Span description"));
    ```

## <a name="custom-usage"></a>사용자 지정 사용
 고급 시나리오의 경우 동시성 시각화 도우미 SDK에서 더 많은 제어를 제공합니다. 표식 공급자 및 표식 계열의 두 가지 주요 개념은 보다 고급 시나리오와 연결됩니다. 표식 공급자는 서로 다른 ETW 공급자(각기 다른 GUID 보유)입니다. 표식 계열은 한 공급자에서 생성하는 일련의 이벤트 채널입니다. 이를 사용하여 표식 공급자에서 생성하는 이벤트를 구성할 수 있습니다.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>C# 또는 Visual Basic 프로젝트에서 새 표식 공급자를 사용하려면

1. [MarkerWriter](/previous-versions/hh694138(v=vs.140)) 개체를 만듭니다. 생성자는 GUID를 사용합니다.

2. 공급자를 등록하려면 동시성 시각화 도우미 [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자를 엽니다.  **표식** 탭을 선택한 다음 **새 공급자 추가** 단추를 선택합니다. [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자에서 공급자 및 공급자에 대한 설명을 만드는 데 사용된 GUID를 입력합니다.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>C++ 또는 C 프로젝트에서 새 표식 공급자를 사용하려면

1. `CvInitProvider` 함수를 사용하여 PCV_PROVIDER를 초기화합니다. 생성자는 GUID *와 PCV_PROVIDER\*를 사용 합니다.

2. 공급자를 등록하려면 [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자를 엽니다. **표식** 탭을 선택한 다음 **새 공급자 추가** 단추를 선택합니다. 이 대화 상자에서 공급자 및 공급자에 대한 설명을 만드는 데 사용된 GUID를 입력합니다.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>C# 또는 Visual Basic 프로젝트에서 표식 계열을 사용하려면

1. 새 [MarkerSeries](/previous-versions/hh694127(v=vs.140))를 사용하려면 먼저 [MarkerWriter](/previous-versions/hh694138(v=vs.140)) 개체를 사용하여 이를 만든 다음, 새 계열에서 직접 표식 이벤트를 생성합니다.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);
    series1.WriteFlag(″My flag″);
    ```

    ```vb
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)
    series1.WriteFlag(″My flag″)
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>C++ 프로젝트에서 표식 계열을 사용하려면

1. `marker_series` 개체를 만듭니다.  새 계열에서 이벤트를 생성할 수 있습니다.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>C 프로젝트에서 표식 계열을 사용하려면

1. `CvCreateMarkerSeries` 함수를 사용하여 PCV_MARKERSERIES를 만듭니다.

    ```cpp
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[C + + 라이브러리 참조](../profiling/cpp-library-reference.md)|C++용 동시성 시각화 도우미 API를 설명합니다.|
|[C 라이브러리 참조](../profiling/c-library-reference.md)|C용 동시성 시각화 도우미 API를 설명합니다.|
|[계측](/previous-versions/hh694104(v=vs.140))|관리 코드용 동시성 시각화 도우미 API를 설명합니다.|
|[동시성 시각화 도우미](../profiling/concurrency-visualizer.md)|동시성 방법을 사용하여 생성되고 스레드 실행 데이터를 포함하는 프로파일링 데이터 파일의 뷰 및 보고서에 대한 정보를 참조합니다.|
