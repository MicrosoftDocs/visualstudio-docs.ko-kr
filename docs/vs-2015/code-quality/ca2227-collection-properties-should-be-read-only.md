---
title: 'CA2227: 컬렉션 속성은 읽기 전용 이어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17c4e2336a5c8bd8905d857dc8189a11f9fb6181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540532"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: 컬렉션 속성은 읽기 전용이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|범주|Microsoft 사용|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 쓰기 가능 속성은을 구현 하는 형식입니다 <xref:System.Collections.ICollection?displayProperty=fullName> . 배열, 인덱서 (이름이 ' Item ' 인 속성) 및 권한 집합은 규칙에서 무시 됩니다.

## <a name="rule-description"></a>규칙 설명
 쓰기 가능한 컬렉션 속성을 통해 사용자는 컬렉션을 완전히 다른 컬렉션으로 바꿀 수 있습니다. 읽기 전용 속성은 컬렉션을 바꾸지 못하도록 하지만 개별 멤버를 설정하는 것은 여전히 가능합니다. 컬렉션을 바꾸는 것이 목표 인 경우 기본 디자인 패턴은 컬렉션에서 모든 요소를 제거 하는 메서드와 컬렉션을 다시 채우는 메서드를 포함 하는 것입니다. <xref:System.Collections.ArrayList.Clear%2A> <xref:System.Collections.ArrayList.AddRange%2A> 이 패턴의 예는 클래스의 및 메서드를 참조 하세요 <xref:System.Collections.ArrayList?displayProperty=fullName> .

 이진 및 XML serialization은 모두 컬렉션인 읽기 전용 속성을 지원 합니다. 클래스에는 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 을 구현 하 고 serialize 할 수 있도록 하는 형식에 대 한 특정 요구 사항이 있습니다 <xref:System.Collections.ICollection> <xref:System.Collections.IEnumerable?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 속성을 읽기 전용으로 설정 하 고, 디자인에 필요한 경우 컬렉션을 지우고 다시 채우는 메서드를 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 쓰기 가능한 컬렉션 속성이 있는 형식을 보여 주고 컬렉션을 직접 바꿀 수 있는 방법을 보여 줍니다. 또한 및 메서드를 사용 하 여 읽기 전용 컬렉션 속성을 대체 하는 기본 설정 방식이 `Clear` `AddRange` 표시 됩니다.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1819: 속성은 배열을 반환해서는 안 됩니다.](../code-quality/ca1819-properties-should-not-return-arrays.md)
