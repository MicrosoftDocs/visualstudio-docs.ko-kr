---
title: 'CA1710: 식별자에는 올바른 접미사가 있어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ee7ce7c4e9edad9d941b4a70b2a199a37130e43
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543990"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: 식별자에는 올바른 접미사를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 식별자의 접미사가 잘못 되었습니다.

## <a name="rule-description"></a>규칙 설명
 규칙에 따라 특정 기본 형식을 확장 하거나 특정 인터페이스를 구현 하는 형식의 이름 또는 이러한 형식에서 파생 된 형식에는 기본 형식 또는 인터페이스와 연결 된 접미사가 있습니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

 다음 표에서는 연결 된 접미사가 있는 기본 형식 및 인터페이스를 보여 줍니다.

|기본 형식/인터페이스|접미사|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|특성|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|예외|
|<xref:System.Collections.ICollection?displayProperty=fullName>|컬렉션|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|컬렉션|
|<xref:System.Collections.Queue?displayProperty=fullName>|컬렉션 또는 큐|
|<xref:System.Collections.Stack?displayProperty=fullName>|컬렉션 또는 스택|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|컬렉션|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|데이터 세트|
|<xref:System.Data.DataTable?displayProperty=fullName>|컬렉션 또는 DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|STREAM|
|<xref:System.Security.IPermission?displayProperty=fullName>|사용 권한|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|조건|
|이벤트 처리기 대리자입니다.|이벤트 처리기|

 및를 구현 하는 형식은 <xref:System.Collections.ICollection> 사전, 스택 또는 큐와 같은 일반화 된 형식의 데이터 구조 이며, 해당 형식의 용도에 대 한 의미 있는 정보를 제공 하는 허용 되는 이름입니다.

 및를 구현 하는 형식과 <xref:System.Collections.ICollection> 특정 항목의 컬렉션인 이름은 ' collection ' 이라는 단어로 끝납니다. 예를 들어 개체의 컬렉션은 <xref:System.Collections.Queue> 이름이 ' QueueCollection '입니다. ' Collection ' 접미사는 `foreach` ( `For Each` in) 문을 사용 하 여 컬렉션의 멤버를 열거할 수 있음을 나타냅니다 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

 을 구현 하는 형식은 <xref:System.Collections.IDictionary> 형식이 또는를 구현 하는 경우에도 ' Dictionary ' 라는 단어로 끝나는 이름입니다 <xref:System.Collections.IEnumerable> <xref:System.Collections.ICollection> . 사용자는 ' 컬렉션 ' 및 ' 사전 ' 접미사 명명 규칙을 사용 하 여 다음 두 열거형 패턴을 구분할 수 있습니다.

 ' Collection ' 접미사가 있는 형식은이 열거형 패턴을 따릅니다.

```
foreach(SomeType x in SomeCollection) { }
```

 ' Dictionary ' 접미사가 있는 형식은이 열거형 패턴을 따릅니다.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 개체는 개체의 컬렉션으로 구성 되며, 개체의 컬렉션으로 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 구성 <xref:System.Data.DataColumn?displayProperty=fullName> 됩니다 <xref:System.Data.DataRow?displayProperty=fullName> . 이러한 컬렉션 <xref:System.Collections.ICollection> 은 기본 클래스를 통해 구현 <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 올바른 용어를 접미사로 사용 하도록 형식의 이름을 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식이 확장 될 수 있거나 임의의 다양 한 항목 집합을 포함 하는 일반화 된 데이터 구조인 경우 ' Collection ' 접미사를 사용 하 여 경고를 표시 하지 않는 것이 안전 합니다. 이 경우에는 구현, 성능 또는 데이터 구조의 기타 특성에 대 한 의미 있는 정보를 제공 하는 이름이 적절 한 것일 수 있습니다 (예: BinaryTree). 형식이 특정 형식의 컬렉션을 나타내는 경우 (예: StringCollection) 접미사는 문을 사용 하 여 형식을 열거할 수 있음을 나타내므로이 규칙에서 경고를 표시 하지 마십시오 `foreach` .

 다른 접미사의 경우에는이 규칙의 경고를 표시 하지 마십시오. 접미사를 사용 하면 형식 이름에서 의도 된 용도를 명확 하 게 알 수 있습니다.

## <a name="related-rules"></a>관련 규칙
 [CA1711: 식별자에는 올바른 접미사를 사용해야 합니다.](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>참고 항목
 [특성](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: 이벤트 및 대리자](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
