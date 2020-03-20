---
title: 디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행 | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 273dc6770f2928ed65d6a473b7f1986bc353687e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999410"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행

Visual Studio는 성능 측정 및 프로파일링 도구 중에서 선택할 수 있습니다. **CPU 사용량** 및 **메모리 사용량**과 같은 일부 도구는 디버거를 사용하거나 사용하지 않고 릴리스 또는 디버그 빌드 구성으로 실행할 수 있습니다. **애플리케이션 타임라인**과 같은 **성능 프로파일러** 도구는 디버그 또는 릴리스 빌드에서 실행할 수 있습니다. **진단 도구** 창 및 **이벤트** 탭과 같은 디버거 통합 도구는 디버깅 세션 중에만 실행됩니다.

>[!NOTE]
>Windows 7 이상에서 비-디버거 성능 도구를 사용할 수 있습니다. 디버거 통합 프로파일링 도구를 실행하려면 Windows 8 이상이 필요합니다.

비-디버거 **성능 프로파일러** 및 디버거 통합 **진단 도구**는 다양한 환경과 정보를 제공합니다. 디버거 통합 도구는 중단점과 변수 값을 표시합니다. 비-디버거 도구를 사용하면 최종 사용자 환경에 더 가까운 결과를 얻을 수 있습니다.

사용할 도구 및 결과를 결정하려면 다음 사항을 고려하세요.

- 파일 I/O 또는 네트워크 응답 문제와 같은 외부 성능 문제는 디버거 또는 비-디버거 도구에서는 크게 다르지 않습니다.
- CPU 집중 호출로 의해 발생하는 문제의 경우 릴리스 빌드와 디버그 빌드 간에 상당한 성능 차이가 있을 수 있습니다. 릴리스 빌드에 문제가 있는지 확인합니다.
- 디버그 빌드 중에만 문제가 발생하면 비-디버거 도구를 실행할 필요가 없을 것입니다. 릴리스 빌드 문제의 경우 디버거 도구가 추가 조사에 도움이 되는지 여부를 결정합니다.
- 릴리스 빌드는 함수 호출 및 상수 인라인, 사용되지 않는 코드 경로 정리 및 디버거가 사용할 수 없는 방식으로 변수 저장과 같은 최적화를 제공합니다. 디버거 통합 도구의 성능 번호는 덜 정확합니다. 디버그 빌드에는 이러한 최적화가 부족하기 때문입니다.
- 디버거 자체는 예외 및 모듈 로드 이벤트 가로채기와 같은 필요한 디버거 작업을 수행하므로 성능 시간을 변경합니다.
- **성능 프로파일러** 도구의 릴리스 빌드 성능 번호가 가장 정밀하고 정확합니다. 디버거 통합 도구 결과는 다른 디버깅 관련 측정과 비교할 때 가장 유용합니다.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> 디버깅하는 동안 프로파일링 데이터 수집

**디버깅** > **디버깅 시작** 또는 **F5**를 눌러 Visual Studio에서 디버깅을 시작하면 기본적으로 **진단 도구** 창이 나타납니다. 수동으로 열려면 **디버그** > **Windows** > **진단 도구 표시**를 선택합니다. **진단 도구**에는 이벤트, 프로세스 메모리 및 CPU 사용량에 대한 정보가 표시됩니다.

![진단 도구](../profiling/media/diagnostictools-update1.png "진단 도구")

- 도구 모음의 **설정** 아이콘을 사용하여 **메모리 사용량**, **UI 분석** 및 **CPU 사용량**을 볼지 여부를 선택합니다.

- **설정** 드롭다운에서 **설정**을 선택하여 추가 옵션으로 **진단 도구 속성 페이지**를 엽니다.

- Visual Studio Enterprise를 실행 중인 경우 Visual Studio **도구** > **옵션** > **IntelliTrace**에서 IntelliTrace를 사용하거나 사용하지 않도록 설정할 수 있습니다.

디버그를 중지하면 진단 세션이 종료됩니다.

원격 디버깅 대상에 대한 **진단 도구**도 볼 수 있습니다. 원격 디버깅 및 프로파일링의 경우 Visual Studio 원격 디버거가 원격 대상에 설치되어 실행 중이어야 합니다.
- 원격 디버깅 및 데스크톱 앱 프로젝트 프로파일링의 경우 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.
- 원격 디버깅 및 UWP 앱 프로파일링의 경우 [원격 머신에서 UWP 앱 디버그](../debugger/run-windows-store-apps-on-a-remote-machine.md)를 참조하세요.

### <a name="the-events-tab"></a>이벤트 탭

디버깅 세션 중에 **진단 도구** 창의 **이벤트** 탭에 발생하는 진단 이벤트가 나열됩니다. 범주 접두사: **중단점**, **파일** 및 기타 항목을 사용하면 범주에 대한 목록을 빠르게 검사하거나 관심 없는 범주를 건너뛸 수 있습니다.

**필터** 드롭다운을 사용하여 특정 범주의 이벤트를 선택하거나 취소하여 보기 안팎으로 이벤트를 필터링합니다.

![진단 이벤트 필터](../profiling/media/diagnosticeventfilter.png "진단 이벤트 필터")

검색 상자를 사용하여 이벤트 목록에서 특정 문자열을 찾습니다. 다음은 네 개의 이벤트와 일치하는 "이름" 문자열에 대한 검색 결과입니다.

![진단 이벤트 검색](../profiling/media/diagnosticseventsearch.png "진단 이벤트 검색")

자세한 내용은 [진단 도구 창의 이벤트 탭 검색 및 필터링](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)을 참조하세요.

## <a name="collect-profiling-data-without-debugging"></a>디버깅을 사용하지 않고 프로파일링 데이터 수집

디버깅하지 않고 성능 데이터를 수집하려면 **성능 프로파일러** 도구를 실행할 수 있습니다. 프로파일링 도구 중 일부를 실행하려면 관리자 권한이 필요합니다. 관리자 권한으로 Visual Studio를 열거나 진단 세션을 시작할 때 관리자 권한으로 실행할 수 있습니다.

1. Visual Studio에서 프로젝트를 연 상태에서 **디버깅** > **성능 프로파일러**를 선택하거나 **Alt**+**F2**를 누릅니다.

1. 진단 시작 페이지에서 실행할 하나 이상의 도구를 선택합니다. 프로젝트 형식, 운영 체제 및 프로그래밍 언어에 적용되는 도구만 표시됩니다. **모든 도구 표시**를 선택하여 이 진단 세션에 사용할 수 없는 도구도 확인하세요. C# UWP 앱의 경우 선택이 다음과 같이 표시될 수 있습니다.

   ![진단 도구 선택](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. 진단 세션을 시작하려면 **시작**을 선택합니다.

   세션이 실행되는 동안 일부 도구는 진단 도구 페이지에 실시간 데이터의 그래프를 표시합니다.

    ![성능 및 진단 허브에서 데이터 수집](../profiling/media/pdhub_collectdata.png "허브 데이터 수집")

1. 진단 세션을 종료하려면 **컬렉션 중지**를 선택합니다.

   분석된 데이터가 **보고서** 페이지에 표시됩니다.

보고서를 저장하고 진단 도구 시작 페이지의 **최근 열린 세션** 목록에서 열 수 있습니다.

![저장된 진단 세션 파일 열기](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>프로파일링 보고서
 ![진단 도구 보고서](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![1단계](../profiling/media/procguid_1.png "ProcGuid_1")|타임라인에는 프로파일링 세션 길이, 응용 프로그램 수명 주기 시작 이벤트 및 사용자 표시가 표시됩니다.|
|![2단계](../profiling/media/procguid_2.png "ProcGuid_2")|파란색 막대를 끌어 타임라인의 부분의 선택하여 보고서를 타임라인의 일부분으로 제한할 수 있습니다.|
|![3단계](../profiling/media/procguid_3.png "ProcGuid_3")|각 진단 도구는 하나 이상의 마스터 그래프를 표시합니다. 진단 세션에 둘 이상의 도구가 있는 경우 모든 해당 마스터 그래프가 표시됩니다.|
|![4단계](../profiling/media/procguid_4.png "ProcGuid_4")|각 도구의 개별 그래프를 축소 또는 확장할 수 있습니다.|
|![5단계](../profiling/media/procguid_6.png "ProcGuid_6")|데이터에 둘 이상의 도구가 포함된 경우 도구 세부 정보가 탭 아래에 수집됩니다.|
|![6단계](../profiling/media/procguid_6a.png "ProcGuid_6a")|보고서의 아래쪽 절반에는 각 도구에 대한 하나 이상의 세부 정보 보기가 표시됩니다. 타임라인의 영역을 선택하여 보기를 필터링할 수 있습니다.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>설치되거나 실행 중인 앱에서 진단 세션 실행

 Visual Studio 프로젝트에서 앱을 시작할 수 있는 것 외에, 다른 대상에서 진단 세션을 실행할 수도 있습니다. 예를 들어 Windows App Store에서 설치된 앱의 성능 문제를 진단할 수 있습니다.

 ![진단 도구 분석 대상 선택](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

 이미 설치된 앱을 시작하거나 이미 실행 중인 앱 및 프로세스에 진단 도구를 연결할 수 있습니다. **실행 중인 앱** 또는 **설치된 앱**을 선택하면 지정된 배포 대상에 앱을 찾는 목록에서 앱을 선택합니다. 이 대상은 로컬 또는 원격 머신일 수 있습니다.

 ![진단을 위해 실행 중이거나 설치된 앱 선택](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

## <a name="see-also"></a>참조

다음은 진단 개발팀의 블로그 게시물 및 MSDN 문서입니다.
- [MSDN Magazine: Visual Studio 2015에서 디버그하는 동안 성능 분석](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [MSDN Magazine: IntelliTrace를 사용하여 문제를 더 빠르게 진단](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [블로그 게시물: Visual Studio 2015의 메모리 사용량 도구로 이벤트 처리기 누수 진단](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)

- [비디오: Microsoft Visual Studio Ultimate 2015의 IntelliTrace를 사용하여 기록 디버그](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)

- [비디오: Visual Studio 2015를 사용하여 성능 문제 디버그](https://channel9.msdn.com/Events/Build/2015/3-731)

- [PerfTips: Visual Studio에서 디버깅 중에 성능 정보 한눈에 확인](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

- [Visual Studio 2015의 진단 도구 디버거 창](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [Visual Studio Enterprise 2015의 IntelliTrace](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
