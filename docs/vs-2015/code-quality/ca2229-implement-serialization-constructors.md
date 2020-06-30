---
title: 'CA2229: serialization 생성자 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba654496d80654f0d9790a01bbc41326f7a5f13e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540493"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: serialization 생성자를 구현하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 형식은 인터페이스를 구현 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 하 고, 대리자 또는 인터페이스가 아니고, 다음 조건 중 하나에 해당 합니다.

- 형식에 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> 개체와 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 개체 (serialization 생성자의 시그니처)를 사용 하는 생성자가 없습니다.

- 형식이 봉인 되지 않고 serialization 생성자의 액세스 한정자가 (family) 보호 되지 않습니다.

- 형식이 sealed이 고 serialization 생성자의 액세스 한정자가 private이 아닙니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 사용자 지정 serialization을 지 원하는 형식과 관련이 있습니다. 인터페이스를 구현 하는 경우 형식이 사용자 지정 serialization을 지원 합니다 <xref:System.Runtime.Serialization.ISerializable> . 메서드를 사용 하 여 serialize 된 개체를 deserialize 하거나 다시 만들려면 serialization 생성자를 사용 해야 합니다 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결하려면 serialization 생성자를 구현합니다. 봉인 클래스의 경우에는 생성자를 private으로 만들고, 그 밖의 경우에는 protected로 만듭니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 규칙 위반을 억제 하지 마십시오. 형식은 deserialize 할 수 없으며 여러 시나리오에서 작동 하지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 충족 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
