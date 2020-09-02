---
title: 'CA1502: 과도 한 복잡성 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5da2e2bf26bb1894987caa8b748181d952bd7c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547838"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: 지나치게 복잡하게 만들지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|범주|Microsoft 유지 관리|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드에 과도 한 순환 복잡성이 있습니다.

## <a name="rule-description"></a>규칙 설명
 *순환 복잡성* 은 조건부 분기의 수와 복잡성에 따라 결정 되는 메서드를 통해 선형 독립적 경로의 수를 측정 합니다. 일반적으로 낮은 순환 복잡성은 이해, 테스트 및 유지 관리가 쉬운 방법을 나타냅니다. 순환 복잡성은 메서드의 제어 흐름 그래프에서 계산 되며 다음과 같이 제공 됩니다.

 순환 복잡성 = 가장자리 수-노드 수 + 1

 여기서 노드는 논리 분기를 나타내고 가장자리는 노드 사이의 선을 나타냅니다.

 이 규칙은 순환 복잡성이 25 이상일 때 위반을 보고 합니다.

 [관리 코드의 복잡성 및 유지 관리 용이성을 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)하 여 코드 메트릭에 대해 자세히 알아볼 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드를 리팩터링하여 순환 복잡성을 줄입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 복잡성을 쉽게 줄이고 메서드를 이해, 테스트 및 유지 관리할 수 있는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 특히, large (in) 문을 포함 하는 메서드는 `switch` `Select` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 제외의 후보입니다. 코드 베이스를 개발 주기에서 늦게 불안정 하거나 이전에 제공 된 코드에서 예기치 않은 런타임 동작이 발생 하는 위험이 코드를 리팩터링 하는 유지 관리 이점 보다 클 수 있습니다.

## <a name="how-cyclomatic-complexity-is-calculated"></a>순환 복잡성을 계산 하는 방법
 순환 복잡성은 다음에 1을 더하여 계산 됩니다.

- 분기 수 (예: `if` , `while` 및 `do` )

- `case`의 문 수`switch`

  다음 예제에서는 다양 한 순환 복잡성이 있는 메서드를 보여 줍니다.

## <a name="example"></a>예
 **순환 복잡성 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>예
 **순환 복잡성 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>예
 **순환 복잡성 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>예
 **순환 복잡성 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>관련 규칙
 [CA1501: 상속성을 너무 많이 사용하지 마세요.](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>관련 항목
 [관리 코드의 복잡성 및 유지 관리 용이성 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
