---
title: 'CA1415: P를 올바르게 선언 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9931d29c818d95785146558637c32237e2c5276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547851"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invoke를 올바르게 선언하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|범주|Microsoft.Interoperability|
|변경 수준|분리 안 됨-매개 변수를 선언 하는 P/Invoke를 어셈블리 외부에서 볼 수 없는 경우 중단-매개 변수를 선언 하는 P/Invoke를 어셈블리 외부에서 볼 수 있는 경우.|

## <a name="cause"></a>원인
 플랫폼 호출 메서드가 잘못 선언 되었습니다.

## <a name="rule-description"></a>규칙 설명
 플랫폼 호출 메서드는 비관리 코드에 액세스 하 고 또는의 키워드를 사용 하 여 정의 됩니다 `Declare` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . 현재이 규칙은 겹친 구조체 매개 변수에 대 한 포인터를 포함 하는 Win32 함수를 대상으로 하는 플랫폼 호출 메서드 선언을 검색 하 고 해당 관리 되는 매개 변수는 구조체에 대 한 포인터가 아닙니다 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 플랫폼 호출 메서드를 올바르게 선언 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 규칙을 위반 하 고 규칙을 충족 하는 플랫폼 호출 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>관련 항목
 [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
