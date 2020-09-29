---
title: 프로파일링 명령줄 - 보고서 만들기
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5eb0f1fa0f9bbe760b1ea89074d02044cf26ab7d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808827"
---
# <a name="create-profiler-reports-from-the-command-line"></a>명령줄에서 프로파일러 보고서 만들기
**VSPerfReport** 명령줄 도구를 통해 프로파일링 데이터(.*vsp*) 파일에서 .*xml* 또는 쉼표로 구분된 값(.*csv*) 보고서를 만들 수 있습니다. VSPerfReport 보고서 유형은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 대한 인터페이스의 테이블 기반 뷰와 일치합니다. 코드만 표시하고 프로파일링 데이터 파일의 세그먼트만 표시하도록 보고서를 필터링할 수 있습니다. 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.

 또한 .*vsp* 파일에 기호를 포함하고 열수 있는 더 작고 더 빠른 미리 분석된 보고서(.*vsps*) 파일을 만들어 프로파일링 데이터 파일을 더 쉽게 공유할 수 있습니다.

## <a name="common-tasks"></a>일반 작업

|Task|관련 내용|
|----------|---------------------|
|**기본 보고서를 만듭니다.** VSPerfReport 보고서 유형의 전체 또는 하위 집합을 만듭니다.|-   [기본 보고서 만들기](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**두 가지 프로파일링 데이터 파일을 비교합니다.** 두 가지 프로파일링 데이터 파일에서 성능 데이터를 비교하는 "diff" 보고서를 만듭니다.|-   [방법: 명령 프롬프트에서 프로파일러 비교 보고서 만들기](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**호출 추적 및 ETW(Windows용 이벤트 추적) 데이터를 봅니다.** 애플리케이션의 함수에 대한 각 진입 지점 및 종료 지점에 대한 타이밍 정보와 함수로 다른 함수에 대한 각 호출을 나열하는 호출 추적 보고서를 만듭니다. 또는 프로파일링 실행 시 수집된 모든 ETW 이벤트의 자세한 목록을 만듭니다.|-   [방법: 호출 추적 보고서 만들기](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**보고서를 필터링합니다.** 코드의 함수로 또는 프로파일링 데이터 파일에서 특정 시간에 대해 보고서를 제한합니다.|-   [방법: 명령줄에서 보고서 필터링](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**이식 가능한 프로파일링 데이터 파일을 만듭니다.** 프로파일링 데이터를 더 쉽게 공유하기 위해 프로파일링 실행에 대한 기호를 .*vsp* 파일로 포함할 수 있습니다. 또한 열 더 작고 더 빠른 미리 분석된 프로파일링 데이터(.*vsps*) 파일을 만들 수도 있습니다.|-   [이식 가능한 프로파일링 데이터 파일 만들기](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
