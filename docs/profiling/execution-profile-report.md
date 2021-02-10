---
title: 실행 프로필 보고서 | Microsoft 문서
description: Visual Studio용 동시성 시각화 도우미 확장의 기존 샘플링 프로필인 실행 프로필 보고서에 관해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7a61e3a9ba159977d4a835126b2a584be1597c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955257"
---
# <a name="execution-profile-report"></a>실행 프로필 보고서
실행 프로필 보고서는 전통적인 샘플링 프로필입니다. 논리 코어에서 스레드가 실행 중인 기간에 거의 밀리초마다 샘플이 수집되고 동시성 시각화에서는 누적된 샘플 스택 집합의 데이터를 정렬하여 일반적인 호출 트리를 빌드합니다. 현재 시간 범위와 숨겨진 스레드 및 적용될 수 있는 다음과 같은 필터가 이 테이블의 데이터에 영향을 미칠 수 있습니다.

- 내 코드만을 선택하면 사용자 코드와 사용자 코드 아래에 한 수준이 포함된 스택 프레임만 표시됩니다.

- 노이즈 감소 값을 설정하면 지정된 빈도보다 적게 포함된 데이터 정렬된 스택이 보고서에서 필터링됩니다.

  다음 표에서는 보고서에 있는 열을 보여 줍니다.

|열|설명|
|------------|-----------------|
|Name|호출 스택의 각 수준에 대한 함수의 이름입니다.|
|포괄 샘플|호출 스택 트리의 이 수준으로 롤업되는 모든 스택에 대해 수집된 총 샘플 수입니다. 포괄 수는 이 함수에 대한 전용 샘플 및 모든 하위 노드에 대한 포괄 카운터의 합계입니다.|
|전용 샘플|이 함수가 호출 스택의 최하위 수준에 있는 경우 수집된 총 샘플 수입니다.|
|% 포함|포괄 샘플 열에 표시된 총 샘플의 백분율입니다. 백분율은 소수점 이하 두 자리까지 반올림됩니다.|
|% 제외|전용 샘플 열에 표시된 총 샘플의 백분율입니다. 백분율은 소수점 이하 두 자리까지 반올림됩니다.|
|세부 정보|함수의 정규화된 이름입니다. 여기에는 사용 가능한 경우 줄 수가 포함됩니다.|

 이 보고서 테이블은 [실행 시간(스레드 뷰)](../profiling/execution-time-threads-view.md) 뷰에서 볼 수 있습니다.

## <a name="see-also"></a>참조
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)