---
title: 'CA1816: GC를 호출 합니다. Gc.suppressfinalize 올바르게 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 532478a8d6ed6b88347d196b4a74b6f19a38ef85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546772"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize를 올바르게 호출하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|범주|Microsoft. 사용량|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인

- 의 구현인 메서드는를 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 호출 하지 않습니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- 호출의 구현이 아닌 메서드입니다 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- 메서드는이 이외의 항목을 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 하 고이를 전달 합니다 (Visual Basic).

## <a name="rule-description"></a>규칙 설명
 메서드를 사용 하면 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 개체를 가비지 수집에 사용할 수 있게 되기 전에 언제 든 지 리소스를 해제할 수 있습니다. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>메서드가 호출 되 면 개체의 리소스를 해제 합니다. 이렇게 하면 종료 하지 않아도 됩니다. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 는를 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 하 여 가비지 수집기가 개체의 종료자를 호출 하지 않도록 해야 합니다.

 종료 자가 있는 파생 형식에서 [System.object]를 다시 구현 하지 못하게 하려면 (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->)를 호출 하 고 종료자를 사용 하지 않는 봉인 되지 않은 형식은 여전히을 호출 해야 합니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 다음을 수행 합니다.

 메서드가의 구현인 경우 <xref:System.IDisposable.Dispose%2A> 에는에 대 한 호출을 추가 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 합니다.

 메서드가의 구현이 아닌 경우 <xref:System.IDisposable.Dispose%2A> 에 대 한 호출을 제거 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 하거나 형식의 구현으로 이동 합니다 <xref:System.IDisposable.Dispose%2A> .

 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>이를 전달 하기 위해에 대 한 모든 호출 (Visual Basic)을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 Deliberating를 사용 하 여 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 다른 개체의 수명을 제어 하는 경우에만이 규칙에서 경고를 표시 하지 않습니다. 의 구현에서를 호출 하지 않는 경우에는이 규칙에서 경고를 표시 하지 마십시오 <xref:System.IDisposable.Dispose%2A> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> . 이 경우 종료를 표시 하지 않으면 성능이 저하 되 고 아무런 이점도 제공 되지 않습니다.

## <a name="example"></a>예
 다음 예제에서는를 잘못 호출 하는 메서드를 보여 줍니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>예
 다음 예제에서는를 올바르게 호출 하는 메서드를 보여 줍니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>관련 항목
 [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
