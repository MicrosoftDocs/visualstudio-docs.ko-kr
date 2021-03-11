---
title: DA0011 - CompareTo의 부담이 큽니다. | Microsoft Docs
description: 해당 형식의 CompareTo 메서드가 부담이 크거나 메모리를 할당합니다.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 91219bed2ca0e8b4bbc28825e1505b9d5f78bbc8
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466156"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo의 부담이 큽니다.

|항목|값|
|-|-|
|규칙 ID|DA0011|
|범주|.NET Framework 사용|
|프로파일링 방법|샘플링<br /><br /> .NET 메모리|
|메시지|CompareTo 함수는 정리되어야 하며 메모리를 할당하면 안 됩니다. 가능한 경우 CompareTo 함수의 복잡성을 줄입니다.|
|규칙 유형|경고|

## <a name="cause"></a>원인
 해당 형식의 CompareTo 메서드가 부담이 크거나 메모리를 할당합니다.

## <a name="rule-description"></a>규칙 설명
 CompareTo 메서드는 효율적이어야 하며 메모리를 할당하지 않아야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 CompareTo 메서드의 복잡성을 줄이세요.
