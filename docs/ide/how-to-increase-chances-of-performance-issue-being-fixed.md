---
title: 성능 문제가 해결될 가능성을 높이는 방법
description: Visual Studio에서 성능 문제 제출에 대한 추가 정보 및 모범 사례
author: madskristensen
ms.author: madsk
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: f5c83a145eb56dcb95c6e9a299c690ae960442c9
ms.sourcegitcommit: 4bcd6abb89feff1cf8251e3ded73fdc30b67e347
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81615037"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>성능 문제가 해결될 가능성을 높이는 방법

“[문제 보고](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)” 도구는 Visual Studio 사용자가 다양한 문제를 보고하는 데 널리 사용됩니다. Visual Studio 팀은 사용자 피드백에서 크래시 및 속도 저하 추세를 파악하고 광범위한 사용자에게 영향을 주는 문제를 해결합니다. 특정 피드백 티켓의 실행 가능성이 높을수록 제품 팀에서 진단하고 빠르게 해결할 가능성이 높습니다. 이 문서에서는 크래시 또는 속도 저하 문제를 보고하면서 모범 사례를 설명하여 모범 사례가 더 많이 실행될 수 있도록 합니다.

## <a name="general-best-practices"></a>일반적인 유용한 정보

Visual Studio는 수많은 언어, 프로젝트 형식, 플랫폼 등을 지원하는 크고 복잡한 플랫폼입니다. 구성 요소가 설치되고 세션에서 활성화되는 방법, 설치된 확장, Visual Studio 설정, 머신 구성, 편집되는 코드의 모양에 대한 기능이 있습니다. 변수 수를 고려할 때, 가시적인 증상이 동일하더라도 한 사용자의 문제 보고서에 다른 사용자의 문제 보고서와 동일한 기본 문제가 있는지 여부를 확인하기는 어렵습니다. 이러한 점을 고려했을 때, 특정 문제 보고서가 진단될 가능성이 높음을 확인하기 위한 몇 가지 모범 사례는 다음과 같습니다.

**가능한 구체적인 제목 제공**

보고되는 문제에 대한 고유한 시그니처를 찾고 제목에 가능한 한 많이 포함합니다. 제목이 설명적인 경우 관련 없는 문제(그러나 표면적으로 동일한 증상)가 있는 사용자가 티켓에 투표하거나 주석을 달 가능성이 작으므로, ‘사용자의’ 문제를 진단하기가 더 어려워집니다. 

**불확실한 경우, 새 문제 보고서 로그**

많은 문제에 재현할 고유한 시그니처나 단계가 없을 수 있습니다. 그러한 경우, 비슷한 표면상의 ‘증상’을 보고하는 다른 보고서에 대한 찬성이나 주석보다 새 보고서가 좋습니다.  보고서의 유형에 따라, 이 문서의 뒷부분에 설명된 대로 보고서에 추가 진단 파일을 포함합니다.

**문제별 모범 사례**

적절한 진단 파일 없이 진단하기 어려운 문제는 아래에 설명되어 있습니다. 문제를 가장 잘 설명하는 사례를 확인한 후 해당 사례에 대한 피드백 단계를 수행합니다.

-   [크래시:](#crashes) 프로세스(Visual Studio)가 예기치 않게 종료되면 크래시가 발생합니다.

-   [무응답:](#unresponsiveness) VS가 오랫동안 응답하지 않게 됩니다.

-   [속도 저하 문제:](#slowness-and-high-cpu-issues) VS의 특정 작업이 원하는 속도보다 느림

-   [높은 CPU:](#slowness-and-high-cpu-issues) 오랫동안 예기치 않게 높은 CPU 사용량

-   [Out-Of-Process 문제:](#out-of-process-issues) Visual Studio 위성 프로세스에서 발생한 문제

## <a name="crashes"></a>크래시
프로세스(Visual Studio)가 예기치 않게 종료되면 크래시가 발생합니다.

**직접 재현 가능한 크래시**

직접 재현 가능한 크래시는 모두 다음과 같은 특징이 있는 경우입니다.

- 알려진 일련의 단계를 수행하여 관찰 가능

- 여러 컴퓨터에서 관찰 가능(사용 가능한 경우)

- 피드백의 일부로 제공하거나 연결할 수 있는 프로젝트 또는 샘플 코드에서 재현 가능(단계가 프로젝트 또는 문서 열기와 관련된 경우)

이러한 문제에 대해서는 “[문제를 보고하는 방법](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)”의 단계를 수행하고 다음을 포함하세요.

-   문제 재현 단계

-   위에서 설명한 독립 실행형 재현 프로젝트. 독립 실행형 재현이 불가능한 경우 다음을 포함하세요.

    -   열려 있는 프로젝트의 언어(C\#, C++, 등)

    -   프로젝트 종류(콘솔 애플리케이션, ASP.NET 등)


> [!NOTE]
> **가장 중요한 피드백:** 이 경우, 가장 중요한 피드백은 샘플 소스 코드와 함께 문제를 재현하는 일련의 단계입니다.

**알 수 없는 크래시**

크래시의 원인이 무엇인지 확실하지 않거나 크래시가 임의로 발생하는 것 같은 경우, Visual Studio 크래시마다 로컬에서 덤프를 캡처하고 별도의 피드백 항목에 첨부할 수 있습니다. Visual Studio에서 크래시가 발생할 때 로컬에서 덤프를 저장하려면 관리자 명령 창에서 다음 명령을 실행합니다.

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

덤프 수와 덤프 폴더를 적절하게 사용자 지정합니다. 이러한 설정에 대한 자세한 내용은 [여기](/windows/win32/wer/collecting-user-mode-dumps)를 참조하세요.

> [!NOTE]
> 작업 관리자를 사용하여 캡처한 덤프는 잘못된 비트가 될 가능성이 높기 때문에 사용 가능성이 줄어듭니다. 위에서 설명한 프로시저는 힙 덤프를 캡처하는 데 선호되는 방법입니다. 작업 관리자를 사용하려면 현재 실행 중인 작업을 닫고 32비트 작업 관리자(%windir%\\syswow64\\taskmgr.exe)를 시작하고 거기에서 힙 덤프를 수집합니다.

> [!NOTE] 
> 이 메서드에 의해 생성되는 각 덤프 파일의 크기는 최대 4GB입니다. DumpFolder를 드라이브 공간이 충분한 위치로 설정하거나 DumpCount를 적절하게 조정합니다.

Visual Studio에서 크래시가 발생할 때마다 구성된 위치에 덤프 파일 **devenv.exe.[number].dmp**가 만들어집니다.

그런 다음, Visual Studio의 “문제 보고...” 기능을 사용합니다. 그러면 적절한 덤프를 첨부할 수 있습니다.

1.  보고 중인 크래시에 대한 덤프 파일을 찾습니다(생성 시간이 올바른 파일 찾기).

2.  가능한 경우, 피드백을 제출하기 전에 파일을 압축(\*.zip)하여 크기를 줄입니다.

3.  “[문제를 보고하는 방법](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)”의 단계를 수행하고 힙 덤프를 새 피드백 항목에 첨부합니다.

> [!NOTE] 
> **가장 중요한 피드백:** 이 경우 가장 중요한 피드백은 크래시 발생 시 캡처된 힙 덤프입니다.

## <a name="unresponsiveness"></a>무응답
VS가 오랫동안 응답하지 않게 됩니다.

**직접 재현 가능한 무응답**

크래시에 대한 해당 섹션에 설명된 것처럼, 여러 머신에서 확인되고 작은 샘플에서 시연할 수 있는 쉽게 재현할 수 있는 문제의 경우, 가장 중요한 피드백 보고서는 문제 재현 단계가 포함되고 문제를 시연하는 샘플 소스 코드가 포함된 보고서입니다.

**알 수 없는 무응답**

무응답이 예측할 수 없는 방식으로 나타나는 경우, 다음번에 Visual Studio의 새 인스턴스를 시작하고 해당 인스턴스에서 문제를 보고합니다.
[“레코드” 화면](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)에서 응답하지 않는 Visual Studio 세션을 선택해야 합니다.

응답하지 않는 Visual Studio 인스턴스가 관리자 모드에서 시작된 경우, 두 번째 인스턴스도 관리자 모드에서 시작되어야 합니다.

>[!NOTE] 
> **가장 중요한 피드백:** 이 경우 가장 중요한 피드백은 무응답 발생 시 캡처된 힙 덤프입니다.

## <a name="slowness-and-high-cpu-issues"></a>속도 저하 및 높은 CPU 문제

느린 작업 또는 높은 CPU 이벤트가 진행되는 동안 캡처한 성능 추적으로 속도 저하 또는 높은 CPU 사용량 문제를 해결할 수 있습니다.

>[!NOTE] 
> 가능하면 각 시나리오를 별도의 특정 피드백 보고서에 구분합니다.
예를 들어 입력과 탐색이 모두 느려지는 경우 문제마다 아래 단계를 한 번씩 수행합니다. 이를 통해 제품 팀은 특정 문제의 원인을 구분할 수 있습니다.

성능 캡처에서 최상의 결과를 위해 다음 단계를 수행합니다.

1.  아직 실행 중이 아닌 경우 문제를 재현할 Visual Studio 복사본을 엽니다.

    -   모든 기능을 설정하여 문제를 재현합니다. 예를 들어 특정 파일을 연 상태에서 특정 프로젝트를 로드해야 하는 경우 계속하기 전에 두 단계가 모두 완료되어야 합니다.

    -   솔루션 로드와 관련된 문제를 보고하지 ‘않는’ 경우, 솔루션을 연 후 5~10분(또는 솔루션 크기에 따라 더 많이) 정도 기다렸다가 성능 추적을 기록합니다.  솔루션 로드 프로세스는 많은 양의 데이터를 생성하므로, 몇 분 동안 기다리면 보고하는 특정 문제에 초점을 맞출 수 있습니다.

2.  ‘솔루션이 열리지 않은’ 두 번째 Visual Studio의 복사본 시작 

3.  Visual Studio의 새 복사본에서 **문제 보고** 도구를 엽니다.

4.  “추적 및 힙 덤프 제공(선택 사항)” 단계에 도달할 때까지 [문제를 보고하는 방법](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)의 단계를 수행합니다.

5.  Visual Studio의 첫 번째 복사본(성능 문제가 발생한 복사본)을 기록하도록 선택하고 기록을 시작합니다.

    -   단계 레코더 애플리케이션이 표시되고 기록을 시작합니다.

    -   **기록하는 동안**, Visual Studio의 첫 번째 복사본에서 문제가 있는 작업을 수행합니다. 기록된 시간 내에 표시되지 않는 경우 특정 성능 문제를 해결하기 어렵습니다.

    -   작업이 30초보다 짧고 쉽게 반복할 수 있는 경우, 문제를 더 보여 주도록 작업을 반복합니다.

    -   대부분의 경우, 특히 문제가 있는 작업이 30초 이상 지속되거나 반복되는 경우 문제를 보여 주는 데 60초 동안의 추적이면 충분합니다. 해결하려는 동작을 캡처하는 데 필요한 만큼 기간을 수정할 수 있습니다.

6.  보고하려는 느린 작업 또는 높은 CPU 이벤트가 완료되는 즉시 단계 레코더에서 “기록 중지”를 클릭합니다. 성능 추적을 처리하는 데 몇 분 정도 걸릴 수 있습니다.

7.  완료되면 몇 가지 파일이 피드백에 첨부됩니다. 문제를 재현하는 데 도움이 될 수 있는 추가 파일(샘플 프로젝트, 스크린샷, 동영상 등)을 첨부합니다.

8.  피드백을 제출합니다.

성능 추적을 기록하는 동안 보고하는 느린 작업 또는 높은 CPU가 종료되면 즉시 기록을 중지합니다. 너무 많은 정보가 수집되면 가장 오래된 정보를 덮어쓰게 됩니다. 흥미로운 작업 후 바로(몇 초 내에) 추적을 중지하지 않으면 유용한 추적 데이터를 덮어쓰게 됩니다.

Developer Community 웹 사이트의 기존 피드백 항목에 성능 추적을 바로 첨부하지 마세요. 추가 정보 요청/제공은 Visual Studio의 기본 제공 문제 보고 도구에서 지원되는 워크플로입니다. 이전 피드백 항목을 해결하기 위해 성능 추적이 필요한 경우 피드백 항목의 상태를 “추가 정보 필요”로 설정하여 새 문제를 보고하는 것과 같은 방식으로 응답할 수 있습니다. 자세한 지침은 문제 보고 도구 문서의 [“추가 정보 필요” 섹션](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info)을 참조하세요.

> [!NOTE] 
> **가장 중요한 피드백:** 거의 모든 속도 저하/높은 CPU 문제의 경우, 가장 중요한 피드백은 해당 시간 동안 동작을 캡처하는 성능 추적(\*.etl.zip)과 함께 수행하려고 했던 작업에 대한 개략적인 설명입니다.

**고급 성능 추적**

문제 보고 도구의 추적 컬렉션 기능은 대부분의 시나리오에서 충분합니다. 그러나 추적 컬렉션에 대해 더 많은 제어가 필요한 경우가 있습니다(예: 버퍼 크기가 큰 추적). 이 경우에는 PerfView를 사용하는 것이 좋습니다. PerfView 도구를 사용하여 성능 추적을 수동으로 기록하는 단계는 [Recording performance traces with PerfView](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView)(PerfView를 사용하여 성능 추적 기록) 페이지에서 확인할 수 있습니다.

## <a name="out-of-process-issues"></a>Out-Of-Process 문제

> [!NOTE]
> Visual Studio 2019 버전 16.3부터 out-of-process 로그가 문제 보고 도구를 사용하여 제출되는 피드백에 자동으로 첨부됩니다. 그러나 문제를 직접 재현할 수 있는 경우 아래 단계에 따라 문제를 진단하는 데 도움이 되는 추가 정보를 제공할 수 있습니다.

Visual Studio와 병렬로 실행되며 기본 Visual Studio 프로세스 외부에서 다양한 기능을 제공 하는 여러 위성 프로세스가 있습니다. 이러한 위성 프로세스 중 하나에서 오류가 발생하는 경우 일반적으로 Visual Studio 쪽에서 'StreamJsonRpc.RemoteInvocationException' 또는 'StreamJsonRpc.ConnectionLostException'로 표시됩니다.

이러한 유형의 문제는 다음 단계를 수행하여 수집할 수 있는 추가 로그를 제공하면 최대한 조치가 가능할 수 있습니다.

1.  직접 재현할 수 있는 문제인 경우 **% temp%/servicehub/logs** 폴더를 삭제하는 것으로 시작합니다. 이 문제를 재현할 수 없는 경우 이 폴더를 그대로 유지하고 다음 글머리 기호는 무시하세요.

    -   전역 환경 변수 **ServiceHubTraceLevel**을 **All**로 설정합니다.
    -   문제를 재현합니다.

2.  [여기](https://www.microsoft.com/download/details.aspx?id=12493)에서 Microsoft Visual Studio 및 .NET Framework 로그 수집 도구를 다운로드하고 실행합니다.
3.  도구를 실행합니다. 그러면 **%temp%/vslogs.zip** 파일이 출력됩니다. 피드백에 해당 파일을 첨부하세요.

## <a name="see-also"></a>참조

* [Visual Studio 피드백 옵션](../ide/feedback-options.md)
* [Mac용 Visual Studio의 문제 보고](/visualstudio/mac/report-a-problem)
* [C++를 사용하여 문제 보고](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio 개발자 커뮤니티](https://developercommunity.visualstudio.com/)
* [개발자 커뮤니티 데이터 개인 정보](developer-community-privacy.md)
