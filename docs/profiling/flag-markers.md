---
title: 플래그 표식 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccc0c7aa3386e906ad13331a596953db70240701
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969965"
---
# <a name="flag-markers"></a>플래그 표식
플래그 마커는 응용 프로그램에서 특정 시점에 발생한 항목을 나타냅니다. 플래그는 여러 종류의 애플리케이션 이벤트를 나타낼 수 있습니다. 예를 들어 특정 작업 항목이 예약되었거나 예외가 throw될 때 플래그가 표시될 수 있습니다. 작업 병렬 라이브러리와 같은 런타임도 플래그를 생성할 수 있습니다.

## <a name="flag-importance"></a>플래그 중요도
 플래그는 중요도에 따라 여러 크기로 표시됩니다. 모든 마커처럼 중요도는 낮음, 보통, 높음 또는 중요일 수 있습니다.  이 그림은 중요도 수준별로 마커의 모양을 보여줍니다.

 ![낮음, 보통, 높음 및 중요 중요도 표식](../profiling/media/cvmarkerimportance.png "CVMarkerImportance") 플래그 중요도를 보여주는 표식

## <a name="flag-category"></a>플래그 범주
 플래그는 해당 범주에 따라 5가지 다른 색상 중 하나로 표시됩니다. 범주가 5개 이상이면 색상이 재사용됩니다. 색상은 선택할 수 없습니다. 모든 마커와 같이 범주는 임의의 정수일 수 있습니다. 다음 그림은 처음 5개 범주에 대한 색상을 보여줍니다.

 ![범주 표식의 5가지 색](../profiling/media/cvmarkercategory.png "CVMarkerCategory") 범주를 보여주는 표식

## <a name="alerts"></a>경고
 경고는 중요 애플리케이션 이벤트(예: 예외)를 나타내는 빨간색 플래그입니다.  경고는 다음과 같습니다.

 ![동시성 시각화 도우미 경고 표식](../profiling/media/cvmarkeralert.png "CVMarkerAlert") 경고 표식

## <a name="aggregation-flags"></a>집계 플래그
 일부 경우에는 동시성 시각화 도우미에서 플래그가 서로 너무 가깝게 붙어서 개별적으로 그릴 수 없을 수 있습니다. 이 경우에는 내부 플래그를 나타내는 회색 *집계 플래그*가 표시됩니다. 이러한 아이콘 중 하나에 포인터를 놓으면 안에 있는 플래그 수가 도구 설명에 표시됩니다. 플래그를 보려면 확대합니다. 끝까지 확대했는데도 집계 플래그가 계속 보이면 [표식 보고서](../profiling/markers-report.md)에서 내부 플래그를 볼 수 있습니다.

 집계 플래그는 여러 크기로 그려집니다. 크기는 집계에서 가장 중요한 플래그의 중요도 수준에 따라 달라집니다. 다음 그림은 중요도가 낮은 순으로 집계 플래그를 보여줍니다.

 ![4가지 중요도 수준을 표시하는 집계 플래그](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate") 중요도 수준별 집계 플래그

## <a name="see-also"></a>참조
- [동시성 시각화 도우미 표식](../profiling/concurrency-visualizer-markers.md)
- [동시성 시각화 도우미 SDK](../profiling/concurrency-visualizer-sdk.md)