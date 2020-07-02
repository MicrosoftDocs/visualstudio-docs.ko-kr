---
title: 'CA2215: Dispose 메서드는 기본 클래스 dispose를 호출 해야 합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534383"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 을 구현 하는 형식은 <xref:System.IDisposable?displayProperty=fullName> 도 구현 하는 형식에서 상속 <xref:System.IDisposable> 됩니다. 상속 하는 <xref:System.IDisposable.Dispose%2A> 형식의 메서드는 부모 형식의 메서드를 호출 하지 않습니다 <xref:System.IDisposable.Dispose%2A> .

## <a name="rule-description"></a>규칙 설명
 형식이 삭제 가능한 형식에서 상속 되는 경우 <xref:System.IDisposable.Dispose%2A> 자체 메서드 내에서 기본 형식의 메서드를 호출 해야 합니다 <xref:System.IDisposable.Dispose%2A> . 기본 형식 메서드 Dispose를 호출 하면 기본 형식에서 생성 된 모든 리소스가 해제 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면를 호출 `base` 합니다.<xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A>메서드에서

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 을 호출 하는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 `base` 합니다.<xref:System.IDisposable.Dispose%2A> 규칙 검사 보다 더 깊은 호출 수준에서 발생 합니다.

## <a name="example"></a>예제
 다음 예제에서는를 구현 하는 형식을 보여 줍니다 `TypeA` <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 `TypeB` 형식에서 상속 하 `TypeA` 고 해당 메서드를 올바르게 호출 하는 형식을 보여 줍니다 <xref:System.IDisposable.Dispose%2A> .

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.IDisposable?displayProperty=fullName> [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
