---
title: DA0010 - GetHashCode의 부담이 큽니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8f94277822d1fcd4210f0f8d79591fc4e2ed3d9e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520681"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: GetHashCode의 부담이 큽니다.

|항목|값|
|-|-|
|규칙 ID|DA0010|
|범주|.NET Framework 사용|
|프로파일링 방법|샘플링<br /><br /> .NET 메모리|
|메시지|GetHashCode 함수는 정리되어야 하며 메모리를 할당하면 안 됩니다. 가능한 경우 해시 코드 함수의 복잡성을 줄입니다.|
|메시지 유형|경고|

## <a name="cause"></a>원인
 해당 형식의 GetHashCode 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지하거나 메서드가 메모리를 할당합니다.

## <a name="rule-description"></a>규칙 설명
 해싱은 큰 컬렉션에서 특정 항목을 신속하게 찾기 위한 기술입니다. 해시 테이블은 클 수 있으며 속도가 빠른 액세스를 지원해야 하므로 해시 테이블이 효율적이어야 합니다. 이 요구 사항의 시사점은 .NET Framework의 GetHashCode 메서드는 메모리를 할당하지 않아야 한다는 것입니다. 메모리 할당은 가비지 수집기의 부하를 증가시키고 할당 요청으로 인해 가비지 수집을 실행하는 것이 필요할 경우 잠재적 지연에 메서드를 노출합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 메서드의 복잡성을 줄이세요.
