---
title: 성능 보고서 개요 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 517156677a6d3711fa5dc2e4a15629a55229cfe2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772234"
---
# <a name="performance-report-overview"></a>성능 보고서 개요
Visual Studio Team System Development Edition IDE(통합 개발 환경)의 **성능 보고서** 창에서 성능 세션의 프로파일링 데이터를 볼 수 있습니다. 프로파일링 데이터는 .vsps 및 .vsp 파일에 저장됩니다. 보고서 뷰 창에서는 애플리케이션 성능 문제를 확인하고 분석할 수 있습니다.

> [!CAUTION]
> 프로파일링 데이터 파일에는 컴퓨터 이름, 운영 체제 버전, 파일 경로, 메모리 정보, 기타 컴퓨터 설정 정보 등의 중요한 정보가 포함됩니다. 따라서 기본 .*vsp* 형식을 사용할 때나 .*csv* 또는 .*xml* 파일로 내보낼 때 모두 데이터 배포를 엄격하게 제어해야 합니다.
>
> 성능 세션의 일부분으로 이벤트 추적 데이터를 수집하는 경우에는 이벤트 추적 로그(.*etl*) 파일에 추가 정보가 표시될 수 있습니다. 이 정보에는 사용자의 도메인 및 사용자 이름이 포함되므로 로그 파일 배포 역시 엄격하게 제어해야 합니다.

## <a name="performance-report-window"></a>성능 보고서 창
 성능 보고서 창은 성능 데이터를 확인/관리/필터링하는 데 사용되며 사용자 지정 가능한 쿼리 컨트롤을 포함하는 도구 창입니다.

 성능 보고서 창의 주 도구 모음에서 각 뷰에 액세스할 수 있습니다. **현재 뷰** 목록 옆의 화살표를 클릭하여 사용 가능한 개별 뷰를 표시하고 선택합니다.

 성능 보고서 창에서는 다음 데이터 뷰를 제공합니다.

### <a name="summary-view"></a>요약 뷰
 프로파일링 데이터는 기본적으로 요약 뷰에 표시됩니다. 이 뷰에서부터 성능 문제 조사를 시작합니다. 요약 뷰의 각 줄에서 함수 또는 모듈 이름을 마우스 오른쪽 단추로 클릭하여 더 자세한 뷰로 이동할 수 있습니다. 자세한 내용은 [요약 뷰](../profiling/summary-view.md)를 참조하세요.

### <a name="callercallee-view"></a>호출자/호출 수신자 뷰
 호출자/호출 수신자 뷰에는 개별 함수의 호출 트리가 표시됩니다. 이 뷰는 세 부분으로 구분됩니다.

- 대상 함수는 뷰의 가운데에 표시됩니다.

- 함수를 호출한 함수(호출자)는 대상 함수 위에 표시됩니다.

- 대상 함수에 의해 호출된 함수(호출 수신자)는 대상 아래에 표시됩니다.

  호출한 목록 또는 호출 수신자 목록에서 함수를 두 번 클릭하여 다른 함수를 선택할 수 있습니다. 자세한 내용은 [호출자/호출 수신자 뷰](../profiling/caller-callee-view.md)를 참조하세요.

### <a name="call-tree-view"></a>호출 트리 뷰
 호출 트리 뷰는 프로파일링된 애플리케이션에서 트래버스된 함수 실행 경로를 표시합니다. 트리의 루트는 애플리케이션이나 구성 요소에 대한 진입점입니다. 각 함수 노드에는 호출한 모든 함수 및 이러한 함수 호출에 대한 성능 데이터가 나열됩니다.

 호출 트리 뷰를 확장하여 시간을 가장 많이 사용했거나 가장 자주 샘플링된 함수의 실행 경로를 강조 표시할 수도 있습니다. 가장 많이 사용된 경로를 표시하려면 함수를 마우스 오른쪽 단추로 클릭하고 **실행 부하 과다 경로 확장**을 클릭합니다. 자세한 내용은 [호출 트리 뷰](../profiling/call-tree-view.md)를 참조하세요.

### <a name="process-view"></a>프로세스 뷰
 프로세스 뷰에는 프로파일링된 각 프로세스 및 스레드에 대한 성능 데이터가 표시됩니다. 자세한 내용은 [프로세스 뷰](../profiling/process-view.md)를 참조하세요.

### <a name="modules-view"></a>모듈 뷰
 모듈 뷰에는 프로젝트의 모듈이 나열되고 각 모듈에 대한 프로파일링 데이터가 표시됩니다. 모듈 이름을 확장하거나 축소하여 함수 프로파일링 데이터를 표시합니다. 샘플링을 사용하여 데이터를 수집한 경우에는 소스 코드 줄 및 명령 포인터 프로파일링 데이터도 사용할 수 있습니다. 자세한 내용은 [모듈 뷰](../profiling/modules-view.md)를 참조하세요.

### <a name="functions-view"></a>함수 뷰
 함수 뷰에는 프로파일링 중에 호출된 함수가 나열됩니다. 자세한 내용은 [함수 뷰](../profiling/functions-view.md)를 참조하세요.

### <a name="line-view"></a>줄 뷰
 줄 뷰를 사용하면 샘플링 프로파일링 중에 실행된 특정 소스 코드 줄을 확인할 수 있습니다. 자세한 내용은 [줄 뷰](../profiling/lines-view.md)를 참조하세요.

### <a name="instruction-pointer-ip-view"></a>IP(명령 포인터) 뷰
 명령 포인터 뷰를 사용하면 샘플링 프로파일링 중 실행된 특정 명령을 확인할 수 있습니다. 자세한 내용은 [IP(명령 포인터) 뷰](../profiling/instruction-pointers-ips-view.md)를 참조하세요.

### <a name="allocation-view"></a>할당 뷰
 **성능 세션** 속성 대화 상자의 **일반** 의 페이지에서 **.NET 개체 할당 정보 수집**을 선택한 경우 할당 뷰를 사용할 수 있습니다. [성능 세션 개요](../profiling/performance-session-overview.md)를 참조하세요. 할당 뷰는에는 애플리케이션 또는 구성 요소가 할당한 .NET 개체가 나열됩니다. 개체 행을 확장하면 호출 트리가 표시됩니다. 호출 트리에는 개체가 생성되도록 한 실행 경로가 표시됩니다. 또한 호출 트리의 각 함수에 대한 포괄/전용 할당 횟수에 대한 정보도 표시됩니다. 할당 뷰를 확장하여 가장 많은 수의 개체를 할당한 함수의 실행 경로를 강조 표시할 수도 있습니다. 가장 많이 사용된 경로를 표시하려면 함수를 마우스 오른쪽 단추로 클릭하고 **실행 부하 과다 경로 확장**을 클릭합니다. 자세한 내용은 [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) 및 [할당 뷰](../profiling/dotnet-memory-allocations-view.md)를 참조하세요.

### <a name="objects-lifetime-view"></a>개체 수명 뷰
 **성능 세션** 속성 대화 상자의 **일반** 페이지에서 **.NET 개체 할당 정보 수집** 및 **추가적으로 .NET 개체 수명 정보 수집**을 선택한 경우 개체 수명 뷰를 사용할 수 있습니다.

 개체 수명 뷰에는 각 가비지 수집 세대에서 수집된 개체의 수와 각 유형의 총 인스턴스 수가 표시됩니다. 자세한 내용은 [개체 수명 뷰](../profiling/object-lifetime-view.md)를 참조하세요.

## <a name="customizable-filter-control"></a>사용자 지정 가능한 필터 컨트롤
 사용자 지정 가능한 필터 컨트롤에는 다음과 같은 옵션이 있습니다.

- **필터 가져오기** - 이전에 저장한 사용자 지정 쿼리를 검색합니다.

- **필터 내보내기** - 사용자 지정 쿼리를 지정한 위치에 저장합니다.

- **쿼리 실행** - 사용자 지정 쿼리 컨트롤에 표시된 대로 쿼리를 실행합니다.

- **쿼리 중지** - 실행 중인 쿼리의 실행을 중지합니다. 실행 중인 쿼리가 없으면 이 단추를 사용할 수 없습니다.

- **쿼리 표시** - 사용자 지정 쿼리 컨트롤 표시하거나 숨깁니다.

- **분석 결과 저장** - 보고서를 현재 분석 내용과 함께 .vsps 파일로 저장합니다.

- **내보내기** - 다른 뷰를 저장하는 옵션과 함께 현재 보고서를 .CSV 형식 또는 .XML 형식 파일로 저장합니다.

## <a name="see-also"></a>참고 항목
- [성능 도구 데이터 분석](../profiling/analyzing-performance-tools-data.md)
- [성능 보고서 뷰](../profiling/performance-report-views.md)
