---
title: DA0021 - Gen 1 가비지 수집의 비율이 높습니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b22341f1e4944b91f86a16af19494a85a2abd013
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544692"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Gen 1 가비지 수집의 비율이 높습니다.

|항목|값|
|-|-|
|규칙 ID|DA0021|
|범주|.NET Framework 사용|
|프로파일링 방법|모두|
|메시지|Gen 1 가비지 수집의 비율이 상당히 높습니다. 의도적으로 프로그램의 데이터 구조가 대다수 오랜 시간 동안 할당되고 지속되는 경우 일반적으로 이러한 현상은 문제가 되지 않습니다. 하지만 이러한 동작이 의도되지 않은 경우에는 애플리케이션이 개체를 고정하고 있는 것일 수 있습니다. 확실하지 않으면 .NET 메모리 할당 데이터 및 개체 수명 정보를 수집하여 애플리케이션이 사용하는 메모리 할당 패턴을 파악할 수 있습니다.|
|규칙 유형|정보|

 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.

## <a name="cause"></a>원인
 프로파일링 중에 수집된 시스템 성능 데이터는 0세대 데이터 수집에 비해 .NET Framework 개체용 메모리의 상당한 부분이 가비지 수집의 1세대에서 회수되었음을 나타냅니다.

## <a name="rule-description"></a>규칙 설명
 Microsoft .NET CLR(공용 언어 런타임)는 가비지 수집을 사용하여 애플리케이션에 더 이상 사용되지 않는 개체에서 메모리를 회수하는 자동 메모리 관리 메커니즘을 제공합니다. 가비지 수집기는 많은 할당이 단기 유지된다는 가정 하에 세대를 기준으로 합니다. 예를 들어 로컬 변수는 단기 유지되어야 합니다. 새로 만들어진 개체는 0세대(gen 0)에서 시작되고, 가비지 수집 실행에서 생존하면 1세대로 이동하고, 애플리케이션에 계속 사용될 경우 마지막으로 2세대로 전환됩니다.

 0세대의 개체는 빈번하게, 보통 매우 효율적으로 수집됩니다. 1세대의 개체는 덜 빈번하게, 덜 효율적으로 수집됩니다. 마지막으로 2세대의 장기 유지 개체는 훨씬 덜 빈번하게 수집되어야 합니다. 전체 가비지 수집 실행을 나타내는 2세대 수집은 가장 부담이 큰 작업이기도 합니다.

 1세대 수집이 상대적으로 너무 많이 발생한 경우 이 규칙이 실행됩니다. 너무 많은 단기 유지 개체가 0세대 수집에서 생존하지만 1세대 수집에서 이를 수집할 수 있다면 메모리 관리 비용이 과도해질 수 있습니다. 자세한 내용은 MSDN 웹 사이트의 Rico Mariani의 Performance Tidbits에서 [Mid-life crisis](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/)(중간 수명의 위기) 게시물을 참조하세요.

## <a name="how-to-investigate-a-warning"></a>경고를 조사하는 방법
 [오류 목록] 창에서 메시지를 두 번 클릭하여 프로파일링 데이터의 [표시 뷰](../profiling/marks-view.md)로 이동합니다. **.NET CLR Memory\\# of Gen 0 Collections** 및 **.NET CLR Memory\\# of Gen 1 Collections** 열을 찾습니다. 가비지 수집이 더 빈번히 발생하는 특정 프로그램 실행 단계가 있는지 확인합니다. 이러한 값을 **% Time in GC** 열에 비교하여 관리되는 메모리 할당의 패턴이 과도한 메모리 관리 오버헤드를 일으키는지 확인합니다.

 애플리케이션의 관리되는 메모리 사용 패턴을 파악하려면 .NET 메모리 할당 프로필을 실행하여 애플리케이션을 다시 프로파일링하고 개체 수명 측정값을 요청합니다.

 가비지 수집 성능 향상 방법에 대한 자세한 내용은 Microsoft 웹 사이트에서 [가비지 수집기 기본 및 성능 힌트](/previous-versions/dotnet/articles/ms973837(v=msdn.10))를 참조하세요. 자동 가비지 수집의 오버헤드에 대한 자세한 내용은 [Large Object Heap Uncovered](https://msdn.microsoft.com/magazine/cc534993.aspx)(대형 개체 힙 살펴보기)를 참조하세요.
