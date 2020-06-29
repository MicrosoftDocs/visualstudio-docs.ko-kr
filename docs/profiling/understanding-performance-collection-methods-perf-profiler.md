---
title: 성능 데이터 수집 방법 이해 | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 03a49763a682f6b98b02fe40ba957efa8f5483c8
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290975"
---
# <a name="understand-performance-collection-methods"></a>성능 데이터 수집 방법 이해

이 문서에서는 Visual Studio 성능 프로파일러 내의 도구에서 사용하는 데이터 수집 방법에 대해 간략하게 설명합니다. 

## <a name="sampling"></a>샘플링

프로파일링 샘플링 방법은 프로파일링 실행 중에 애플리케이션이 수행하는 작업에 대한 통계 데이터를 수집합니다. 데이터 수집은 정기적 샘플링 주기(예: 밀리초 단위)로 정보를 수집한 다음 이 데이터를 분석하여 애플리케이션에서 시간이 소요된 위치를 모델링하여 수행됩니다. 샘플링 방법은 간단하며 프로파일링되는 애플리케이션의 실행에 거의 영향을 주지 않습니다. 샘플링 방법을 활용하는 성능 프로파일러 도구에는 [CPU 사용량](../profiling/cpu-usage.md) 도구가 포함됩니다.

## <a name="instrumentation"></a>계측

계측 프로파일링은 프로파일링 실행 중에 애플리케이션이 수행하는 작업에 대한 자세한 정보를 수집합니다. 데이터 수집은 타이밍 정보를 캡처하는 이진 파일에 코드를 삽입하는 도구를 통해 또는 애플리케이션이 실행되는 동안 정확한 타이밍 및 호출 수 정보를 수집하고 내보내는 데 콜백 후크를 사용하여 수행됩니다. 계측 방법은 샘플링 기반 접근 방법과 비교할 때 오버헤드가 높습니다. 계측을 사용하는 성능 프로파일러 도구에는 [.NET 개체 할당](../profiling/dotnet-alloc-tool.md) 도구가 포함됩니다.