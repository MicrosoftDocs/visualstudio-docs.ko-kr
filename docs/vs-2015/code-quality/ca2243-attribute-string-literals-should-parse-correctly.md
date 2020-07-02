---
title: 'CA2243: 특성 문자열 리터럴이 올바르게 구문 분석 되어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535748"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: 특성 문자열 리터럴이 올바르게 구문 분석되어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 특성의 문자열 리터럴 매개 변수는 URL, GUID 또는 버전에 대해 올바르게 구문 분석 되지 않습니다.

## <a name="rule-description"></a>규칙 설명
 특성은에서 파생 되 <xref:System.Attribute?displayProperty=fullName> 고 특성은 컴파일 시간에 사용 되므로 상수 값만 생성자에 전달할 수 있습니다. Url, Guid 및 버전을 나타내야 하는 특성 매개 변수는, 및로 입력할 수 없습니다 <xref:System.Uri?displayProperty=fullName> <xref:System.Guid?displayProperty=fullName> <xref:System.Version?displayProperty=fullName> . 이러한 형식은 상수로 표현할 수 없기 때문입니다. 대신 문자열로 표시 되어야 합니다.

 매개 변수가 문자열로 형식화 되기 때문에 컴파일 시간에 잘못 된 형식의 매개 변수가 전달 될 수 있습니다.

 이 규칙은 명명 추론을 사용 하 여 URI (uniform resource identifier), GUID (Globally Unique Identifier) 또는 버전을 나타내는 매개 변수를 찾고 전달 된 값이 올바른지 확인 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 매개 변수 문자열을 올바른 형식의 URL, GUID 또는 버전으로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 매개 변수가 URL, GUID 또는 버전을 나타내지 않는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 AssemblyFileVersionAttribute의 코드를 보여 줍니다.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 규칙은 다음에 의해 트리거됩니다.

- ' Version '이 포함 된 매개 변수는 System.object로 구문 분석할 수 없습니다.

- ' Guid '를 포함 하 고 system.string으로 구문 분석할 수 없는 매개 변수입니다.

- ' Uri ', ' urn ' 또는 ' u r l '을 포함 하는 매개 변수를 System.uri로 구문 분석할 수 없습니다.

## <a name="see-also"></a>참고 항목
 [CA1054: URI 매개 변수는 문자열이면 안 됩니다.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
