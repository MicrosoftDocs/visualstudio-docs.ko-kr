---
title: 'CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 00992fc71f07d820620cecbe57eac4f3b3702701
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539648"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: 멤버 시그니처에 제네릭 형식을 중첩하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 노출 되는 멤버에는 중첩 된 형식 인수를 포함 하는 시그니처가 있습니다.

## <a name="rule-description"></a>규칙 설명
 중첩된 형식 인수는 제네릭 형식의 인수입니다. 시그니처에 중첩된 형식 인수가 포함되어 있는 멤버를 호출하려면 제네릭 형식 하나를 인스턴스화하고 이 형식을 두 번째 제네릭 형식의 생성자에 전달해야 합니다. 이 경우 복잡한 프로시저와 구문이 필요하므로 이 방법을 피해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 디자인을 변경 하 여 중첩 된 형식 인수를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 쉽게 이해 하 고 사용할 수 있는 구문에서 제네릭을 제공 하면 새 라이브러리의 도입 률을 배우고 늘리는 데 필요한 시간이 단축 됩니다.

## <a name="example"></a>예
 다음 예제에서는 규칙을 위반 하는 메서드와 위반 메서드를 호출 하는 데 필요한 구문을 보여 줍니다.

 [!code-csharp[FxCop.Design.NestedGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/cs/FxCop.Design.NestedGenerics.cs#1)]
 [!code-vb[FxCop.Design.NestedGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/vb/FxCop.Design.NestedGenerics.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: 제네릭 목록을 노출하지 마세요.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: 제네릭 메서드는 형식 매개 변수를 제공해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적합한 제네릭을 사용하세요.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>관련 항목
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
