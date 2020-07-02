---
title: 'CA2231: 오버 로드 연산자는 ValueType을 재정의 하는 것과 같습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f01495e4238461d0b1dfe5a13a208b528df1581f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540298"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 값 형식이를 재정의 <xref:System.Object.Equals%2A?displayProperty=fullName> 하지만 같음 연산자를 구현 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 대부분의 프로그래밍 언어에는 값 형식에 대 한 같음 연산자 (= =)의 기본 구현이 없습니다. 프로그래밍 언어가 연산자 오버 로드를 지 원하는 경우 같음 연산자를 구현 하는 것을 고려해 야 합니다. 해당 동작은의 동작과 동일 해야 합니다 <xref:System.Object.Equals%2A> .

 같음 연산자의 오버 로드 된 구현에서는 기본 같음 연산자를 사용할 수 없습니다. 이렇게 하면 스택 오버플로가 발생 합니다. 같음 연산자를 구현 하려면 구현에서 개체. Equals 메서드를 사용 합니다. 예를 들면 다음과 같습니다.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 같음 연산자를 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시 하지 않아도 됩니다. 그러나 가능 하면 같음 연산자를 제공 하는 것이 좋습니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 형식을 정의 합니다.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode/cs/FxCop.Usage.EqualsGetHashCode.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1046: 참조 형식에 같음 연산자를 오버로드하지 마세요.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: 연산자 오버로드에는 명명된 대체 항목이 있습니다.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: 연산자에는 대칭 오버로드가 있어야 합니다.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: 같음 연산자를 오버로드할 때 Equals를 재정의하세요.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Equals를 재정할 때 GetHashCode를 재정의하세요.](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Object.Equals%2A?displayProperty=fullName>
