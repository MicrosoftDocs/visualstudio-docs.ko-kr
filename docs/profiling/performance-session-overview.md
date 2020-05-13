---
title: 성능 세션 개요 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e7b23a7cbefeace19a3deaa5c1bfc05580081d39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778468"
---
# <a name="performance-session-overview"></a>성능 세션 개요
이 개요에서는 프로파일링의 기본 사항에 대해 설명합니다. 성능 작업을 처음 수행하는 개발자는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구를 통해 빠르게 생산성을 높이고 코드 성능을 개선하는 방법을 파악할 수 있습니다. 그리고 프로파일링에 대해 잘 알고 있는 개발자는 특정 프로파일링 도구의 기능과 프로세스에 대해 대략적으로 확인할 수 있습니다.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구를 사용하면 소스 코드의 성능 문제를 파악하고 사용 가능한 해결 방법의 성능을 비교할 수 있습니다. 프로파일링 도구 마법사와 기본 설정을 사용하면 대다수 성능 문제를 즉시 파악할 수 있습니다. 프로파일링 도구의 기능과 옵션을 통해 프로파일링 프로세스를 정확하게 제어할 수 있습니다. 이러한 제어에는 코드 섹션의 정확한 대상 지정, 블록 수준 타이밍 정보 수집, 데이터에 추가 프로세서 및 시스템 성능 데이터 포함 등이 있습니다.

 프로파일링 도구를 사용하는 기본 프로세스는 다음 단계로 구성됩니다.

1. 수집 방법과 수집할 데이터를 지정하여 성능 세션을 구성합니다.

2. 성능 세션에서 애플리케이션을 실행하여 프로파일링 데이터를 수집합니다.

3. 데이터를 분석하여 성능 문제를 파악합니다.

4. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE(통합 개발 환경)에서 코드를 수정하여 코드의 애플리케이션 성능을 개선합니다.

5. 변경된 코드에서 프로파일링 데이터를 수집하여 원래 데이터와 변경된 데이터의 프로파일링 데이터를 비교합니다.

6. 성능 개선 사항을 설명하는 보고서를 생성합니다.

   프로파일링을 통해 제공되는 정보를 사용하려면 프로파일링할 이진 파일 및 Windows 운영 체제의 이진 파일에 대해 기호 정보를 사용할 수 있어야 합니다.

## <a name="configure-the-performance-session"></a>성능 세션 구성
 프로파일링 세션을 구성하려면 사용할 프로파일링 방법과 수집할 데이터를 선택합니다. 프로파일링 도구 **성능 마법사**는 기본 구성을 안내할 수 있으며, 성능 세션 속성 페이지를 사용하여 옵션을 더 추가할 수 있습니다.

- 프로파일링 방법에는 샘플링, 추적 및 메모리 할당이 포함됩니다.

- 데이터 값에는 시간, 프로세서 및 운영 체제 성능 카운터와 애플리케이션 이벤트(예: 페이지 폴트, 커널 전환) 등이 있습니다.

  프로젝트 솔루션의 일부분으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트에서 성능 세션을 구성하거나, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE를 통해 임의의 이진 파일을 프로파일링할 수 있습니다. 성능 세션 속성 페이지에서 세션 속성을 지정할 수도 있고 프로파일링 마법사를 사용할 수도 있습니다.

## <a name="collect-profiling-data"></a>프로파일링 데이터 수집
 **성능 탐색기**에서 프로파일링 데이터 수집을 시작합니다. 프로파일링을 일시 중지하고 다시 시작하여 수집하는 데이터의 양을 제한할 수 있습니다. 이미 실행 중인 프로세스에 연결할 수도 있습니다.

 애플리케이션이 시작되는 즉시 **데이터 수집 제어** 창이 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE에 표시됩니다. **데이터 수집 제어** 창에서 수집 프로세스를 일시 중지하고 다시 시작하여 특정 애플리케이션 부분을 프로파일링할 수 있습니다. **데이터 수집 제어** 창을 사용하여 수집되는 데이터에 표시를 삽입할 수도 있습니다. 표시는 프로파일링 뷰에 표시되며 프로파일링 데이터를 필터링하는 데 사용할 수 있는 사용자 정의 데이터 요소입니다.

 대상 애플리케이션이 종료되면 프로파일링 도구는 프로파일링 데이터 파일(*.vsp)을 생성하고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE에 요약 보고서 뷰를 표시합니다.

## <a name="analyze-the-data-and-identify-performance-issues"></a>데이터 분석 및 성능 문제 파악
 프로파일링 실행을 종료하면 데이터가 분석되어 프로파일링 도구 **성능 보고서** 뷰 창에 요약이 표시됩니다. 대상 애플리케이션의 개별 함수와 호출 스택에 대해 프로파일링 데이터가 수집됩니다. 보고서 뷰에는 애플리케이션 프로세스, 스레드, 모듈, 함수 및 소스 코드 줄의 데이터 범위에 대한 성능 분석이 표시됩니다. 함수의 프로파일링 데이터 값에는 다음 항목이 포함됩니다.

- 함수 및 해당 함수가 호출한 자식 함수에서 소요된 전체 시간(포괄 값)

- 함수의 코드만 실행하는 데 소요된 시간(전용 값)

  12개가 넘는 개별 뷰를 통해 가장 효율적인 방식으로 프로파일링 데이터를 분석할 수 있습니다. 뷰를 사용자 지정하면 데이터를 필터링하고 정렬하여 성능 문제를 발생시킬 수 있는 함수를 찾을 수 있습니다. 실행 부하 과다 경로 필터링을 수행하면 호출 트리 및 모듈 뷰에서 가장 사용량이 많은 경로가 즉시 강조 표시됩니다.

## <a name="modify-the-application-code"></a>애플리케이션 코드 수정
 관련 성능 문제가 하나 이상 파악되면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE를 사용하여 코드를 수정한 다음 변경 내용에 대해 프로파일링 데이터를 수집할 수 있습니다.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>프로파일링 데이터 다시 수집 및 프로파일링 실행 간에 데이터 비교
 프로파일링 도구 비교 보고서 뷰에는 선택한 두 프로파일링 데이터 파일 간의 모듈, 함수 또는 줄 성능 차이가 표시됩니다. 비교할 프로파일링 데이터 값을 지정할 수 있으며, 비교 뷰와 개별 파일 뷰 간을 전환할 수 있습니다.

## <a name="generate-a-report-of-the-results"></a>결과 보고서 생성
 성능 보고서 뷰의 행을 전자 메일과 스프레드시트에 붙여 넣을 수 있으며, 뷰 하나 이상의 데이터가 포함된 보고서를 생성할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [개요](../profiling/overviews-performance-tools.md)
- [연습: 성능 문제 확인](beginners-guide-to-cpu-sampling.md)
