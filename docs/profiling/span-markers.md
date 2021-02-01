---
title: 범위 표식 | Microsoft Docs
description: 범위 표식을 사용하여 애플리케이션의 의미 있는 단계를 나타내는 방법을 알아보고 동시성 시각화 도우미에서 범위를 표시하는 예제를 살펴봅니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fb9da2e838a17f5b014c3b1af4fc9ee5ab46d7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720113"
---
# <a name="span-markers"></a>범위 표식
범위 표식은 애플리케이션에서 중요한 한 단계를 나타냅니다. 예를 들어 범위를 사용하면 특정 작업 항목을 처리하는 기간의 간격을 나타낼 수 있습니다. 범위의 길이는 해당 애플리케이션 단계의 길이를 나타냅니다. 다음 그림은 동시성 시각화 도우미에서 범위를 보여줍니다.

 ![동시성 시각화 도우미의 범위 표식](../profiling/media/cvmarkerspan.png "CVMarkerSpan") 동시성 시각화 도우미의 범위 표식

## <a name="span-category"></a>범위 범주
 범위 표식은 해당 범주에 따라 5가지 색상 중 하나로 표시됩니다. 범주가 5개 이상이면 색상이 반복됩니다. 범주는 임의의 정수일 수 있습니다. 다음 그림은 5가지 사용 가능한 색상을 보여줍니다.

 ![다양한 범주의 5가지 범위](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") 처음 5개 범위 범주 색

## <a name="span-aggregation-markers"></a>범위 집계 표식
 일부 경우에는 동시성 시각화 도우미에서 범위 표식이 너무 가깝게 표시되어 개별적으로 그리기 어려울 수 있습니다. 이 경우에는 내부 범위를 나타내는 회색 *범위 집계 표식* 이 표시됩니다. 이러한 아이콘 중 하나에 포인터를 놓으면 안에 있는 범위 수가 도구 설명에 표시됩니다. 범위를 보려면 확대하십시오. 끝까지 확대해도 범위 집계 표식이 보이면 [표식 보고서](../profiling/markers-report.md)에서 내부 범위 표식을 볼 수 있습니다. 다음 그림은 범위 집계 표식을 보여줍니다.

 ![동시성 시각화 도우미의 집계 범위 표식](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") 범위 집계 표식

## <a name="see-also"></a>추가 정보
- [동시성 시각화 도우미 표식](../profiling/concurrency-visualizer-markers.md)
- [동시성 시각화 도우미 SDK](../profiling/concurrency-visualizer-sdk.md)