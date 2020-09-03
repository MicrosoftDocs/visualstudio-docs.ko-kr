---
title: 'CA1054: URI 매개 변수는 문자열이 면 안 됩니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: babef652bbfa55d6549cf0e43ddae0920b3ff302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539492"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: URI 매개 변수는 문자열이면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식이 "uri", "Uri", "urn", "Urn", "url" 또는 "Url"을 포함 하는 문자열 매개 변수를 포함 하는 메서드를 선언 합니다 .이 형식은 매개 변수를 사용 하는 해당 오버 로드를 선언 하지 않습니다 <xref:System.Uri?displayProperty=fullName> .

## <a name="rule-description"></a>규칙 설명
 이 규칙은 카멜식 대/소문자 규칙을 기반으로 매개 변수 이름을 토큰으로 분할 하 고 각 토큰이 "uri", "Uri", "urn", "Urn", "url" 또는 "Url"과 일치 하는지 확인 합니다. 일치 하는 항목이 있는 경우 규칙은 매개 변수가 URI (uniform resource identifier)를 나타내는 것으로 가정 합니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. 메서드가 URI의 문자열 표현을 사용 하는 경우 클래스의 인스턴스를 사용 하는 해당 오버 로드를 제공 해야 <xref:System.Uri> 합니다 .이 클래스는 안전 하 고 안전한 방식으로 이러한 서비스를 제공 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 매개 변수를 형식으로 변경 <xref:System.Uri> 합니다 .이는 주요 변경 내용입니다. 또는 매개 변수를 사용 하는 메서드의 오버 로드를 제공 <xref:System.Uri> 합니다 .이는 주요 변경 내용입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 매개 변수가 URI를 나타내지 않는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예
 다음 예제에서는 `ErrorProne` 이 규칙을 위반 하는 형식 및 `SaferWay` 규칙을 충족 하는 형식을 보여 줍니다.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1056: URI 속성은 문자열이면 안 됩니다.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: URI 반환 값은 문자열이면 안 됩니다.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: 문자열 대신 System.Uri 개체를 전달하세요.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: 문자열 URI 오버로드는 System.Uri 오버로드를 호출합니다.](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
