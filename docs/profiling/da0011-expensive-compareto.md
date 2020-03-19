---
title: 'DA0011: CompareTo의 부담이 큽니다. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779430"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo의 부담이 큽니다.

|||
|-|-|
|규칙 ID|DA0011|
|Category|.NET Framework 사용|
|프로파일링 방법|샘플링<br /><br /> .NET 메모리|
|메시지|CompareTo 함수는 정리되어야 하며 메모리를 할당하면 안 됩니다. 가능한 경우 CompareTo 함수의 복잡성을 줄입니다.|
|규칙 유형|Warning|

## <a name="cause"></a>원인
 해당 형식의 CompareTo 메서드가 부담이 크거나 메모리를 할당합니다.

## <a name="rule-description"></a>규칙 설명
 CompareTo 메서드는 효율적이어야 하며 메모리를 할당하지 않아야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 CompareTo 메서드의 복잡성을 줄이세요.
