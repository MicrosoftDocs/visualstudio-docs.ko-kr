---
title: 'CA1414: 부울 P-Invoke 인수를 MarshalAs로 표시 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 783f7fad05cad18efea2f83b6d76c4c9e644f119
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548384"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: 부울 P/Invoke 인수를 MarshalAs로 표시하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 플랫폼 호출 메서드 선언에 <xref:System.Boolean?displayProperty=fullName> 매개 변수 또는 반환 값이 포함 되어 있지만 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> 특성이 매개 변수 또는 반환 값에 적용 되지 않습니다.

## <a name="rule-description"></a>규칙 설명
 플랫폼 호출 메서드는 비관리 코드에 액세스 하 고 또는의 키워드를 사용 하 여 정의 됩니다 `Declare` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . <xref:System.Runtime.InteropServices.MarshalAsAttribute>관리 코드와 비관리 코드 간에 데이터 형식을 변환 하는 데 사용 되는 마샬링 동작을 지정 합니다. 및와 같은 많은 단순 데이터 형식은 <xref:System.Byte?displayProperty=fullName> <xref:System.Int32?displayProperty=fullName> 비관리 코드에서 단일 표현을 가지 며 마샬링 동작을 지정 하지 않아도 됩니다. 공용 언어 런타임에서 올바른 동작을 자동으로 제공 합니다.

 <xref:System.Boolean>데이터 형식은 비관리 코드에 여러 개의 표현이 있습니다. 을 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 지정 하지 않은 경우 데이터 형식에 대 한 기본 마샬링 동작은 <xref:System.Boolean> <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> 입니다. 이것은 모든 상황에서 적절 하지 않은 32 비트 정수입니다. 관리 되지 않는 메서드에 필요한 부울 표현을 결정 하 고 적절 하 게 일치 해야 합니다 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . Unmanagedtype.lpwstr은 항상 4 바이트인 Win32 BOOL 형식입니다. Unmanagedtype.lpwstr는 c + + `bool` 또는 다른 1 바이트 형식에 사용 해야 합니다. 자세한 내용은 [부울 형식에 대 한 기본 마샬링](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)을 참조 하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Boolean> 매개 변수 또는 반환 값에을 적용 합니다. 특성의 값을 적절 한로 설정 합니다 <xref:System.Runtime.InteropServices.UnmanagedType> .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 기본 마샬링 동작이 적절 한 경우에도 동작이 명시적으로 지정 되 면 코드를 보다 쉽게 유지할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 적절 한 특성으로 표시 된 두 개의 플랫폼 호출 메서드를 보여 줍니다 <xref:System.Runtime.InteropServices.MarshalAsAttribute> .

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1901: P/Invoke 선언은 이식 가능 해야 합니다.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[부울 형식에 대 한 기본 마샬링](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
