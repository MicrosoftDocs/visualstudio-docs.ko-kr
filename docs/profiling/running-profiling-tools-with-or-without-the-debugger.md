---
title: 디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행 | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3d50f8fcad0294adec032322229e9dd6cedac2
ms.sourcegitcommit: 8e5b0106061bb43247373df33d0850ae68457f5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88508082"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행

Visual Studio는 성능 측정 및 프로파일링 도구 중에서 선택할 수 있습니다. CPU 사용량 및 메모리 사용량과 같은 일부 도구는 디버거를 사용하거나 사용하지 않고 릴리스 또는 디버그 빌드 구성으로 실행할 수 있습니다. 애플리케이션 타임라인과 같은 성능 프로파일러 도구는 디버그 또는 릴리스 빌드에서 실행할 수 있습니다. 진단 도구 창 및 이벤트 탭과 같은 디버거 통합 도구는 디버깅 세션 중에만 실행됩니다.

>[!NOTE]
>Windows 7 이상에서 비-디버거 성능 도구를 사용할 수 있습니다. 디버거 통합 프로파일링 도구를 실행하려면 Windows 8 이상이 필요합니다.

비-디버거 성능 프로파일러 및 디버거 통합 진단 도구는 다양한 환경과 정보를 제공합니다. 디버거 통합 도구는 중단점과 변수 값을 표시합니다. 비-디버거 도구를 사용하면 최종 사용자 환경에 더 가까운 결과를 얻을 수 있습니다.

사용할 도구 및 결과를 결정하려면 다음을 고려하세요.

- 파일 I/O 또는 네트워크 응답 문제와 같은 외부 성능 문제는 디버거 또는 비-디버거 도구에서는 크게 다르지 않습니다.
- CPU를 많이 사용하는 호출로 인해 발생하는 문제의 경우 릴리스 빌드와 디버그 빌드 간에 상당한 성능 차이가 있을 수 있습니다. 릴리스 빌드에 문제가 있는지 확인합니다.
- 디버그 빌드 중에만 문제가 발생하면 비-디버거 도구를 실행할 필요가 없을 것입니다. 릴리스 빌드 문제의 경우 디버거 도구가 추가 조사에 도움이 되는지 여부를 결정합니다.
- 릴리스 빌드는 함수 호출 및 상수 인라인, 사용되지 않는 코드 경로 정리 및 디버거가 사용할 수 없는 방식으로 변수 저장과 같은 최적화를 제공합니다. 디버거 통합 도구의 성능 번호는 덜 정확합니다. 디버그 빌드에는 이러한 최적화가 부족하기 때문입니다.
- 디버거 자체는 예외 및 모듈 로드 이벤트 가로채기와 같은 필요한 디버거 작업을 수행하므로 성능 시간을 변경합니다.
- 성능 프로파일러 도구의 릴리스 빌드 성능 번호가 가장 정밀하고 정확합니다. 디버거 통합 도구 결과는 다른 디버깅 관련 측정과 비교할 때 가장 유용합니다.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> 디버깅하는 동안 프로파일링 데이터 수집

**디버그** > **디버깅 시작**을 선택하거나 **F5**를 눌러 Visual Studio에서 디버깅을 시작하면 기본적으로 **진단 도구 창**이 나타납니다. 수동으로 열려면 **디버그** > **Windows** > **진단 도구 표시**를 선택합니다. **진단 도구**에는 이벤트, 프로세스 메모리 및 CPU 사용량에 대한 정보가 표시됩니다.

![진단 도구 창 스크린샷](../profiling/media/diagnostictoolswindow.png "진단 도구 창")

- 도구 모음의 **설정** 아이콘을 사용하여 **메모리 사용량**, **UI 분석** 및 **CPU 사용량**을 볼지 여부를 선택합니다.

- **설정** 드롭다운 목록에서 **설정**을 선택하여 추가 옵션으로 **진단 도구 속성 페이지**를 엽니다.

- Visual Studio Enterprise를 실행 중인 경우 **도구** > **옵션** > **IntelliTrace**로 이동하여 IntelliTrace를 사용하거나 사용하지 않도록 설정할 수 있습니다.

디버그를 중지하면 진단 세션이 종료됩니다.

### <a name="the-events-tab"></a>이벤트 탭

디버깅 세션 중에 진단 도구 창의 이벤트 탭에 발생하는 진단 이벤트가 나열됩니다. 범주 접두사 중단점, 파일 및 기타 항목을 사용하면 범주에 대한 목록을 빠르게 검사하거나 관심 없는 범주를 건너뛸 수 있습니다.

**필터** 드롭다운 목록을 사용하여 특정 범주의 이벤트를 선택하거나 취소하여 보기 안팎으로 이벤트를 필터링합니다.

![진단 이벤트 필터 스크린샷](../profiling/media/diagnosticeventfilter.png "진단 이벤트 필터")

검색 상자를 사용하여 이벤트 목록에서 특정 문자열을 찾습니다. 다음은 네 개의 이벤트와 일치하는 이름 문자열에 대한 검색 결과입니다.

![진단 이벤트 검색 스크린샷](../profiling/media/diagnosticseventsearch.png "진단 이벤트 검색")

자세한 내용은 [진단 도구 창의 이벤트 탭 검색 및 필터링](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)을 참조하세요.

## <a name="collect-profiling-data-without-debugging"></a>디버깅을 사용하지 않고 프로파일링 데이터 수집

디버깅하지 않고 성능 데이터를 수집하려면 성능 프로파일러 도구를 실행할 수 있습니다.

1. Visual Studio에서 프로젝트를 열고 솔루션 구성을  **릴리스**로 설정하고  **로컬 Windows 디버거** (또는 **로컬 컴퓨터**)를 배포 대상으로 선택합니다.

1. **디버그** > **성능 프로파일러**를 선택하거나 **Alt**+**F2**를 누릅니다.

1. 진단 도구 시작 페이지에서 실행할 하나 이상의 도구를 선택합니다. 프로젝트 형식, 운영 체제 및 프로그래밍 언어에 적용되는 도구만 표시됩니다. **모든 도구 표시**를 선택하여 이 진단 세션에 사용할 수 없는 도구도 확인하세요.

   ![진단 도구 스크린샷](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. 진단 세션을 시작하려면 **시작**을 선택합니다.

   세션을 실행하는 동안 일부 도구는 진단 도구 페이지에 실시간 데이터의 그래프를 표시하고 데이터 수집을 일시 중지 및 다시 시작하는 컨트롤도 표시합니다.

    ![성능 및 진단 허브의 데이터 수집을 보여 주는 스크린샷](../profiling/media/diaghubcollectdata.png "허브 데이터 수집")

1. 진단 세션을 종료하려면 **컬렉션 중지**를 선택합니다.

   분석된 데이터는 **보고서** 페이지에 표시됩니다.

보고서를 저장하고 진단 도구 시작 페이지의 **최근 열린 세션** 목록에서 열 수 있습니다.

![진단 도구 최근에 열린 세션 목록의 스크린샷](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>명령줄에서 프로파일링 데이터 수집

명령줄에서 성능 데이터를 측정하기 위해 Visual Studio 또는 원격 도구와 함께 제공되는 VSDiagnostics.exe를 사용할 수 있습니다. 이는 Visual Studio가 설치되지 않은 시스템에서 성능 추적을 캡처하거나, 성능 추적 컬렉션을 스크립팅하는 데 유용합니다. 자세한 내용은 [명령줄에서 애플리케이션 성능 측정](../profiling/profile-apps-from-command-line.md)을 참조하세요.