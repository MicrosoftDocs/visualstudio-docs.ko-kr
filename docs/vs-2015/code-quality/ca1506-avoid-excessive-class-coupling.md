---
title: 'CA1506: 과도 한 클래스 결합 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 07f19cb9d4aa2ed118898a1816092479cbd16565
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545706"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: 클래스를 지나치게 많이 결합하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|범주|Microsoft 유지 관리|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식 또는 메서드가 다른 많은 형식과 결합 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 형식 또는 메서드에 들어 있는 고유한 형식 참조의 개수를 계산하여 클래스 결합을 측정합니다.

 클래스 결합 수준이 높은 형식과 메서드는 관리 하기 어려울 수 있습니다. 낮은 결합 및 높은 응집을 나타내는 형식 및 메서드를 포함 하는 것이 좋습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 위반 문제를 해결 하려면 형식이 나 메서드를 다시 디자인 하 여 결합 된 형식의 수를 줄이십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식 또는 메서드가 다른 형식에 대 한 많은 종속성에도 불구 하 고 계속 유지 관리 되는 것으로 간주 되는 경우이 경고를 제외 합니다.

## <a name="see-also"></a>참고 항목
 [관리 코드의 복잡성 및 유지 관리 용이성을 측정 하는](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [유지 관리 경고](../code-quality/maintainability-warnings.md)
