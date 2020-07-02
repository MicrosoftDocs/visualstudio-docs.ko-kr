---
title: 'CA1059: 멤버는 구체적인 특정 형식을 노출 하면 안 됩니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792426615dd78241ade1d38a24ec1f4d5702cede
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545381"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: 멤버는 구체적인 특정 형식을 노출하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 멤버는 구체적인 특정 형식 이거나 해당 매개 변수 또는 반환 값 중 하나를 통해 구체적인 특정 형식을 노출 합니다. 현재이 규칙은 다음과 같은 구체적인 형식의 노출을 보고 합니다.

- <xref:System.Xml.XmlNode?displayProperty=fullName>에서 파생된 형식입니다.

## <a name="rule-description"></a>규칙 설명
 구체적인 형식은 완전히 구현되었기 때문에 인스턴스화할 수 있는 형식을 말합니다. 멤버를 광범위 하 게 사용할 수 있도록 하려면 구체적인 형식을 제안 된 인터페이스로 바꿉니다. 이를 통해 멤버는 인터페이스를 구현 하는 모든 형식을 허용 하거나 인터페이스를 구현 하는 형식이 필요한 위치에 사용할 수 있습니다.

 다음 표에서는 대상으로 지정 된 구체적인 형식 및 제안 된 대체 항목을 보여 줍니다.

|구체적 형식|대체 기능|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> 인터페이스를 사용 하 여 XML 데이터 원본의 특정 구현에서 멤버를 분리 합니다.|

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 구체적인 유형을 제안 된 인터페이스로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 구체적 형식에서 제공 하는 특정 기능이 필요한 경우에는이 규칙에서 메시지를 표시 하지 않는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA1011: 기본 형식을 매개 변수로 전달해 보세요.](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
