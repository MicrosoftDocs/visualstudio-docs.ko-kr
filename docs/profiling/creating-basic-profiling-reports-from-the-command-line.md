---
title: 명령줄에서 기본 프로파일링 보고서 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd9748d88a9398792274c386a42bdaa3ce48ba70
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777792"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>명령줄에서 기본 프로파일링 보고서 만들기
이 문서에서는 .*vsp* 또는 .*vsps* 프로파일링 데이터 파일에서 쉼표로 구분된 값(.*csv*) 보고서를 생성하는 기본 VSPerfReport 명령을 설명합니다. 모든 보고서 옵션에 대한 설명은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.

## <a name="report-commands"></a>보고서 명령
 다음 명령 중 하나를 사용하여 지정된 프로파일링 데이터 파일에 대한 보고서를 만듭니다.

 **VSPerfReport** `VSPFile` **/Summary:All** .*vsp* 또는 .*vsps* 파일에 사용할 수 있는 모든 보고서를 생성합니다.

 **VSPerfReport** `VSPFile` **/Summary:** `ReportType`[,`ReportType`...] 지정된 보고서 형식을 생성합니다.

 **VSPerfReport** `VSPFile` **/CallTrace** 각 데이터 수집 이벤트를 나열하는 보고서를 생성합니다. 계측만 해당합니다.

## <a name="summary-report-type-parameters"></a>요약 보고서 형식 매개 변수
 다음 표에서는 지정된 보고서 형식 옵션에 의해 생성되는 보고서를 설명합니다. 보고서의 열은 데이터를 수집하는 데 사용된 프로파일링 방법에 따라 다릅니다.

|요약 매개 변수|보고서 설명|보고서 참조|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|함수 간의 부모/자식 관계를 나타냅니다.|-   [샘플링 데이터](../profiling/caller-callee-view-sampling-data.md)<br />-   [계측 데이터](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET 메모리 샘플링 데이터](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET 메모리 계측 데이터](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [경합 데이터](../profiling/caller-callee-view-contention-data.md)|
|**Function**|함수별로 프로파일링 데이터를 나열합니다.|-   [샘플링 데이터](../profiling/functions-view-sampling-data.md)<br />-   [계측 데이터](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET 메모리 샘플링 데이터](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET 메모리 계측 데이터](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [경합 데이터](../profiling/functions-view-contention-data.md)|
|**CallTree**|프로파일링 실행 시 함수의 실행 경로 및 프로파일링 데이터를 나타냅니다.|-   [계측 데이터](../profiling/call-tree-view-instrumentation-data.md)<br />-   [샘플링 데이터](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET 메모리 샘플링 데이터](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET 메모리 계측 데이터](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [경합 데이터](../profiling/call-tree-view-contention-data.md)|
|**Counter**|프로파일링 실행 중에 수집된 프로파일링 표시 및 Windows 성능 카운터 값을 나열합니다.|-   [표시 뷰](../profiling/marks-view.md)|
|**Ip**|계측별로 프로파일링 데이터를 나열합니다.|-   [샘플링 데이터](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET 메모리 샘플링 데이터](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [경합 데이터](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Life**|할당된 개체의 수명을 나열합니다.|-   [개체 수명 뷰](../profiling/object-lifetime-view.md)|
|**Line**|소스 코드 줄별로 프로파일링 데이터를 나열합니다.|-   [샘플링 데이터](../profiling/lines-view-sampling-data.md)<br />-   [.NET 메모리 샘플링 데이터](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [경합 데이터](../profiling/lines-view-contention-data.md)|
|**Header**|프로파일링 데이터 파일 헤더 정보입니다.|파일에만 한정됩니다.|
|**Mark**|프로파일링 실행 시 수집된 프로파일링 표시입니다.|-   [표시 뷰](../profiling/marks-view.md)|
|**모듈**|모듈에 대한 프로파일링 데이터를 나열합니다.|-   [샘플링 데이터](../profiling/modules-view-sampling-data.md)<br />-   [계측 데이터](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET 메모리 샘플링 데이터](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET 메모리 계측 데이터](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [경합 데이터](../profiling/modules-view-contention-data.md)|
|**Process**|프로세스에 대한 프로파일링 데이터를 나열합니다.|-   [프로세스 뷰](../profiling/process-view.md)<br />-   [경합 데이터](../profiling/process-view-contention-data.md)|
|**스레드**|스레드에 대한 프로파일링 데이터를 나열합니다.|-   [프로세스 뷰](../profiling/process-view.md)|
|**Type**|형식별로 할당 프로파일링 데이터를 나열합니다.|-   [할당 뷰](../profiling/dotnet-memory-allocations-view.md)|
|**경합**|리소스 경합입니다.|-   [리소스 경합](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|성능 규칙 문제를 나열합니다.|-   CheckId, 설명 및 규칙 문제의 소스 코드 위치를 나열합니다.|
|**ETW**|프로파일링 실행 시 수집된 ETW(Windows용 이벤트 추적) 이벤트를 나열합니다.|-   [ETW 보고서](../profiling/event-tracing-for-windows-etw-report.md)|
