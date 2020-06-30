---
title: 'CA2116: APTCA 메서드는 APTCA 메서드만 호출 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 115c0e733716994ba463eada938f8ff908612d0f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547760"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA 메서드는 APTCA 메서드만 호출해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 특성을 사용 하는 어셈블리의 메서드가 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 특성을 포함 하지 않는 어셈블리의 메서드를 호출 합니다.

## <a name="rule-description"></a>규칙 설명
 기본적으로 강력한 이름의 어셈블리에서 public 또는 protected 메서드는 완전 신뢰에 대 한 [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) 에 의해 암시적으로 보호 됩니다. 완전히 신뢰할 수 있는 호출자만 강력한 이름의 어셈블리에 액세스할 수 있습니다. (APTCA) 특성으로 표시 된 강력한 이름의 어셈블리 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 에는이 보호가 포함 되지 않습니다. 특성은 링크 요청을 사용 하지 않도록 설정 하 여 인트라넷 또는 인터넷에서 실행 되는 코드와 같이 완전 신뢰가 없는 호출자가 어셈블리에 액세스할 수 있도록 합니다.

 완전히 신뢰할 수 있는 어셈블리에 APTCA 특성이 있고 어셈블리에서 부분적으로 신뢰할 수 있는 호출자를 허용 하지 않는 다른 어셈블리의 코드를 실행 하는 경우 보안을 악용할 수 있습니다. 두 가지 방법 `M1` 및가 `M2` 다음 조건을 충족 하는 경우 악성 호출자는 메서드를 사용 하 여를 `M1` 보호 하는 암시적 완전 신뢰 링크 요청을 무시할 수 있습니다 `M2` .

- `M1`는 APTCA 특성이 있는 완전히 신뢰할 수 있는 어셈블리에 선언 된 공용 메서드입니다.

- `M1`어셈블리 외부에서 메서드를 호출 `M2` `M1` 합니다.

- `M2`의 어셈블리에 APTCA 특성이 없으므로 부분적으로 신뢰할 수 있는 호출자 대신 또는에서 실행 해서는 안 됩니다.

  부분적으로 신뢰할 수 있는 호출자는 `X` 메서드를 호출 `M1` 하 여 `M1` 를 호출할 수 있습니다 `M2` . 에는 `M2` APTCA 특성이 없으므로 해당 직계 호출자 ( `M1` )는 완전 신뢰에 대 한 링크 요구를 충족 해야 합니다. `M1` 는 완전 신뢰를 가지 므로이 검사를 충족 합니다. 는 `X` 신뢰할 수 없는 호출자 로부터 보호 하는 링크 요구를 충족 하지 않기 때문에 보안상 위험할 수 `M2` 있습니다. 따라서 APTCA 특성이 있는 메서드는 특성이 없는 메서드를 호출 해서는 안 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 APCTA 특성이 필요한 경우 요청을 사용 하 여 완전 신뢰 어셈블리로를 호출 하는 메서드를 보호 합니다. 필요한 정확한 권한은 메서드에 의해 노출 되는 기능에 따라 달라 집니다. 가능 하면 완전 신뢰 요청을 통해 메서드를 보호 하 여 기본 기능이 부분적으로 신뢰할 수 있는 호출자에 게 노출 되지 않도록 합니다. 가능 하지 않은 경우 노출 된 기능을 효과적으로 보호 하는 권한 집합을 선택 합니다. 요청에 대 한 자세한 내용은 [요청](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)을 참조 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 안전 하 게 표시 하지 않으려면 메서드에서 노출 하는 기능이 호출자에 게 직접 또는 간접적으로 호출자가 안전 하 게 사용할 수 있는 중요 한 정보, 작업 또는 리소스에 액세스할 수 없도록 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 두 개의 어셈블리와 테스트 응용 프로그램을 사용 하 여이 규칙에 의해 검색 된 보안 취약성을 보여 줍니다. 첫 번째 어셈블리에는 APTCA 특성이 없으므로 부분적으로 신뢰할 수 있는 호출자 (이전 토론에서 표시)에 액세스할 수 없습니다 `M2` .

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>예제
 두 번째 어셈블리는 완전히 신뢰할 수 있으며, 부분적으로 신뢰할 수 있는 호출자 (이전 토론에서로 표시 됨)를 허용 `M1` 합니다.

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>예제
 이전 토론에서로 표시 된 테스트 응용 프로그램은 `X` 부분적으로 신뢰할 수 있습니다.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **완전 신뢰 요청: 요청이 실패 했습니다.** 
 **ClassRequiringFullTrust가 호출 되었습니다.**
## <a name="related-rules"></a>관련 규칙
 [CA2117: APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>참고 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) .NET Framework 부분적으로 [신뢰할 수 있는 코드에서 라이브러리를 사용 하 여](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Demands](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [부분적으로 신뢰할 수 있는 코드에서 호출할 수 있는 어셈블리](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [연결 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
