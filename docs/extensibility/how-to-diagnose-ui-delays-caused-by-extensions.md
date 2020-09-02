---
title: Visual Studio에서 확장 UI 지연 진단 | Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: e8b35a566eb0f2457d6eb8ae3a33235df2a64cd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849157"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>방법: 확장으로 인해 발생한 진단 UI 지연

UI가 응답 하지 않을 경우 Visual Studio는 리프에서 시작 하 여 기본으로 작업 하는 UI 스레드의 호출 스택을 검사 합니다. Visual Studio가 설치 되 고 사용 하도록 설정 된 확장의 일부인 모듈에 속해 있는지 확인 하는 경우 알림을 표시 합니다.

![UI 지연 (응답 하지 않음) 알림](media/ui-delay-notification-in-vs.png)

알림은 ui 지연 (즉, UI에서 응답 하지 않음)이 확장의 코드 결과일 수 있음을 사용자에 게 알립니다. 또한 확장을 사용 하지 않도록 설정 하는 옵션을 사용자에 게 제공 합니다.

이 문서에서는 확장 코드에서 UI 지연 알림을 발생 시키는 원인을 진단 하는 방법을 설명 합니다.

> [!NOTE]
> Visual Studio 실험적 인스턴스를 사용 하 여 UI 지연을 진단 하지 마십시오. UI 지연 알림에 필요한 일부 호출 스택 분석 부분은 실험적 인스턴스를 사용할 때 해제 됩니다. 즉, UI 지연 알림이 표시 되지 않을 수 있습니다.

진단 프로세스에 대 한 개요는 다음과 같습니다.
1. 트리거 시나리오를 식별 합니다.
2. 작업 로깅을 사용 하 여 및를 다시 시작 합니다.
3. ETW 추적을 시작 합니다.
4. 알림이 다시 표시 되도록 트리거합니다.
5. ETW 추적을 중지 합니다.
6. 활동 로그를 검토 하 여 지연 ID를 가져옵니다.
7. 6 단계의 지연 ID를 사용 하 여 ETW 추적을 분석 합니다.

다음 섹션에서는 이러한 단계를 좀 더 자세히 살펴보겠습니다.

## <a name="identify-the-trigger-scenario"></a>트리거 시나리오 식별

UI 지연을 진단 하려면 먼저 작업 순서를 식별 하 여 Visual Studio에서 알림을 표시 해야 합니다. 이는 나중에 로깅이 설정 된 상태에서 알림을 트리거할 수 있도록 하기 위한 것입니다.

## <a name="restart-vs-with-activity-logging-on"></a>작업 로깅 사용 및 다시 시작

Visual Studio는 문제를 디버그할 때 유용한 정보를 제공 하는 "활동 로그"를 생성할 수 있습니다. Visual Studio에서 활동 로깅을 설정 하려면 명령줄 옵션을 사용 하 여 Visual Studio를 엽니다 `/log` . Visual Studio가 시작 되 면 활동 로그는 다음 위치에 저장 됩니다.

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

VS 인스턴스 ID를 찾는 방법에 대 한 자세한 내용은 [Visual Studio 인스턴스 검색 및 관리 도구](../install/tools-for-managing-visual-studio-instances.md)를 참조 하세요. 이 활동 로그는 나중에 UI 지연 및 관련 알림에 대 한 자세한 정보를 확인 하는 데 사용 됩니다.

## <a name="starting-etw-tracing"></a>ETW 추적 시작

[Perfview](https://github.com/Microsoft/perfview/) 를 사용 하 여 ETW 추적을 수집할 수 있습니다. PerfView는 ETW 추적을 수집 하 고 분석 하는 데 사용 하기 쉬운 인터페이스를 제공 합니다. 다음 명령을 사용 하 여 추적을 수집 합니다.

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

이를 통해 Visual Studio에서 UI 지연 알림과 관련 된 이벤트에 대해 사용 하는 "VisualStudio" 공급자를 사용할 수 있습니다. 또한 PerfView에서 **스레드 시간 스택** 뷰를 생성 하는 데 사용할 수 있는 커널 공급자에 대 한 키워드를 지정 합니다.

## <a name="trigger-the-notification-to-appear-again"></a>알림이 다시 표시 되도록 트리거합니다.

PerfView에서 추적 컬렉션을 시작한 후에는 1 단계의 트리거 작업 순서를 사용 하 여 알림이 다시 표시 될 수 있습니다. 알림이 표시 되 면 PerfView의 추적 수집을 중지 하 여 출력 추적 파일을 처리 하 고 생성할 수 있습니다.

## <a name="stop-etw-tracing"></a>ETW 추적 중지

추적 컬렉션을 중지 하려면 PerfView 창에서 **컬렉션 중지** 단추를 사용 하면 됩니다. 추적 컬렉션을 중지 한 후에는 PerfView에서 ETW 이벤트를 자동으로 처리 하 고 출력 추적 파일을 생성 합니다.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>활동 로그를 검사 하 여 지연 ID 가져오기

앞에서 설명한 대로 *%APPDATA%\Microsoft\VisualStudio \<vs_instance_id>\ActivityLog.xml*에서 활동 로그를 찾을 수 있습니다. Visual Studio는 확장 UI 지연을 감지할 때마다를 사용 하 여 활동 로그에 노드를 소스로 씁니다 `UIDelayNotifications` . 이 노드에는 UI 지연에 대 한 네 가지 정보가 포함 되어 있습니다.

- VS 세션에서 UI 지연을 고유 하 게 식별 하는 일련 번호 인 UI 지연 ID입니다.
- 시작부터 종료까지 Visual Studio 세션을 고유 하 게 식별 하는 세션 ID입니다.
- 알림이 UI 지연에 대해 표시 되었는지 여부
- UI 지연을 일으킬 수 있는 확장

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> 모든 UI 지연으로 인해 알림이 발생 하는 것은 아닙니다. 따라서 항상 **표시 되는 알림** 값을 확인 하 여 올바른 UI 지연을 정확 하 게 식별 해야 합니다.

활동 로그에서 올바른 UI 지연을 찾은 후 노드에 지정 된 UI 지연 ID를 기록 합니다. ID를 사용 하 여 다음 단계에서 해당 ETW 이벤트를 찾습니다.

## <a name="analyze-the-etw-trace"></a>ETW 추적 분석

다음으로 추적 파일을 엽니다. PerfView의 동일한 인스턴스를 사용 하거나 새 인스턴스를 시작 하 고 창의 왼쪽 위에 있는 현재 폴더 경로를 추적 파일의 위치로 설정 하 여이 작업을 수행할 수 있습니다.

![Perfview에서 폴더 경로 설정](media/perfview-set-path.png)

그런 다음 왼쪽 창에서 추적 파일을 선택 하 고 마우스 오른쪽 단추 클릭 또는 상황에 맞는 메뉴에서 **열기** 를 선택 하 여 엽니다.

> [!NOTE]
> 기본적으로 PerfView는 Zip 보관 파일을 출력 합니다. *trace.zip*열면 자동으로 보관 파일의 압축을 풀거나 추적이 열립니다. 추적 수집 중에 **Zip** 상자의 선택을 취소 하 여이를 건너뛸 수 있습니다. 그러나 다른 컴퓨터에서 추적을 전송 하 고 사용 하려는 경우에는 **Zip** 상자를 사용 하지 않는 것이 좋습니다. 이 옵션을 사용 하지 않으면 Ngen 어셈블리에 필요한 Pdb가 추적에 수반 되지 않으므로 Ngen 어셈블리의 기호가 대상 컴퓨터에서 확인 되지 않습니다. Ngen 어셈블리에 대 한 Pdb에 대 한 자세한 내용은 [이 블로그 게시물](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) 을 참조 하세요.

PerfView에서 추적을 처리 하 고 여는 데 몇 분 정도 걸릴 수 있습니다. 추적이 열리면 다양 한 "뷰" 목록이 표시 됩니다.

![PerfView 추적 요약 뷰](media/perfview-summary-view-events-selected.png)

먼저 **이벤트** 보기를 사용 하 여 UI 지연의 시간 범위를 가져옵니다.

1. **Events** `Events` 추적 아래에서 노드를 선택 하 고 마우스 오른쪽 단추 클릭 또는 상황에 맞는 메뉴에서 **열기** 를 선택 하 여 이벤트 보기를 엽니다.
2. `Microsoft-VisualStudio/ExtensionUIUnresponsiveness`왼쪽 창에서 ""를 선택 합니다.
3. Enter 키를 누릅니다.

선택 항목이 적용 되 고 모든 `ExtensionUIUnresponsiveness` 이벤트가 오른쪽 창에 표시 됩니다.

![이벤트 뷰에서 이벤트 선택](media/perfview-event-selection.png)

오른쪽 창의 각 행은 UI 지연에 해당 합니다. 이벤트에는 6 단계에서 활동 로그의 지연 ID와 일치 해야 하는 "지연 ID" 값이 포함 되어 있습니다. `ExtensionUIUnresponsiveness`는 ui 지연의 끝에서 발생 하므로 이벤트의 타임 스탬프 (대략적)는 ui 지연의 종료 시간을 표시 합니다. 이벤트에는 지연 기간도 포함 됩니다. 종료 타임 스탬프에서 지속 되는 기간을 빼서 UI 지연이 시작 된 시간의 타임 스탬프를 가져올 수 있습니다.

![UI 지연 시간 범위 계산](media/ui-delay-time-range.png)

예를 들어 이전 스크린샷에서 이벤트의 타임 스탬프는 12125.679이 고 지연 기간은 6143.085 (밀리초)입니다. 그러므로
* 지연 시작은 12125.679-6143.085 = 5982.594입니다.
* UI 지연 시간 범위는 5982.594에서 12125.679 까지입니다.

시간 범위가 있으면 **이벤트** 보기에서 종료 하 고 **스레드 시간 (startstop 활동 포함) 스택** 뷰를 열 수 있습니다. 이 보기는 UI 스레드를 차단 하는 확장이 다른 스레드나 i/o 바인딩된 작업 에서만 대기 하는 경우가 많기 때문에 특히 유용 합니다. 따라서 대부분의 경우에 대 한 이동 옵션인 **Cpu 스택** 보기는 해당 시간 동안 cpu를 사용 하지 않으므로 스레드가 차단에 소비한 시간을 캡처하지 못할 수 있습니다. **스레드 시간 스택은** 차단 된 시간을 적절히 표시 하 여이 문제를 해결 합니다.

![PerfView 요약 뷰의 스레드 시간 (StartStop 작업 포함) 스택 노드](media/perfview-thread-time-with-startstop-activities-stacks.png)

**스레드 시간 스택** 보기를 여는 동안 **devenv** 프로세스를 선택 하 여 분석을 시작 합니다.

![UI 지연 분석을 위한 스레드 시간 스택 보기](media/ui-delay-thread-time-stacks.png)

페이지 왼쪽 위의 **스레드 시간 스택** 뷰에서 시간 범위를 이전 단계에서 계산 된 값으로 설정 하 고 **enter** 키를 눌러 스택이 해당 시간 범위로 조정 되도록 할 수 있습니다.

> [!NOTE]
> Visual Studio가 이미 열려 있는 후에 추적 수집이 시작 되는 경우 UI (시작) 스레드가 직관적 수 있는 스레드를 결정 합니다. 그러나 UI (시작) 스레드의 스택에 있는 첫 번째 요소는 항상 운영 체제 Dll (*ntdll.dll* 및 *kernel32.dll*)이 되 고 그 다음에이와 야 `devenv!?` `msenv!?` 합니다. 이 시퀀스는 UI 스레드를 식별 하는 데 도움이 될 수 있습니다.

 ![시작 스레드 식별](media/ui-delay-startup-thread.png)

패키지의 모듈을 포함 하는 스택만 포함 하 여이 뷰를 추가로 필터링 할 수도 있습니다.

* 기본적으로 추가 된 모든 그룹화를 제거 하려면 **GroupPats** 를 빈 텍스트로 설정 합니다.
* 기존 프로세스 필터 외에도 어셈블리 이름의 일부를 포함 하도록 **IncPats** 를 설정 합니다. 이 경우에는 devenv 여야 합니다 **. UIDelayR2**.

![스레드 시간 스택 뷰에서 GroupPath 및 IncPath 설정](media/perfview-tts-group-path-inc-path.png)

PerfView에는 코드의 성능 병목 상태를 식별 하는 데 사용할 수 있는 **도움말** 메뉴 아래에 자세한 지침이 있습니다. 또한 다음 링크는 Visual Studio 스레딩 Api를 활용 하 여 코드를 최적화 하는 방법에 대 한 자세한 정보를 제공 합니다.

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

효율적인 확장 작성을 위한 모범 사례에 대 한 지침을 제공 하는 확장 ( [NuGet 패키지)](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)에 대 한 새로운 Visual Studio 정적 분석기를 사용할 수도 있습니다. [VS SDK 분석기](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) 및 [스레딩 분석기](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)의 목록을 참조 하세요.

> [!NOTE]
> 제어 권한이 없는 종속성으로 인 한 응답 중지를 해결할 수 없는 경우 (예: 확장이 UI 스레드에서 동기 VS 서비스를 호출 해야 하는 경우)이에 대해 알고 싶습니다. Visual Studio 파트너 프로그램의 멤버인 경우 개발자 지원 요청을 제출 하 여 문의할 수 있습니다. 그렇지 않으면 ' 문제 보고 ' 도구를 사용 하 여 피드백을 제출 하 고 `"Extension UI Delay Notifications"` 제목에를 포함 합니다. 분석에 대 한 자세한 설명도 포함 해 주세요.
