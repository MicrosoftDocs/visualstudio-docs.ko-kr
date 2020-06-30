---
title: 'CA1004: 제네릭 메서드는 형식 매개 변수를 제공 해야 합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e7a96c95313ffee82448e3485c90868c8103814a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539804"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: 제네릭 메서드는 형식 매개 변수를 제공해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 제네릭 메서드의 매개 변수 시그니처에는 메서드의 모든 형식 매개 변수에 해당 하는 형식이 포함 되어 있지 않습니다.

## <a name="rule-description"></a>규칙 설명
 제네릭 메서드의 형식 인수가 형식 인수를 명시적으로 지정하는 대신 메서드로 전달된 인수의 형식에 따라 결정되는 방식을 유추라고 합니다. 유추를 사용하려면 제네릭 메서드의 매개 변수 시그니처에 메서드에 대한 형식 매개 변수와 같은 형식의 매개 변수가 포함되어야 합니다. 이 경우 형식 인수는 지정할 필요가 없습니다. 모든 형식 매개 변수에 대해 유추를 사용 하는 경우 제네릭 및 제네릭이 아닌 인스턴스 메서드를 호출 하는 구문은 동일 합니다. 이렇게 하면 제네릭 메서드의 유용성이 간소화 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 매개 변수 시그니처에 메서드의 각 형식 매개 변수에 대해 동일한 형식이 포함 되도록 디자인을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 쉽게 이해 하 고 사용할 수 있는 구문에서 제네릭을 제공 하면 새 라이브러리의 도입 률을 배우고 늘리는 데 필요한 시간이 단축 됩니다.

## <a name="example"></a>예제
 다음 예제에서는 두 개의 제네릭 메서드를 호출 하는 구문을 보여 줍니다. 에 대 한 형식 인수가 `InferredTypeArgument` 유추 되 고에 대 한 형식 인수를 `NotInferredTypeArgument` 명시적으로 지정 해야 합니다.

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: 제네릭 목록을 노출하지 마세요.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩하지 마세요.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적합한 제네릭을 사용하세요.](../code-quality/ca1007-use-generics-where-appropriate.md)