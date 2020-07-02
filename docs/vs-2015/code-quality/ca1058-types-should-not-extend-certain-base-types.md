---
title: 'CA1058: 형식은 특정 기본 형식을 확장 하면 안 됩니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8e267b1e6203759efc91936a3b13059368a3862
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545394"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: 형식은 특정 기본 형식을 확장하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식이 특정 기본 형식을 확장합니다. 현재이 규칙은 다음 형식에서 파생 되는 형식을 보고 합니다.

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]버전 1의 경우에서 새 예외를 파생 시키는 것이 <xref:System.ApplicationException> 좋습니다. 권장 사항이 변경 되 고 새 예외는 <xref:System.Exception?displayProperty=fullName> 네임 스페이스의 서브 클래스 중 하나에서 파생 되어야 합니다 <xref:System> .

 <xref:System.Xml.XmlDocument>기본 개체 모델 또는 데이터 원본의 XML 뷰를 만들려는 경우의 서브 클래스를 만들지 마십시오.

### <a name="non-generic-collections"></a>제네릭이 아닌 컬렉션
 가능 하면 언제 든 지 및/또는 제네릭 컬렉션을 확장 하십시오. 이전에 제공 하지 않는 한 코드에서 제네릭이 아닌 컬렉션을 확장 하지 마십시오.

 **잘못 된 사용 예**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **올바른 사용법의 예**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 다른 기본 형식 또는 제네릭 컬렉션에서 형식을 파생 시킵니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 위반에 대해이 규칙에서 경고를 표시 하지 마십시오 <xref:System.ApplicationException> . 위반에 대해이 규칙에서 경고를 표시 하지 않는 것이 안전 <xref:System.Xml.XmlDocument> 합니다. 코드가 이전에 릴리스된 경우 제네릭이 아닌 컬렉션에 대 한 경고를 표시 하지 않는 것이 안전 합니다.
