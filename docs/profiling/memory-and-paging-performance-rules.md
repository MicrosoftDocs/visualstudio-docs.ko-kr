---
title: 메모리 및 페이징 성능 규칙 | Microsoft Docs
description: 메모리 및 페이징 범주의 성능 규칙을 사용하여 애플리케이션 성능과 응답성에 영향을 줄 수 있는 프로파일링 실행의 페이징 작업을 식별하는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1cddda12fbb67f9b604186e754146558cdd62ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720607"
---
# <a name="memory-and-paging-performance-rules"></a>메모리 및 페이징 성능 규칙
메모리의 성능 규칙 및 페이징 범주는 애플리케이션 성능과 응답성에 영향을 줄 수 있는 프로파일링 실행의 페이징 작업을 식별합니다.

|규칙|설명|
|-|-|
|[DA0014: 활성 메모리를 디스크에 페이징하는 비율이 매우 높습니다.](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|프로파일링 실행 전체에서 발생된 디스크 간 활성 메모리를 페이징하는 비율이 매우 높습니다. 이 수준의 페이징 비율은 대개 애플리케이션 성능 및 응답성에 영향을 미칩니다. 알고리즘을 수정하여 메모리 할당을 줄여 보세요. 애플리케이션의 메모리 요구 사항을 고려해야 할 수도 있습니다. 더 많은 메모리가 있는 컴퓨터에서 프로파일링을 다시 실행하세요. 이 규칙은 페이징 작업의 양이 D0017 규칙의 상한 임계값을 초과할 때 발생합니다.|
|[DA0017: 활성 메모리를 디스크에 페이징하는 비율이 높습니다.](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|프로파일링 실행 전체에서 발생된 디스크 간 활성 메모리를 페이징하는 비율이 비교적 높습니다. 이 수준의 페이징 비율은 대개 애플리케이션 성능 및 응답성에 영향을 미칩니다. 알고리즘을 수정하여 메모리 할당을 줄여 보세요. 애플리케이션의 메모리 요구 사항을 고려해야 할 수도 있습니다. 더 많은 메모리가 있는 컴퓨터에서 프로파일링을 다시 실행하세요.|
