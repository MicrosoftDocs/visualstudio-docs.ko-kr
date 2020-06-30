---
title: 'CA2240: ISerializable을 올바르게 구현 하십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 217f95b7d3658db107fc482040686eea9ee47604
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543665"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable을 올바르게 구현하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식은 인터페이스에 할당할 수 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 있으며 다음 조건 중 하나에 해당 합니다.

- 형식은를 상속 하지만 메서드를 재정의 하지 않으며 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 형식에서 특성으로 표시 되지 않은 인스턴스 필드를 선언 합니다 <xref:System.NonSerializedAttribute?displayProperty=fullName> .

- 형식이 sealed가 아니고 형식이 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 외부적으로 표시 되지 않고 재정의할 수 있는 메서드를 구현 합니다.

## <a name="rule-description"></a>규칙 설명
 인터페이스를 상속 하는 형식에서 선언 된 인스턴스 필드 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 는 serialization 프로세스에 자동으로 포함 되지 않습니다. 필드를 포함 하려면 형식이 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 메서드 및 serialization 생성자를 구현 해야 합니다. 필드를 serialize 하지 않아야 하는 경우 <xref:System.NonSerializedAttribute> 필드에 특성을 적용 하 여 결정을 명시적으로 지정 합니다.

 봉인 되지 않은 형식에서 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 메서드의 구현은 외부에서 볼 수 있어야 합니다. 따라서 메서드는 파생 형식에 의해 호출 될 수 있으며 재정의할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드를 표시 하 고 재정의 가능 하 게 설정 하 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 고 모든 인스턴스 필드가 serialization 프로세스에 포함 되거나 명시적으로 특성으로 표시 되도록 합니다 <xref:System.NonSerializedAttribute> .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 serialize 할 수 있는 두 가지 형식을 보여 줍니다.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>예제
 다음 예제에서는 [GetObjectData]의 재정의 가능 구현을 제공 하 여 두 가지 이전 위반을 수정 합니다.<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->)를 제공 하 고 다음의 구현을 제공 합니다. <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> Library 클래스에서

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: serialization 메서드를 올바르게 구현하십시오.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: 선택적 필드에 deserialization 메서드를 제공하세요.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: serialization 생성자를 안전하게 하세요.](../code-quality/ca2120-secure-serialization-constructors.md)
