---
title: UWP 앱의 에너지 사용 분석 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
monikerRange: vs-2017
ms.openlocfilehash: 0fc78a84d0c2f86e8db6c4703cc7404a32508d72
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73144738"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>UWP 앱의 에너지 사용 분석

Visual Studio **에너지 소비** 프로파일러를 사용하면 자체 배터리로 전부 또는 일부의 시간 동안 실행하는 저전력 태블릿 디바이스에서 UWP 앱의 전력 및 에너지 소비를 분석할 수 있습니다. 배터리로 구동하는 디바이스에서 앱이 너무 많은 에너지를 사용할 경우 고객 불만족을 일으킬 수 있고, 결과적으로 고객이 설치를 제거할 수도 있습니다. 에너지 사용을 최적화하면 고객이 앱을 채택하고 사용하는 사례가 증가할 수 있습니다.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>에너지 소비 프로파일러 소개, 작동 방법 및 측정 대상

에너지 소비 프로파일러는 세션을 프로파일링하는 중 디바이스의 디스플레이, CPU, 네트워크 연결 활동을 캡처합니다. 그런 다음 그러한 활동에 사용된 전력과 세션 프로파일링의 총 에너지량의 추정치를 생성합니다.

> [!NOTE]
> 에너지 프로파일러는 표준 참조 디바이스 하드웨어를 사용하여 애플리케이션을 실행하는 저전력 태블릿 디바이스의 대표적 전력 및 에너지 사용을 추정합니다. 가장 정확한 추정치를 제공하려면 저전력 태블릿 디바이스에서 프로파일 데이터를 수집하는 것이 좋습니다.
>
> 이 모델은 다양한 저전력 디바이스에 대해 상당히 정확한 추정치를 제공하지만 프로파일링하는 디바이스의 실제 값은 달라질 가능성이 높습니다. 이러한 값을 사용하여 다른 리소스 사용에 비해 많은 에너지를 사용하고 있어서 최적화해야 할 디스플레이, CPU, 네트워크 활동을 찾습니다.

에너지 소비 프로파일러는 이러한 *전원* 및 *에너지*에 대한 정의를 사용합니다.

- *전원* 은 일정 시간 동안 일을 수행하는 데 사용된 힘의 효율을 측정합니다. 전기 과학에서 전력의 표준 단위는 *와트*입니다. 와트는 1암페어의 전류가 1볼트의 전위 차이를 통해 흐를 때 작업이 수행되는 속도로 정의됩니다. **전원 사용** 그래프에서 단위가 **mW** (밀리와트)로 표시되고 1mW는 1W의 1/1000에 해당합니다.

   전력은 속도이므로 방향(일정 시간 동안 작업이 증가하거나 감소할 수 있음)과 속도(작업이 증가하거나 감소하는 양)가 있습니다.

- *에너지* 는 배터리의 전력 용량과 같이 총 전력량을 용량 또는 전위로 측정하거나 일정 기간 동안 사용된 총 전력량으로 측정합니다. 에너지 단위는 1시간 동안 1와트가 일정하게 적용된 전력량인 와트-시간입니다. **에너지 요약**에서 단위가 **mW-h**(밀리와트시)로 표시됩니다.

![에너지 양, 사용한 전원, 사용한 전체 에너지](../profiling/media/energyprof_capcitypowerused.png)

예를 들어, 태블릿의 완전히 충전된 배터리에는 저장된 에너지가 상당히 많습니다. 네트워크 통신, 값 계산, 그래픽 표시 등의 작업을 수행하는 데 에너지를 사용하므로 다른 속도로 배터리 전력이 소실됩니다. 특정 기간 동안 소비된 총 전력도 에너지로 측정합니다.

## <a name="identify-scenarios-with-user-marks"></a>사용자 표시로 시나리오 식별
 프로파일링 데이터에 *사용자 표시* 를 추가하여 타임라인 눈금자의 영역을 식별할 수 있습니다.

 ![타임라인의 사용자 표시](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 이 표시는 메서드 실행 시 타임라인에 주황색 삼각형으로 표시됩니다. 이 표시를 마우스로 가리키면 메시지와 시간이 도구 설명으로 표시됩니다. 두 개 이상의 사용자 표시가 서로 가까이 있으면 표시가 병합되고 도구 설명 데이터가 결합됩니다. 타임라인을 확대하면 표시가 분리되어 표시됩니다.

 **C#, Visual Basic, C++ 코드에 표시 추가**

 C#, Visual Basic, C++ 코드에 사용자 표시를 추가하려면 <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> 개체를 먼저 만듭니다. 그런 다음, 표시할 코드의 지점의 <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> 메서드에 호출을 삽입합니다. 호출에 [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) 을 사용합니다.

 메서드가 실행되면 프로파일링 데이터에 사용자 표시와 메시지가 추가됩니다.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType>은 <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> 인터페이스(C# 및 VB에서 <xref:System.IDisposable?displayProperty=nameWithType>로 프로젝션됨)를 구현합니다. 운영 체제 리소스가 누락되지 않도록 하려면 로깅 채널이 완료될 때 <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType>(C# 및 VB에서 <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType>)를 호출합니다.
> - 열린 각 로깅 채널의 이름은 고유해야 합니다. 삭제되지 않은 채널과 이름이 같은 새 로깅 채널을 만들려고 시도하면 예외가 throw됩니다.

예제 코드는 Windows SDK 샘플 [LoggingSession sample](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)(LoggingSession 샘플)을 참조하세요.

::: moniker range="vs-2017"
**JavaScript 코드에 표시 추가**

사용자 표시를 추가하려면 표시할 코드의 지점에 다음 코드를 추가합니다.

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription* 은 사용자 표시 도구 설명에 표시할 메시지가 포함되는 문자열입니다.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>프로파일링을 위한 환경 구성
 더 정확하게 예측하려면 배터리 전원을 사용하는 저전력 디바이스에서 앱의 에너지 사용을 프로파일링합니다. Visual Studio는 이러한 디바이스에서 대부분 실행되지 않으므로 Visual Studio 원격 도구를 사용하여 디바이스에 Visual Studio 컴퓨터를 연결해야 합니다. 원격 디바이스에 연결하려면 Visual Studio 프로젝트와 원격 디바이스를 모두 구성해야 합니다. 자세한 내용은 [원격 컴퓨터에서 UWP 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조하세요.

> [!TIP]
> - UWP 시뮬레이터 또는 Visual Studio 컴퓨터에서 에너지 프로파일링이 권장되지 않습니다. 실제 디바이스에서 프로파일링할 경우 실제에 훨씬 더 가까운 데이터가 제공됩니다.
> - 대상 디바이스에 배터리 전원을 연결한 상태에서 프로파일링합니다.
> - 동일한 리소스(네트워크, CPU 또는 디스플레이)를 사용할 수 있는 다른 앱을 닫습니다.

## <a name="collect-energy-profile-data-for-your-app"></a>앱의 에너지 프로파일 데이터 수집

1. **디버그** 메뉴에서 **디버그하지 않고 진단 시작**을 선택합니다.

     ![진단 허브에서 에너지 소비 선택](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. **에너지 소비** 를 선택한 다음 **시작**을 선택합니다.

    > [!NOTE]
    > **에너지 소비** 프로파일러를 시작하면 **VsEtwCollector.exe** 실행 권한을 요청하는 *사용자 계정 제어* 창이 나타날 수 있습니다. **예**를 선택합니다.

3. 데이터를 수집하려면 앱을 실행합니다.

4. 프로파일링을 중지하려면 Visual Studio로 다시 전환하고(Alt + Tab) 진단 허브 페이지에서 **수집 중지** 를 선택합니다.

     ![데이터 수집 중지](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Visual Studio에서는 수집된 데이터를 분석하고 결과를 표시합니다.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>설치된 에너지 프로파일 데이터 수집
 에너지 소비 도구는 Visual Studio 솔루션에서 시작하거나 Microsoft Store에서 설치하는 UWP 앱에서만 실행할 수 있습니다. 솔루션을 Visual Studio에서 열 경우 기본 대상은 **시작 프로젝트**입니다. 설치된 앱을 대상으로 하려면

1. **대상 변경** 을 선택한 다음 **설치된 응용 프로그램**을 선택합니다.

2. **설치된 응용 프로그램 패키지 선택** 목록에서 대상을 선택합니다.

3. 진단 허브 페이지에서 **에너지 소비** 를 선택합니다.

4. 프로파일링을 시작하려면 **시작** 을 선택합니다.

   프로파일링을 중지하려면 Visual Studio로 다시 전환하고(Alt + Tab) 진단 허브 페이지에서 **수집 중지** 를 선택합니다.

## <a name="analyze-energy-profile-data"></a>에너지 프로파일 데이터 분석
 에너지 프로필 데이터가 Visual Studio 문서 창에 표시됩니다.

 ![에너지 프로파일러 보고서 페이지](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|||
|-|-|
|![1단계](../profiling/media/procguid_1.png "ProcGuid_1")|보고서 파일의 이름은 Report*YYYYMMDD-HHMM*.diagsession입니다. 보고서를 저장할 경우 이름을 변경할 수 있습니다.|
|![2단계](../profiling/media/procguid_2.png "ProcGuid_2")|타임라인에는 프로파일링 세션 길이, 응용 프로그램 수명 주기 시작 이벤트 및 사용자 표시가 표시됩니다.|
|![3단계](../profiling/media/procguid_3.png "ProcGuid_3")|파란색 막대를 끌어 타임라인의 부분의 선택하여 보고서를 타임라인의 일부분으로 제한할 수 있습니다.|
|![4단계](../profiling/media/procguid_4.png "ProcGuid_4")|**전원 사용** 그래프는 프로파일링 세션 동안 디바이스 리소스로 발생하는 전원 출력의 변화를 나타내는 다중선형 차트입니다. 에너지 소비 프로파일러는 CPU, 네트워크 작업 및 화면 디스플레이에서 사용하는 전력을 추적합니다.|
|![5단계](../profiling/media/procguid_6.png "ProcGuid_6")|**리소스(설정/해제)**  그래프는 네트워크 에너지 소비에 대한 자세한 정보를 제공합니다. **네트워크** 표시줄은 네트워크 연결이 열려 있던 시간을 나타냅니다. **데이터 전송** 하위 막대는 앱에서 네트워크를 통해 데이터를 수신하거나 송신하는 시간을 나타냅니다.|
|![6단계](../profiling/media/procguid_6a.png "ProcGuid_6a")|**에너지 사용 요약** 에서는 선택한 타임라인에서 CPU, 네트워크 작업 및 화면 디스플레이 사용에 비례하는 총 에너지양을 보여 줍니다.|

 **에너지 프로필 데이터를 분석하려면**

 리소스 전력이 가장 많이 사용되는 부분을 찾습니다. 최고 영역을 앱의 기능에 연결합니다. 그런 다음 타임라인에서 타임라인 제어 막대를 사용하여 영역을 확대합니다. 네트워크 사용에 초점을 두는 경우 **리소스(설정/해제)** 그래프에서 **네트워크**  노드를 확장하여 앱이 연결을 통해 데이터를 수신하거나 전송하는 시간에 대해 네트워크 연결이 열리는 시간을 비교합니다. 네트워크가 불필요하게 열리는 시간을 줄이는 것은 매우 효과적인 최적화입니다.

## <a name="optimize-energy-use"></a>에너지 사용 최적화
 네트워크 연결에서는 데이터 전송 이외에 연결 초기화, 유지, 종료의 에너지 비용이 발생합니다. 일부 네트워크는 단일 연결에서 더 많은 데이터를 전송할 수 있도록 데이터가 전송 또는 수신된 후 일정 기간 동안 연결을 유지합니다. **리소스(설정/해제)** 창을 사용하여 앱이 연결과 상호 작용하는 방법을 검사할 수 있습니다.

 ![리소스 &#40;On&#47;Off&#41; 창](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 **네트워크** 및 **데이터 전송** 막대에서 일련의 작은 데이터 패킷을 가끔 전송하기 위해 오랜 시간 동안 연결이 열려 있다고 표시되는 경우, 데이터를 한번에 전송하도록 일괄 처리하여 네트워크가 열려 있는 시간을 줄이고 에너지 소비도 절약할 수 있습니다.

 ![에너지 소비 요약 창](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 디스플레이의 에너지 비용에 대한 제어 권한이 적습니다. 대부분의 화면은 어두운 색을 표시할 때보다 밝은 색을 표시할 때 더 많은 에너지를 필요로 하므로 어두운 배경을 사용하는 것은 비용을 줄이는 한 가지 방법입니다.

## <a name="other-resources"></a>기타 리소스

- **C#/VB/C++ 및 XAML**의 [연결 상태 및 비용 관리](/previous-versions/windows/apps/hh452985\(v\=win.10\)) 섹션에서는 앱이 네트워크 트래픽 비용을 최소화하는 데 사용할 수 있는 네트워크 연결 정보를 제공하는 Windows API에 대해 설명합니다.

   UWP 앱에 대한 Visual Studio 시뮬레이터를 사용하여 네트워크 정보 API의 데이터 연결 속성을 시뮬레이션할 수 있습니다. [시뮬레이터에서 UWP 앱 실행](../debugger/run-windows-store-apps-in-the-simulator.md)을 참조하세요.

- **CPU 사용** 도구를 사용하면 비효율적 함수 때문에 발생하는 CPU 로드를 줄일 수 있습니다. [CPU 사용량 분석](../profiling/beginners-guide-to-performance-profiling.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 프로파일링](../profiling/index.yml)
- [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)