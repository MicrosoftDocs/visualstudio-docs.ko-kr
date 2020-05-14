---
title: 'DA0005: GC2 컬렉션이 많습니다. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a50567a101d77ed6498aaae13a5fe5556d9c1056
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777714"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: GC2 컬렉션이 많습니다.

|||
|-|-|
|RuleId|DA0005|
|Category|.NET Framework 사용|
|프로파일링 방법|.NET 메모리|
|메시지|대부분의 개체는 2세대 가비지 수집에서 수집됩니다.|
|메시지 유형|Warning|

## <a name="cause"></a>원인
 많은 .NET 메모리 개체가 2세대 가비지 수집에서 회수됩니다.

## <a name="rule-description"></a>규칙 설명
 Microsoft .NET CLR(공용 언어 런타임)은 가비지 수집기를 사용하여 애플리케이션에 더 이상 사용되지 않는 개체에서 메모리를 회수하는 자동 메모리 관리 메커니즘을 제공합니다. 가비지 수집기는 많은 할당이 단기 유지된다는 가정 하에 세대를 기준으로 합니다. 예를 들어 로컬 변수는 단기 유지되어야 합니다. 새로 만들어진 개체는 0세대(gen 0)에서 시작되고, 가비지 수집 실행에서 생존하면 1세대로 이동하고, 애플리케이션에 계속 사용될 경우 마지막으로 2세대로 전환됩니다.

 0세대의 개체는 빈번하게, 보통 매우 효율적으로 수집됩니다. 1세대의 개체는 덜 빈번하게, 덜 효율적으로 수집됩니다. 마지막으로 2세대의 장기 유지 개체는 훨씬 덜 빈번하게 수집되어야 합니다. 전체 가비지 수집 실행을 나타내는 2세대 수집은 가장 부담이 큰 작업이기도 합니다.

 2세대 수집이 상대적으로 너무 많이 발생한 경우 이 규칙이 실행됩니다. 너무 많은 상대적 단기 유지 개체가 1세대 수집에서 생존하지만 2세대 전체 수집에서 이를 수집할 수 있다면 메모리 관리 비용이 쉽게 과도해질 수 있습니다. 자세한 내용은 MSDN 웹 사이트의 Rico Mariani의 Performance Tidbits에서 [Mid-life crisis](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/)(중간 수명의 위기) 게시물을 참조하세요.

## <a name="how-to-investigate-a-warning"></a>경고를 조사하는 방법
 [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md) 보고서를 검토하여 애플리케이션의 메모리 할당 패턴을 파악합니다. [개체 수명 뷰](../profiling/object-lifetime-view.md)를 사용하여 프로그램의 어떤 데이터 개체가 2세대로 생존하고 2세대에서 회수되는지 확인합니다. [할당 뷰](../profiling/dotnet-memory-allocations-view.md)를 사용하여 이러한 할당이 시작된 실행 경로를 확인합니다.

 가비지 수집 성능 향상 방법에 대한 자세한 내용은 Microsoft 웹 사이트에서 [가비지 수집기 기본 및 성능 힌트](/previous-versions/dotnet/articles/ms973837(v=msdn.10))를 참조하세요. 자동 가비지 수집의 오버헤드에 대한 자세한 내용은 [Large Object Heap Uncovered](https://msdn.microsoft.com/magazine/cc534993.aspx)(대형 개체 힙 살펴보기)를 참조하세요.
