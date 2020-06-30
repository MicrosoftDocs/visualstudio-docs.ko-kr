---
title: 'CA1036: 비교 가능한 형식에 메서드를 재정의 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52247c9175b22d3d96aa91557ee133f37c55e789
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546603"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: 비교 가능한 형식에 메서드를 재정의하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 인터페이스를 구현 <xref:System.IComparable?displayProperty=fullName> 하며 <xref:System.Object.Equals%2A?displayProperty=fullName> , 같음, 같지 않음, 보다 작음 또는 보다 큼에 대해 언어별 연산자를 재정의 하거나 오버 로드 하지 않습니다. 형식이 인터페이스의 구현만 상속 하는 경우 규칙에서 위반을 보고 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 사용자 지정 정렬 순서를 정의 하는 형식은 <xref:System.IComparable> 인터페이스를 구현 합니다. <xref:System.IComparable.CompareTo%2A>메서드는 형식의 두 인스턴스에 대 한 올바른 정렬 순서를 나타내는 정수 값을 반환 합니다. 이 규칙은 정렬 순서를 설정 하는 형식을 식별 합니다. 이는 같음, 같지 않음, 보다 작음, 보다 큼의 일반적인 의미가 적용 되지 않음을 의미 합니다. 의 구현을 제공 하는 경우 <xref:System.IComparable> 일반적으로와 일치 하는 값을 반환 하도록를 재정의 해야 합니다 <xref:System.Object.Equals%2A> <xref:System.IComparable.CompareTo%2A> . <xref:System.Object.Equals%2A>연산자 오버 로드를 지 원하는 언어에서를 재정의 하 고 코딩 하는 경우와 일치 하는 연산자도 제공 해야 <xref:System.Object.Equals%2A> 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면를 재정의 <xref:System.Object.Equals%2A> 합니다. 프로그래밍 언어가 연산자 오버 로드를 지 원하는 경우 다음 연산자를 제공 합니다.

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  C #에서 이러한 연산자를 나타내는 데 사용 되는 토큰은 = =,! \<, and > =,와 같습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 누락 된 연산자로 인해 위반이 발생 했을 때 프로그래밍 언어가 연산자 오버 로드를 지원 하지 않는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. Visual Basic .NET의 경우와 동일 합니다. 또한 연산자를 구현 하는 것이 응용 프로그램 컨텍스트에서 적합 하지 않을 것으로 확인 되는 경우 op_Equality 이외의 같음 연산자에서 발생 하는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 그러나 개체. Equals를 재정의 하는 경우 항상 op_Equality 및 = = 연산자를 재정의 해야 합니다.

## <a name="example"></a>예제
 다음 예제에는를 올바르게 구현 하는 형식이 포함 되어 있습니다 <xref:System.IComparable> . 코드 주석은 및 인터페이스와 관련 된 다양 한 규칙을 충족 하는 메서드를 식별 <xref:System.Object.Equals%2A> <xref:System.IComparable> 합니다.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램은 이전에 표시 된 구현의 동작을 테스트 합니다 <xref:System.IComparable> .

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [같음 연산자](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
