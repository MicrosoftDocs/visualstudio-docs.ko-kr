---
title: 리소스 경합 데이터 값 이해 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f522d1854cae86d9dc6e757ef0c9a62f4511800
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779989"
---
# <a name="understand-resource-contention-data-values"></a>리소스 경합 데이터 값 이해

리소스 경합 프로파일링에서는 애플리케이션에서 경쟁하는 스레드가 공유 리소스에 액세스하기 위해 대기해야 할 때마다 자세한 호출 스택 정보를 수집합니다.

리소스 경합 보고서에는 총 경합 수와 대기가 발생한 모듈, 함수, 소스 코드 줄 및 명령에서 리소스를 대기하는 데 소요된 총 시간이 표시됩니다.

- 포괄 값에는 함수가 리소스 경합으로 인해 강제로 대기해야 했던 경합의 총 수와 함수가 대기한 총 시간이 표시됩니다.  함수가 호출한 자식 함수에 의해 발생한 경합도 포괄 값에 포함됩니다.

- 전용 값에는 함수 본문의 코드로 인해 발생했으며 함수가 강제로 대기해야 했던 경합의 수만 표시됩니다. 자식 함수에 의해 발생한 경합은 포함되지 않습니다. 또한 함수의 전용 시간에는 함수 본문의 문에 의해 발생한 대기 시간만 포함됩니다.

리소스 경합 보고서 뷰에는 시간별 개별 경합 이벤트 및 특정 이벤트를 생성한 호출 스택을 보여 주는 시간 표시 막대 그래프도 포함됩니다. 자세한 내용은 다음 항목 중 하나를 참조하십시오.

- [스레드 정보 뷰](../profiling/thread-details-view-contention-data.md)

- [리소스 정보 뷰](../profiling/resource-details-view-contention-data.md)

동시성 프로파일링의 두 번째 모드에 대한 자세한 내용은 [Concurrency 시각화](../profiling/concurrency-visualizer.md)를 참조하세요.
