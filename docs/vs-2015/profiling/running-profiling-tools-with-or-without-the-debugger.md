---
title: 디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fb07e9bc6c308e27e3ad054c5aeb0b12c092054
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534006"
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서는 이제 성능 도구를 선택할 수 있습니다. 그 중 일부(예: **CPU 사용** 및 **메모리 사용**)는 디버거를 사용하거나 사용하지 않고 실행될 수 있습니다. 디버거가 없는 성능 도구는 릴리스 구성에서 실행될 수 있으며, 디버거 통합 도구는 디버그 구성에서 실행될 수 있습니다.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>디버거를 사용하여 도구를 실행할지 여부 선택  
 디버거 통합 성능 도구에서는 디버거가 없는 도구로 수행할 수 없는 중단점 설정, 변수 값 검사 등의 많은 작업을 수행할 수 있습니다. 디버거가 없는 도구는 릴리스된 애플리케이션의 사용자가 볼 수 있는 것에 가까운 환경을 제공합니다.  
  
 목적에 적합한 도구의 종류를 결정하는 데 도움이 될 수 있는 몇 가지 질문은 다음과 같습니다.  
  
1. 애플리케이션이 개발되는 동안 문제가 발견되었나요? 아니면 릴리스 버전에서 문제가 발견되었나요?  
  
     처리하고 있는 문제가 개발 중에 발견된 경우 릴리스 빌드에서 성능 도구를 실행할 필요가 없을 수도 있습니다. 문제가 릴리스 버전에서 발견된 경우 릴리스 구성에서 문제를 재현한 다음 디버거가 추가 조사에 도움이 될지 여부를 결정해야 합니다.  
  
2. 문제가 CPU를 많이 사용하는 처리 때문에 발생하나요?  
  
     많은 문제의 원인이 파일 I/O 또는 네트워크 응답 성능과 같은 외부 성능 문제이므로 디버거를 사용하거나 사용하지 않고 성능 도구를 실행하는지 여부는 큰 차이를 발생시키지 않습니다. 문제의 원인이 CPU를 많이 사용하는 호출인 경우 릴리스 구성과 디버그 구성 간의 차이는 상당할 수 있으며 디버거 통합 도구를 사용하기 전에 릴리스 빌드에 문제가 있는지 확인해야 할 수 있습니다.  
  
3. 성능을 정확히 측정해야 하나요, 아니면 대략적인 수치라도 괜찮은가요?  
  
     디버그 빌드에는 릴리스 빌드에서 제공하는 함수 호출 및 상수 인라인 처리, 사용되지 않는 코드 경로 정리 및 디버거가 사용할 수 없는 방식으로 변수 저장과 같은 특정 최적화가 없습니다. 디버거 자체가 디버깅에 필요한 특정 작업(예: 예외 및 모듈 로드 이벤트 가로채기)을 수행하기 때문에 성능 시간을 변경합니다. 따라서 디버거 통합 도구의 성능 수치는 수십 밀리초 범위까지만 정확합니다. 디버거가 없는 도구를 사용한 릴리스 구성의 성능 수치는 훨씬 더 정확합니다.  
  
## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> 디버깅하는 동안 프로파일링 데이터 수집  
 다음 섹션에서는 로컬 디버그에 대해 설명합니다. 디바이스에서의 디버그 또는 원격 디버그에 대해서는 뒤의 섹션에서 확인할 수 있습니다.  
  
1. 디버그할 프로젝트를 연 다음 **디버그 / 디버깅 시작** 을 클릭합니다(또는 도구 모음에서 **시작** 을 클릭하거나 **F5**사용).  
  
2. 끄지 않았다면 **진단 도구** 가 자동으로 나타납니다. 창을 다시 표시하려면 **디버그/Windows/진단 도구 표시**를 클릭합니다.  
  
3. 데이터를 수집할 시나리오를 실행합니다.  
  
    세션을 실행하는 동안 이벤트, 프로세스 메모리 및 CPU 사용률에 대한 정보를 볼 수 있습니다.  
  
    다음 그림은 Visual Studio 2015 업데이트 1의 **진단 도구** 창을 보여 줍니다.  
  
    ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
4. 도구 모음의 **도구 선택** 설정을 사용하여 **메모리 사용** 또는 **CPU 사용** 중 하나를 표시하거나 둘 다 표시하도록 선택할 수 있습니다. Visual Studio Enterprise를 실행 중인 경우 **도구/옵션/IntelliTrace**에서 IntelliTrace를 사용하거나 사용하지 않도록 설정할 수 있습니다.  
  
5. 디버그를 중지하면 진단 세션이 종료됩니다.  
  
   Visual Studio 2015 업데이트 1에서 **진단 도구** 창을 사용하면 관심 있는 이벤트에 보다 쉽게 집중할 수 있습니다.   이제 이벤트 이름이 범주 접두사 (**제스처**, **프로그램 출력**, **중단점**, **파일** 등)와 함께 표시 되므로 지정 된 범주에 대 한 목록을 빠르게 검색 하거나 관심 없는 범주를 건너뛸 수 있습니다.  
  
   이제 이벤트 목록의 모든 위치에서 특정 문자열을 찾을 수 있도록 창에 검색 상자가 있습니다. 예를 들어 다음 그림에서는 4개의 이벤트와 일치한 "설치" 문자열에 대한 검색 결과를 보여 줍니다.  
  
   ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
   창에서 보기 내부 및 외부 이벤트를 필터링할 수도 있습니다. **필터** 드롭다운에서 특정 이벤트 범주를 선택하거나 선택 취소할 수 있습니다. 범주 이름은 접두사 이름과 동일합니다.  
  
   ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
   자세한 내용은 [진단 도구 창의 이벤트 탭 검색 및 필터링](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)을 참조하세요.  
  
## <a name="collect-profiling-data-without-debugging"></a>디버깅을 사용하지 않고 프로파일링 데이터 수집  
 일부 프로파일링 도구를 실행하려면 관리자 권한이 필요합니다. 관리자 권한으로 Visual Studio를 시작할 수도 있고, 진단 세션을 시작할 때 관리자 권한으로 도구를 실행하도록 선택할 수 있습니다.  
  
1. Visual Studio에서 프로젝트를 엽니다.  
  
2. **디버그** 메뉴에서 **성능 프로파일러** ... (바로 가기 키: Alt + F2)를 선택 합니다.  
  
3. 진단 시작 페이지에서, 세션에서 실행할 하나 이상의 도구를 선택합니다. 프로젝트 형식, 운영 체제 및 프로그래밍 언어에 적용되는 도구만 표시됩니다. 진단 도구를 선택하면 같은 진단 세션에서 실행할 수 없는 도구 선택을 사용할 수 없게 설정됩니다. C# Windows 유니버설 앱의 경우 선택 항목이 다음과 같이 표시될 수 있습니다.  
  
    ![진단 도구 선택](../profiling/media/diag-selecttool.png "DIAG_SelectTool")  
  
4. 진단 세션을 시작하려면 **시작**을 클릭합니다.  
  
5. 데이터를 수집할 시나리오를 실행합니다.  
  
    세션을 실행하는 동안 일부 도구는 진단 도구 시작 페이지에 실시간 데이터의 그래프를 표시합니다.  
  
    ![성능 및 진단 페이지에서 데이터를 수집합니다.](../profiling/media/pdhub-collectdata.png "PDHUB_CollectData")  
  
6. 진단 세션을 종료하려면 **컬렉션 중지**를 클릭합니다.  
  
   진단 세션에서 데이터 수집을 중지하면 데이터가 분석되고 보고서가 진단 페이지에 표시됩니다.  
  
   진단 도구 시작 페이지의 최근에 열어 본 목록에서 저장된 진단 세션 파일을 열 수도 있습니다.  
  
   ![저장된 진단 세션 파일 열기](../profiling/media/pdhub-openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>프로파일링 보고서  
 ![진단 도구 보고서](../profiling/media/diag-report.png "DIAG_Report")  
  
|이미지|설명|  
|-|-|  
|![1단계](../profiling/media/procguid-1.png "ProcGuid_1")|타임라인에는 프로파일링 세션 길이, 응용 프로그램 수명 주기 시작 이벤트 및 사용자 표시가 표시됩니다.|  
|![2단계](../profiling/media/procguid-2.png "ProcGuid_2")|파란색 막대를 끌어 타임라인의 부분의 선택하여 보고서를 타임라인의 일부분으로 제한할 수 있습니다.|  
|![3단계](../profiling/media/procguid-3.png "ProcGuid_3")|도구는 하나 이상의 마스터 그래프를 표시합니다. 진단 세션이 여러 가지 도구로 만들어질 경우 모든 마스터 그래프가 표시됩니다.|  
|![4단계](../profiling/media/procguid-4.png "ProcGuid_4")|개별 그래프를 축소 또는 확장할 수 있습니다.|  
|![5단계](../profiling/media/procguid-6.png "ProcGuid_6")|데이터에 여러 도구의 정보가 포함되어 있으면 도구에 대한 세부 정보는 탭 아래에 수집됩니다.|  
|![6단계](../profiling/media/procguid-6a.png "ProcGuid_6a")|도구에는 세부 정보 뷰가 하나 이상 있을 수 있습니다. 뷰는 타임라인의 선택된 부분으로 필터링됩니다.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>다른 디바이스로 분석 대상 설정  
 Visual Studio 프로젝트에서 앱을 시작할 수 있는 것 외에, 다른 대상에서 진단 세션을 실행할 수도 있습니다. 예를 들어 Windows 앱 스토어에서 설치된 앱 버전의 성능 문제를 진단할 수 있습니다.  
  
 ![진단 도구 분석 대상 선택](../profiling/media/pdhub-chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 디바이스에 이미 설치된 앱을 시작하거나 이미 실행 중인 일부 앱에 진단 도구를 연결할 수 있습니다. **실행 중인 응용 프로그램** 또는 **설치된 응용 프로그램**을 선택하면 지정된 배포 대상에서 앱을 검색하는 목록에서 앱을 선택하는 것입니다.  
  
 ![진단을 위해 실행 중이거나 설치된 앱 선택](../profiling/media/pdhub-selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 **Internet Explorer**를 선택하면 URL을 지정하고 휴대폰 배포 대상을 변경할 수 있습니다.  
  
 ![Internet Explorer에 표시할 URL을 지정합니다.](../profiling/media/pdhub-choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Remote Debugging  
 원격 PC 또는 태블릿에서 진단 세션을 실행하려면 원격 대상에 Visual Studio 원격 도구가 설치되어 있고 실행 중이어야 합니다. 데스크톱 앱의 경우 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.  Windows 유니버설 앱의 경우 [원격 컴퓨터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조하세요.  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>진단 개발팀의 블로그 게시물 및 MSDN 문서  
 [MSDN Magazine: Visual Studio 2015에서 디버그하는 동안 성능 분석](https://msdn.microsoft.com/magazine/dn973013.aspx)  
  
 [MSDN Magazine: IntelliTrace를 사용하여 문제를 더 빠르게 진단](https://msdn.microsoft.com/magazine/dn973014.aspx)  
  
 [블로그 게시물: Visual Studio 2015의 메모리 사용량 도구로 이벤트 처리기 누수 진단](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)  
  
 [비디오: Microsoft Visual Studio Ultimate 2015의 IntelliTrace를 사용하여 기록 디버그](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [비디오: Visual Studio 2015를 사용하여 성능 문제 디버그](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [PerfTips: Visual Studio에서 디버깅 중에 성능 정보 한눈에 확인](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)  
  
 [Visual Studio 2015의 진단 도구 디버거 창](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [Visual Studio Enterprise 2015의 IntelliTrace](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
