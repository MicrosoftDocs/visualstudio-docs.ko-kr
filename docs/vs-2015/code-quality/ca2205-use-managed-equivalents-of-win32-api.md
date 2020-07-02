---
title: 'CA2205: Win32 API |의 관리 되는 항목 사용 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 85e27ab04ca81f5513a0b09bc41548f4a7c2430d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547682"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Win32 API의 동일한 관리형 기능을 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 플랫폼 호출 메서드가 정의 되 고 해당 기능이 있는 메서드가 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 라이브러리에 있습니다.

## <a name="rule-description"></a>규칙 설명
 플랫폼 호출 메서드는 관리 되지 않는 DLL 함수를 호출 하는 데 사용 되 고 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 특성 또는 Visual Basic의 키워드를 사용 하 여 정의 됩니다 `Declare` . 잘못 정의 된 플랫폼 호출 메서드는 misnamed 함수, 매개 변수 및 반환 값 데이터 형식의 잘못 된 매핑 및 호출 규칙 및 문자 집합과 같은 잘못 된 필드 사양과 같은 문제로 인해 런타임 예외를 일으킬 수 있습니다. 사용 가능한 경우 관리 되지 않는 메서드를 직접 정의 하 고 호출 하는 것 보다 해당 하는 관리 되는 메서드를 호출 하는 것이 더 간단 하 고 오류가 줄어듭니다. 플랫폼 호출 메서드를 호출 하면 해결 해야 하는 추가 보안 문제가 발생할 수도 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 관리 되지 않는 함수에 대 한 호출을 관리 되는 해당 함수로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 제안 된 대체 방법이 필요한 기능을 제공 하지 않는 경우에는이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 플랫폼 호출 메서드 정의를 보여 줍니다. 또한 플랫폼 호출 메서드 및 해당 하는 관리 되는 메서드에 대 한 호출이 표시 됩니다.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1404: P/Invoke 직후에 GetLastError를 호출 합니다.](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: P/Invoke를 NativeMethods 클래스로 이동 합니다.](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke 진입점이 있어야 합니다.](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke는 노출 되지 않아야 합니다.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
