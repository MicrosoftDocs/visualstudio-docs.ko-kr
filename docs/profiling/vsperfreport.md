---
title: VSPerfReport | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 54d5de2395c0ce95bc0c20c3ae7810b2762122fa
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329953"
---
# <a name="vsperfreport"></a>VSPerfReport
VSPerfReport 명령줄 도구는 데이터 파일을 프로파일링하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구를 사용하여 보고서를 만드는 데 사용됩니다. 기본 보고서 형식은 .*csv* 파일입니다.

 VSPerfReport는 다음 구문을 사용합니다.

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 `filename`은 유효한 .*vsp* 또는 .*vsps* 파일이어야 합니다.

 VSPerfReport 명령줄 도구는 .*vsp* 또는 .*vsps* 파일을 비교하는 데도 사용됩니다. 차이("diff") 보고서를 생성하려면 다음 구문을 사용합니다.

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2`는 유효한 .*vsp* 또는 .*vsps* 파일이어야 합니다.

## <a name="symbol-files"></a>기호 파일
 함수 이름 및 줄 번호와 같은 기호 정보를 표시하려면 VSPerfReport가 프로파일링된 구성 요소의 기호(.PDB) 파일과 Windows 기호 파일에 액세스할 수 있어야 합니다. 자세한 내용은 [방법: 명령줄에서 기호 파일 위치 지정](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)을 참조하세요.

## <a name="general-report-options"></a>일반 보고서 옵션
 다음 표에서는 일반 보고서 서식 옵션과 보고할 데이터를 선택하는 옵션에 대해 설명합니다.

|옵션|설명|
|-------------|-----------------|
|**U**|보고서 출력 및 리디렉션된 콘솔 출력이 유니코드로 기록됩니다. 이 옵션을 첫 번째 옵션으로 지정해야 합니다.|
|**Summary:** [*types*]|하나 이상의 보고서 형식을 만듭니다.<br /><br /> -   `All` - 모든 보고서 형식이 생성됩니다.<br />-   `CallerCallee` - 함수 간의 부모/자식 관계입니다.<br />-   `Function` - 호출된 함수입니다.<br />-   `CallTree` - 호출된 함수의 계층 구조입니다.<br />-   `Counter` - 모든 표시와 Windows 성능 카운터 값입니다.<br />-   `Ip` - 프로 파일링된 명령입니다.<br />-   `Life` - 할당된 개체의 수명입니다(할당 데이터가 수집되면 사용 가능함).<br />-   `Line` - 소스 코드 줄 프로필 데이터입니다.<br />-   `Header` - 보고서에 파일 헤더 정보가 포함됩니다.<br />-   `Mark` - 모든 표시입니다.<br />-   `Module` - 프로파일링된 모듈입니다.<br />-   `Process` - 프로파일링된 프로세스입니다.<br />-   `Thread` - 프로파일링된 스레드입니다.<br />-   `Type` - 할당된 형식입니다.<br />-   `Contention` - 리소스 경합입니다.<br />-   `RuleWarnings` - 성능 규칙 문제입니다.<br />-   `ETW` - 프로 파일링 실행 시 수집된 모든 ETW(Windows용 이벤트 추적) 이벤트입니다. .etl 데이터 파일은 원래 위치에 있거나 .vsp 또는 .vsps 파일을 포함하는 디렉터리에 있어야 합니다.|
|**Xml**|보고서를 XML 형식으로 출력합니다.|
|**CallTrace**|함수 시작 및 종료, ETW 이벤트 및 표시 목록을 만듭니다.|
|**ClearPackedSymbols**|프로파일러 데이터 파일에서 이전에 포함된 기호를 제거합니다. PackSymbols를 두 번째로 실행하기 전에 이 명령을 실행합니다.|
|**SymbolPath:** `path`|프로파일러 데이터 파일에 대한 기호를 포함하는 하나 이상의 검색 경로 또는 기호 서버를 지정합니다.|
|**DebugSymPath**|기호가 검색된 위치 및 찾았는지 여부를 나열합니다. 이 옵션은 기호 확인 문제를 해결하는 데 유용합니다.|
|**PackSymbols**|기호(.*pdb*) 파일이 분석에 필요 없도록 프로파일링 데이터(.vsp) 파일에 기호를 저장합니다.|
|**Output:** *path*&#124;*filename*|생성된 보고서 파일에 대한 대체 위치를 지정합니다. 기본적으로 보고서는 현재 디렉터리에 만들어집니다.|
|**SummaryFile**|분석을 수행한 후 분석한 정보를 .vsps 요약 파일에 저장합니다.|
|**PrintMarks**|지정한 vsp 파일에 있는 모든 표시의 이름 및 타임스탬프를 표시합니다.|
|**?**|사용 정보를 표시합니다.|
|**NoLogo**|보고서를 실행하고 있을 때 버전 정보를 숨깁니다.|
|**UserRulesDirectory**|사용자 정의 성능 규칙을 포함하는 디렉터리를 지정합니다[아직 구현되지 않음은].|

## <a name="filter-options"></a>필터 옵션
 다음 표에서는 사용할 수 있는 데이터를 필터링하기 위한 옵션에 대해 설명합니다.

|옵션|설명|
|-------------|-----------------|
|**JustMyCode**[ **:** [`caller`][,`callee`]]|사용자 애플리케이션 함수 호출만 표시하고 시스템 호출은 숨깁니다.<br /><br /> - 매개 변수 없음 - 시스템 함수를 모두 숨깁니다.<br />-   `caller` - 애플리케이션 함수를 호출하는 한 수준의 시스템 함수를 표시합니다.<br />-   `callee` - 사용자 애플리케이션 함수가 호출하는 한 수준의 시스템 함수를 표시합니다.|
|**StartTime:** [*value*]|value 이후에 수집된 데이터만 표시합니다(밀리초).|
|**EndTime:** [*value*]|value 이전에 수집된 데이터만 표시합니다(밀리초).|
|**FilterFile:** `VSPFFile`|Visual Studio 성능 보고서 창에서 생성된 필터 파일의 위치를 지정합니다.|
|**MsFilter:** [*starttime,duration*]|`starttime`부터 `duration` 길이(밀리초)까지의 데이터만 표시합니다.|
|**Process:** [*pid*]|지정한 프로세스의 데이터만 표시합니다.|
|**Thread:** [*threadid*]|지정한 스레드의 데이터만 표시합니다.|
|**Thread:** [*threadid,processid*]|지정한 프로세스와 관련된 특정 스레드의 데이터만 표시합니다.|

## <a name="difference-report-options"></a>차이점 보고서 옵션
 다음 표에서는 보고서 파일을 비교하기 위한 옵션에 대해 설명합니다.

|옵션|설명|
|-------------|-----------------|
|**Diff**  `vspfile1 vspfile2`|두 개의 보고서 파일(.*vsp* 또는 .*vsps*)을 비교합니다. diff 옵션을 사용하면 Summary 옵션은 무시됩니다.|
|**Diff:** [*value*]|이 임계값 아래에서는 두 값의 차이가 무시됩니다. 또한 이 임계값보다 낮은 값을 갖는 새 데이터는 표시되지 않습니다.|
|**DiffTable:** [*tablename*]|이 특정 테이블을 사용하여 파일을 비교합니다. 기본값은 함수 테이블입니다.|
|**DiffColumn:** [*columnname*]|이 특정 열 비교 값을 사용합니다. 기본값은 전용 샘플 백분율 열입니다.|
|**QueryDiffTables**|제공한 두 보고서 파일의 올바른 테이블 및 열을 나열합니다.|

## <a name="see-also"></a>참조
- [성능 보고서 뷰](../profiling/performance-report-views.md)
