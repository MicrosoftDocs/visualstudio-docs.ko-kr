---
title: 요약 뷰 - .NET 메모리 데이터 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a67902af99eaee6c75f92f86c2481dfc2afd744e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771558"
---
# <a name="summary-view---net-memory-data"></a>요약 뷰 - .NET 메모리 데이터
요약 뷰에는 .NET 함수 및 메모리를 가장 많이 할당한 형식과 프로파일링 실행에서 가장 여러 번 생성된 형식에 대한 정보가 표시됩니다. 알림 링크 및 보고서 목록에 대한 설명을 비롯한 자세한 내용은 [요약 뷰](../profiling/summary-view.md)를 참조하세요.

## <a name="timeline-graph"></a>시간 표시 막대 그래프
 요약 뷰의 시간 표시 막대 그래프에는 프로파일링이 수행된 시간 동안 프로파일링된 애플리케이션의 프로세서(CPU) 사용률이 표시됩니다. 시간 표시 막대 그래프를 사용하여 보기를 선택한 시간 범위로 필터링할 수 있습니다. 자세한 내용은 [방법: 요약 시간 표시 막대에서 보고서 뷰 필터링](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)을 참조하세요.

## <a name="functions-allocating-most-memory"></a>대부분의 메모리를 할당하는 함수
 프로파일링 실행에서 메모리(바이트)를 가장 많이 할당한 함수의 목록이 표시됩니다.

|열|Description|
|------------|-----------------|
|**이름**|함수의 이름입니다.|
|**바이트 %**|프로파일링 실행에서 이 함수 또는 이 함수가 호출한 자식 함수에 의해 할당된 모든 바이트의 백분율입니다.|

## <a name="types-with-most-memory-allocated"></a>대부분의 메모리가 할당된 형식
 프로파일링 실행에서 가장 많은 메모리(바이트)가 할당된 형식의 목록이 표시됩니다.

|열|Description|
|------------|-----------------|
|**이름**|형식의 이름입니다.|
|**바이트 %**|프로파일링 실행에서 이 형식에 대해 할당된 모든 바이트의 백분율입니다.|

## <a name="types-with-most-instances"></a>대부분의 인스턴스가 있는 형식
 프로파일링 실행 중에 가장 여러 번 생성된 형식의 목록이 표시됩니다.

|열|Description|
|------------|-----------------|
|**이름**|형식의 이름입니다.|
|**인스턴스 %**|프로파일링 실행에서 생성된 이 형식의 인스턴스인 .NET 개체의 총 수 백분율입니다.|

## <a name="see-also"></a>참고 항목
- [요약 뷰 - 샘플링 데이터](../profiling/summary-view-sampling-data.md)
- [요약 뷰 - 계측 데이터](../profiling/summary-view-instrumentation-data.md)
