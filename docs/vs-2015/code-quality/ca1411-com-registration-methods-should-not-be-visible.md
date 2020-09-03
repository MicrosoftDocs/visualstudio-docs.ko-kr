---
title: 'CA1411: COM 등록 메서드는 노출 되지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f001a2bb4920ebfb3f5cff3745639bd346a0a920
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540143"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: COM 등록 메서드는 노출되면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 또는 특성으로 표시 된 메서드는 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 외부에서 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 볼 수 있습니다.

## <a name="rule-description"></a>규칙 설명
 COM (구성 요소 개체 모델)을 사용 하 여 어셈블리를 등록 하면 어셈블리의 각 COM 노출 형식에 대해 레지스트리에 항목이 추가 됩니다. 및 특성으로 표시 된 메서드 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 는 각각 등록 및 등록 취소 프로세스 중에 호출 되어 이러한 형식의 등록/등록 취소와 관련 된 사용자 코드를 실행 합니다. 이 코드는 이러한 프로세스 외부에서 호출 해서는 안 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드의 액세스 가능성을 `private` 또는 `internal` ( `Friend` 의 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 경우)로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 규칙을 위반 하는 두 개의 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1410: COM 등록 메서드는 일치해야 합니다.](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>관련 항목
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[COMRegasm.exe에 어셈블리 등록](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [(어셈블리 등록 도구)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
