---
title: 'CA2117: APTCA 형식은 APTCA 기본 형식만 확장 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 90c1f66f36fc689ee077ec66f154487d65ee13a1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543613"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 특성이 있는 어셈블리의 public 또는 protected 형식이 특성이 없는 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 어셈블리에 선언 된 형식에서 상속 됩니다.

## <a name="rule-description"></a>규칙 설명
 기본적으로 강력한 이름을 가진 어셈블리에서 public 또는 protected 형식은 완전 신뢰에 대 한 [상속 요청](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) 에 의해 암시적으로 보호 됩니다. (APTCA) 특성으로 표시 된 강력한 이름의 어셈블리 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 에는이 보호가 포함 되지 않습니다. 특성은 상속 요청을 사용 하지 않도록 설정 합니다. 이렇게 하면 어셈블리에 선언 된 노출 된 형식이 완전 신뢰가 없는 형식에 의해 상속 가능 하 게 됩니다.

 완전히 신뢰할 수 있는 어셈블리에 APTCA 특성이 있고 어셈블리의 형식이 부분적으로 신뢰할 수 있는 호출자를 허용 하지 않는 형식에서 상속 되는 경우 보안을 악용할 수 있습니다. 두 형식이 `T1` `T2` 다음 조건을 충족 하는 경우 악성 호출자는 형식을 사용 하 여를 `T1` 보호 하는 암시적 완전 신뢰 상속 요청을 무시할 수 있습니다 `T2` .

- `T1`는 APTCA 특성이 있는 완전히 신뢰할 수 있는 어셈블리에 선언 된 공용 형식입니다.

- `T1`어셈블리 외부의 형식에서 상속 `T2` 됩니다.

- `T2`의 어셈블리에 APTCA 특성이 없으므로 부분적으로 신뢰할 수 있는 어셈블리의 형식으로 상속 될 수 없습니다.

  부분적으로 신뢰할 수 있는 형식은에서 `X` 상속할 수 있습니다 `T1` . 그러면에서 선언 된 상속 된 멤버에 액세스할 수 있습니다 `T2` . 에는 `T2` APTCA 특성이 없으므로 직계 파생 형식 ( `T1` )은 완전 신뢰에 대 한 상속 수요를 충족 해야 합니다. `T1` 는 완전 신뢰를 가지 므로이 검사를 충족 합니다. 는 `X` `T2` 신뢰할 수 없는 서브클래싱 으로부터 보호 하는 상속 수요를 충족 하지 않기 때문에 보안상 위험할 수 있습니다. 이러한 이유로 APTCA 특성이 있는 형식은 특성이 없는 형식을 확장 하면 안 됩니다.

  또 다른 보안 문제 및 보다 일반적인 문제는 파생 형식 ( `T1` )이 프로그래머 오류를 통해 완전 신뢰가 필요한 형식 ()에서 보호 된 멤버를 노출 하는 것입니다 `T2` . 이 문제가 발생 하면 신뢰할 수 없는 호출자는 완전히 신뢰할 수 있는 형식에만 사용할 수 있는 정보에 액세스할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 위반에 의해 보고 된 형식이 APTCA 특성이 필요 없는 어셈블리에 있는 경우이를 제거 합니다.

 APTCA 특성이 필요한 경우 형식에 완전 신뢰를 위한 상속 요청을 추가 합니다. 이렇게 하면 신뢰할 수 없는 형식에의 한 상속 으로부터 보호 됩니다.

 위반에서 보고 하는 기본 형식의 어셈블리에 APTCA 특성을 추가 하 여 위반 문제를 해결할 수 있습니다. 어셈블리 및 어셈블리에 종속 된 모든 코드의 모든 코드에 대 한 집중적인 보안 검토를 먼저 수행 하지 않고이 작업을 수행 하지 마십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 안전 하 게 표시 하지 않으려면 해당 형식에 의해 노출 된 protected 멤버가 안전 하지 않은 방식으로 사용할 수 있는 중요 한 정보, 작업 또는 리소스에 액세스할 수 있도록 직접 또는 간접적으로 허용 하지 않도록 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 두 개의 어셈블리와 테스트 응용 프로그램을 사용 하 여이 규칙에 의해 검색 된 보안 취약성을 보여 줍니다. 첫 번째 어셈블리는 APTCA 특성을 포함 하지 않으며, 부분적으로 신뢰할 수 있는 형식 (이전 토론에서 표시)으로 상속 될 수 없습니다 `T2` .

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>예제
 이전 설명에서에 표시 되는 두 번째 어셈블리는 `T1` 완전히 신뢰할 수 있으며 부분적으로 신뢰할 수 있는 호출자를 허용 합니다.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>예제
 `X`이전 설명에서에 나타난 테스트 형식은 부분적으로 신뢰할 수 있는 어셈블리에 있습니다.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **Shady 글을 2/22/2003 12:00:00 AM** 
 **테스트: sunny 목초지** 
 **Sunny 목초지 2/22/2003 12:00:00 AM을 소개 합니다.**
## <a name="related-rules"></a>관련 규칙
 [CA2116: APTCA 메서드는 APTCA 메서드만 호출해야 합니다.](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>참고 항목
 [부분적으로 신뢰할 수 있는 코드 상속 요청의 라이브러리를 사용 하 여](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Inheritance Demands](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [부분적으로 신뢰할 수 있는 코드에서 호출할 수 있는 어셈블리 .NET Framework](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
