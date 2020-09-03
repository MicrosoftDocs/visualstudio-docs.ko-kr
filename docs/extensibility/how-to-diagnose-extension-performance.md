---
title: '방법: 확장 성능 진단 | Microsoft Docs'
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 542d8a6d6d90091aa7a800ef18f847fea6b1a81c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905914"
---
# <a name="measuring-extension-impact-in-startup"></a>시작 시 확장 영향 측정

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Visual Studio 2017의 확장 성능에 집중

고객 피드백에 따라 Visual Studio 2017 릴리스의 주요 영역 중 하나는 시작 및 솔루션 로드 성능입니다. Visual Studio 플랫폼 팀은 시작 및 솔루션 로드 성능을 향상 시키기 위해 노력 하 고 있습니다. 일반적으로 측정 된 확장은 해당 시나리오에 상당한 영향을 줄 수 있습니다.

사용자가 이러한 영향을 이해할 수 있도록 Visual Studio의 새로운 기능을 추가 하 여 저속 확장을 사용자에 게 알립니다. 경우에 따라 Visual Studio는 솔루션 로드 또는 시작 속도를 저하 시키는 새 확장을 검색 합니다. 속도가 느려지는 경우 사용자에 게 IDE에서 새로운 "Visual Studio 성능 관리" 대화 상자를 가리키는 알림이 표시 됩니다. 이 대화 상자는 이미 검색 된 확장을 검색 하기 위해 도움말 메뉴에서 항상 액세스할 수도 있습니다.

![Visual Studio 성능 관리](media/manage-performance.png)

이 문서에서는 확장 프로그램의 영향을 계산 하는 방법을 설명 하 여 확장 개발자에 게 도움을 줍니다. 이 문서에서는 확장 영향을 로컬에서 분석 하는 방법에 대해서도 설명 합니다. 확장 프로그램 영향을 로컬로 분석 하면 확장을 성능에 영향을 주는 확장으로 표시할 수 있는지 여부를 결정 합니다.

> [!NOTE]
> 이 문서에서는 시작 및 솔루션 로드에 대 한 확장의 영향에 대해 집중적으로 설명 합니다. 확장은 UI가 응답 하지 않을 경우 Visual Studio 성능에도 영향을 줍니다. 이 항목에 대 한 자세한 내용은 [방법: 확장으로 인 한 UI 지연 진단](how-to-diagnose-ui-delays-caused-by-extensions.md)을 참조 하세요.

## <a name="how-extensions-can-impact-startup"></a>확장이 시작에 영향을 줄 수 있는 방법

시작 성능에 영향을 주는 확장 프로그램에 대 한 가장 일반적인 방법 중 하나는 NoShellInitialized Exists 또는와 같은 알려진 시작 UI 컨텍스트 중 하나에서 자동 로드를 선택 하는 것입니다. 이러한 UI 컨텍스트는 시작 시 활성화 됩니다. 해당 컨텍스트를 사용 하 여 해당 정의에 특성을 포함 하는 모든 패키지는 `ProvideAutoLoad` 해당 시점에 로드 되 고 초기화 됩니다.

확장의 영향을 측정할 때 주로 위의 컨텍스트에서 자동 로드를 선택 하는 확장에 소요 되는 시간에 중점을 둡니다. 측정 된 시간에는 다음이 포함 되지만이에 제한 되지 않습니다.

* 동기 패키지에 대 한 확장 어셈블리 로드
* 동기 패키지의 package class 생성자에 소요 된 시간
* 동기 패키지에 대해 package Initialize (또는 SetSite) 메서드에 소요 된 시간
* 비동기 패키지의 경우 위의 작업은 백그라운드 스레드에서 실행 됩니다.  따라서 작업은 모니터링에서 제외 됩니다.
* 주 스레드에서 실행 되도록 패키지를 초기화 하는 동안 예약 된 비동기 작업에 소요 된 시간
* 이벤트 처리기에서 소요 된 시간, 특히 셸 초기화 컨텍스트 활성화 또는 셸 좀비 상태 변경
* Visual Studio 2017 업데이트 3부터 셸이 초기화 되기 전에 유휴 호출에 소요 된 시간 모니터링을 시작 합니다. 유휴 처리기에서 긴 작업을 수행 하면 IDE가 응답 하지 않으며 사용자가 인식 하는 시작 시간에 기여 하 게 됩니다.

Visual Studio 2015에서 시작 하는 많은 기능을 추가 했습니다. 이러한 기능을 사용 하면 패키지를 자동으로 로드할 필요가 없습니다. 또한이 기능을 통해 패키지를 더 구체적인 경우에 로드 해야 하는 필요성을 연기할 수 있습니다. 이러한 경우에는 사용자가 확장을 사용 하거나 자동으로 로드할 때 확장의 영향을 줄이는 것이 더 확실 한 예제가 포함 됩니다.

이러한 기능에 대 한 자세한 내용은 다음 문서에서 찾을 수 있습니다.

[규칙 기반 ui 컨텍스트](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): ui 컨텍스트를 기반으로 작성 된 보다 다양 한 규칙 기반 엔진을 사용 하 여 프로젝트 형식, 특색 및 특성을 기반으로 사용자 지정 컨텍스트를 만들 수 있습니다. 사용자 지정 컨텍스트는 보다 구체적인 시나리오에서 패키지를 로드 하는 데 사용할 수 있습니다. 이러한 특정 시나리오에는 시작 대신 특정 기능을 포함 하는 프로젝트가 있습니다. 사용자 지정 컨텍스트를 사용 하면 프로젝트 구성 요소나 기타 사용 가능한 조건에 따라 [사용자 지정 컨텍스트에 명령 표시 유형을](visibilityconstraints-element.md) 연결할 수도 있습니다. 이 기능은 패키지를 로드 하 여 명령 상태 쿼리 처리기를 등록 하지 않아도 됩니다.

[비동기 패키지 지원](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): 자동 로드 특성이 나 비동기 서비스 쿼리에서 패키지 로드를 요청 하는 경우 visual studio 2015의 새 asyncpackage 기본 클래스를 사용 하 여 visual studio 패키지를 백그라운드에서 비동기적으로 로드할 수 있습니다. 이 백그라운드 로드를 통해 IDE는 응답성을 유지할 수 있습니다. 확장은 백그라운드에서 초기화 되 고 시작 및 솔루션 로드와 같은 중요 한 시나리오에는 영향을 받지 않지만 IDE는 응답성이 향상 됩니다.

[비동기 서비스](how-to-provide-an-asynchronous-visual-studio-service.md): 비동기 패키지 지원을 사용 하면 서비스를 비동기적으로 쿼리하고 비동기 서비스를 등록할 수 있는 지원도 추가 했습니다. 비동기 쿼리에서 대부분의 작업이 백그라운드 스레드에서 발생 하도록 핵심 Visual Studio 서비스를 비동기 쿼리를 지원 하도록 변환 하는 것이 더 중요 합니다. SComponentModel (Visual Studio MEF 호스트)는 확장이 비동기 로드를 완전히 지원할 수 있도록 비동기 쿼리를 지 원하는 주요 서비스 중 하나입니다.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>자동 로드 된 확장의 영향 줄이기

시작할 때 패키지를 자동으로 로드 해야 하는 경우 패키지를 초기화 하는 동안 수행 되는 작업을 최소화 하는 것이 중요 합니다. 패키지 초기화 작업을 최소화 하면 확장의 시작에 영향을 줄 가능성이 줄어듭니다.

패키지 초기화의 비용이 많이 들 수 있는 몇 가지 예는 다음과 같습니다.

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>비동기 패키지 로드 대신 동기 패키지 로드 사용

기본적으로 동기 패키지는 주 스레드에 로드 되므로 앞에서 설명한 대로 비동기 패키지 기본 클래스를 사용 하도록 자동으로 로드 된 패키지를 포함 하는 확장 소유자가 권장 됩니다. 비동기 로드를 지원 하도록 자동 로드 된 패키지를 변경 하면 아래의 다른 문제를 더 쉽게 해결할 수 있습니다.

### <a name="synchronous-filenetwork-io-requests"></a>동기 파일/네트워크 IO 요청

이상적으로는 주 스레드에서 모든 동기 파일 또는 네트워크 IO 요청을 피해 야 합니다. 이러한 영향은 컴퓨터 상태에 따라 달라 지 며 경우에 따라 장기간 차단 될 수 있습니다.

비동기 패키지 로드 및 비동기 IO Api를 사용 하면 패키지 초기화에서 주 스레드를 차단 하지 않는지 확인 해야 합니다. 또한 사용자는 백그라운드에서 i/o 요청이 발생 하는 동안 Visual Studio와 계속 상호 작용할 수 있습니다.

### <a name="early-initialization-of-services-components"></a>서비스의 초기 초기화, 구성 요소

패키지 초기화의 일반적인 패턴 중 하나는에서 사용 하거나 패키지 또는 메서드에서 해당 패키지에서 제공 하는 서비스를 초기화 하는 것입니다 `constructor` `initialize` . 이를 통해 서비스를 사용할 수 있지만, 해당 서비스가 즉시 사용 되지 않는 경우 패키지 로드에 불필요 한 비용을 추가할 수도 있습니다. 대신 패키지 초기화에서 수행 되는 작업을 최소화 하기 위해 필요에 따라 이러한 서비스를 초기화 해야 합니다.

패키지에서 제공 하는 전역 서비스의 경우 함수를 사용 하는 메서드를 사용 하 여 `AddService` 구성 요소에서 요청 하는 경우에만 서비스를 지연 초기화할 수 있습니다. 패키지 내에서 사용 되는 서비스의 경우 Lazy \<T> 또는 AsyncLazy \<T> 를 사용 하 여 처음 사용할 때 서비스가 초기화/쿼리 되도록 할 수 있습니다.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>활동 로그를 사용 하 여 자동 로드 된 확장의 영향 측정

Visual Studio 2017 업데이트 3부터 Visual Studio 활동 로그에는 시작 및 솔루션 로드 중 패키지의 성능 영향에 대 한 항목이 포함 됩니다. 이러한 측정값을 보려면/log 스위치를 사용 하 여 Visual Studio를 열고 *ActivityLog.xml* 파일을 열어야 합니다.

활동 로그에서 항목은 "Visual Studio 성능 관리" 소스 아래에 있으며 다음 예제와 같이 표시 됩니다.

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

이 예제에서는 GUID가 "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" 인 패키지가 Visual Studio를 시작 하는 데 2008 밀리초를 할애 함을 보여 줍니다. Visual Studio는 패키지에 대 한 확장을 사용 하지 않도록 설정 하는 경우 사용자에 게 표시 되는 것 처럼 패키지의 영향을 계산할 때 최상위 비용을 기본 숫자로 간주 합니다.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>PerfView를 사용 하 여 자동 로드 된 확장의 영향 측정

코드 분석은 패키지 초기화 속도를 저하 시킬 수 있는 코드 경로를 식별 하는 데 도움이 되지만, PerfView와 같은 응용 프로그램을 사용 하 여 추적을 활용 하 여 Visual Studio 시작 시 패키지 로드의 영향을 이해할 수도 있습니다.

PerfView는 시스템 차원 추적 도구입니다. 이 도구는 CPU 사용량 또는 차단 시스템 호출 때문에 응용 프로그램의 핫 경로를 이해 하는 데 도움이 됩니다. 다음은 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=28567)에서 제공 되는 perfview를 사용 하 여 샘플 확장을 분석 하는 간단한 예제입니다.

**예제 코드:**

이 예제는 다음과 같은 몇 가지 일반적인 지연 원인을 보여 주기 위해 설계 된 아래의 샘플 코드를 기반으로 합니다.

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**PerfView를 사용 하 여 추적 기록:**

확장이 설치 된 Visual Studio 환경을 설정한 후에는 PerfView를 열고 **수집** 메뉴에서 **수집** 대화 상자를 열어 시작 추적을 기록할 수 있습니다.

![perfview 수집 메뉴](media/perfview-collect-menu.png)

기본 옵션은 CPU 소비에 대 한 호출 스택을 제공 하지만, 차단 시간에도 관심이 있으므로 **스레드 시간** 스택을 사용 하도록 설정 해야 합니다. 설정이 준비 되 면 **수집 시작** 을 클릭 한 다음 기록이 시작 된 후 Visual Studio를 열 수 있습니다.

수집을 중지 하기 전에 Visual Studio가 완전히 초기화 되었는지 확인 하 고, 주 창이 완전히 표시 되 고, 확장에 자동으로 표시 되는 UI 부분이 있으면 표시 됩니다. Visual Studio가 완전히 로드 되 고 확장이 초기화 되 면 기록을 중지 하 여 추적을 분석할 수 있습니다.

**PerfView를 사용 하 여 추적 분석:**

기록이 완료 되 면 PerfView에서 추적 및 확장 옵션을 자동으로 엽니다.

이 예제의 목적을 위해 주로 **고급 그룹**에서 찾을 수 있는 **스레드 시간 스택** 보기에 관심이 있습니다. 이 보기에는 CPU 시간과 차단 된 시간 (예: 디스크 IO 또는 핸들 대기)을 모두 포함 하는 메서드에 의해 스레드에 소요 된 총 시간이 표시 됩니다.

 ![스레드 시간 스택](media/perfview-thread-time-stacks.png)

 **스레드 시간 스택** 보기를 여는 동안 분석을 시작 하려면 **devenv** 프로세스를 선택 해야 합니다.

PerfView에는 자세한 분석을 위해 자체 도움말 메뉴에서 스레드 시간 스택을 읽는 방법에 대 한 자세한 지침이 있습니다. 이 예에서는 패키지 모듈 이름 및 시작 스레드를 포함 하는 스택만 포함 하 여이 뷰를 추가로 필터링 하려고 합니다.

1. 기본적으로 추가 된 모든 그룹화를 제거 하려면 **GroupPats** 를 빈 텍스트로 설정 합니다.
2. **IncPats** 를 설정 하 여 기존 프로세스 필터 외에도 어셈블리 이름 및 시작 스레드의 일부를 포함 하도록 설정 합니다. 이 경우에는 devenv 여야 합니다 **. 시작 스레드 Make의 Lowlowextension**.

이제 보기에는 확장과 관련 된 어셈블리와 관련 된 비용도 표시 됩니다. 이 뷰에서 시작 스레드의 **Inc (포괄 비용)** 열 아래에 나열 된 시간은 필터링 된 확장과 관련 되며 시작에 영향을 줍니다.

위의 예제에서 몇 가지 흥미로운 호출 스택은 다음과 같습니다.

1. 클래스를 사용 하는 IO `System.IO` : 이러한 프레임의 포괄 비용은 추적에 너무 많은 비용이 들지 않을 수 있지만 파일 IO 속도가 컴퓨터 마다 다르기 때문에 문제의 원인일 수 있습니다.

   ![시스템 io 프레임](media/perfview-system-io-frames.png)

2. 다른 비동기 작업을 기다리는 호출 차단:이 경우 포괄 시간은 비동기 작업이 완료 될 때 주 스레드가 차단 되는 시간을 나타냅니다.

   ![호출 프레임 차단](media/perfview-blocking-call-frames.png)

영향을 확인 하는 데 유용한 추적의 다른 뷰 중 하나는 **이미지 로드 스택입니다**. **스레드 시간 스택** 보기에 적용 되는 것과 동일한 필터를 적용 하 고 자동 로드 된 패키지에 의해 실행 되는 코드로 인해 로드 된 모든 어셈블리를 찾을 수 있습니다.

패키지 초기화 루틴 내에 로드 된 어셈블리 수를 최소화 하는 것이 중요 합니다. 각 추가 어셈블리에 추가 디스크 i/o가 포함 되므로 느린 컴퓨터에서 시작 속도가 느려질 수 있습니다.

## <a name="summary"></a>요약

Visual Studio를 시작 하는 것은 지속적으로 피드백을 받는 영역 중 하나입니다. 앞에서 설명한 것과 같은 목표는 설치 된 구성 요소 및 확장에 관계 없이 모든 사용자가 일관 된 시작 환경을 갖도록 하는 것입니다. 이러한 목표를 달성 하는 데 도움이 되도록 확장 소유자에 게 문의 하 고 싶습니다. 위의 지침은 시작할 때 확장에 미치는 영향을 이해 하 고, 사용자 생산성에 대 한 영향을 최소화 하기 위해 비동기적으로 자동 로드 또는 로드 하지 않아도 되는 경우에 유용 합니다.
