---
title: 'CA1410: COM 등록 메서드는 일치 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 43767ce04b32440a5c6753f5bfcabb91487c1232
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546707"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: COM 등록 메서드는 일치해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|범주|Microsoft.Interoperability|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식은 특성으로 표시 된 메서드를 선언 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 하지만 특성으로 표시 된 메서드를 선언 하지는 않습니다 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>규칙 설명
 COM (구성 요소 개체 모델) 클라이언트가 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식을 만들려면 먼저 형식을 등록 해야 합니다. 사용할 수 있는 경우 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 사용자 지정 코드를 실행 하기 위해 등록 프로세스 중에 특성으로 표시 된 메서드가 호출 됩니다. 특성으로 표시 된 해당 메서드는 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 등록 취소 프로세스 중에 호출 되어 등록 메서드의 작업을 되돌립니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 해당 등록 또는 등록 취소 메서드를 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다. 주석 처리 된 코드는 위반에 대 한 수정 사항을 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1411: COM 등록 메서드는 노출되면 안 됩니다.](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[COMRegasm.exe에 어셈블리 등록](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [(어셈블리 등록 도구)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
