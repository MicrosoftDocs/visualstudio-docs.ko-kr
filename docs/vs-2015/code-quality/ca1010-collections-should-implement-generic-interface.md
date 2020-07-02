---
title: 'CA1010: 컬렉션은 제네릭 인터페이스를 구현 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b141d755c717ad6650d2a49c98c2b26547066b7a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545524"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식은 <xref:System.Collections.IEnumerable?displayProperty=fullName> 인터페이스를 구현 하지만 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 인터페이스 및 포함 하는 어셈블리 대상을 구현 하지 않습니다 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] . 이 규칙은를 구현 하는 형식을 무시 <xref:System.Collections.IDictionary?displayProperty=fullName> 합니다.

## <a name="rule-description"></a>규칙 설명
 컬렉션의 유용성을 높이려면 제네릭 컬렉션 인터페이스 중 하나를 구현합니다. 그런 다음 컬렉션을 사용 하 여 다음과 같은 제네릭 컬렉션 형식을 채울 수 있습니다.

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 다음 제네릭 컬렉션 인터페이스 중 하나를 구현 합니다.

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시 하지 않아도 됩니다. 그러나 컬렉션은 더 제한적으로 사용 됩니다.

## <a name="example-violation"></a>위반 예

### <a name="description"></a>설명
 다음 예제에서는 `CollectionBase` 이 규칙을 위반 하는 제네릭이 아닌 클래스에서 파생 되는 클래스 (참조 형식)를 보여 줍니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>주석
 이러한 위반 위반 문제를 해결 하려면 제네릭 인터페이스를 구현 하거나 기본 클래스를 클래스와 같은 제네릭 및 비 제네릭 인터페이스를 이미 구현 하는 형식으로 변경 해야 합니다 `Collection<T>` .

## <a name="fix-by-base-class-change"></a>기본 클래스 변경에의 한 수정

### <a name="description"></a>설명
 다음 예제에서는 컬렉션의 기본 클래스를 제네릭이 아닌 `CollectionBase` 클래스에서 제네릭 `Collection<T>` ( `Collection(Of T)` 의 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) 클래스로 변경 하 여 위반을 수정 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>주석
 이미 릴리스된 클래스의 기본 클래스를 변경 하는 것은 기존 소비자의 주요 변경 내용으로 간주 됩니다.

## <a name="fix-by-interface-implementation"></a>인터페이스 구현에 의해 수정

### <a name="description"></a>설명
 다음 예제에서는 `IEnumerable<T>` , `ICollection<T>` 및 `IList<T>` ( `IEnumerable(Of T)` 의 경우 `ICollection(Of T)` `IList(Of T)` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] )와 같은 제네릭 인터페이스를 구현 하 여 위반을 수정 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: 제네릭 목록을 노출하지 마세요.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩하지 마세요.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드는 형식 매개 변수를 제공해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적합한 제네릭을 사용하세요.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>참고 항목
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
