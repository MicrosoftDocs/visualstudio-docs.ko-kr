---
title: 'CA2220: 종료자는 기본 클래스 종료자를 호출 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540662"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: 종료자는 기본 클래스 종료자를 호출해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 을 재정의 하는 형식은 <xref:System.Object.Finalize%2A?displayProperty=fullName> <xref:System.Object.Finalize%2A> 기본 클래스의 메서드를 호출 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 종료는 상속 계층을 통해 전파되어야 합니다. 이를 위해 형식은 <xref:System.Object.Finalize%2A> 자체 메서드 내에서 기본 클래스 메서드를 호출 해야 합니다 <xref:System.Object.Finalize%2A> . C # 컴파일러는 기본 클래스 종료자에 대 한 호출을 자동으로 추가 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드에서 기본 형식의 메서드를 호출 <xref:System.Object.Finalize%2A> <xref:System.Object.Finalize%2A> 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 공용 언어 런타임을 대상으로 하는 일부 컴파일러는 기본 형식의 종료자에 대 한 호출을 MSIL (Microsoft 중간 언어)에 삽입 합니다. 이 규칙의 경고를 보고 하는 경우 컴파일러는 호출을 삽입 하지 않으므로 코드에 추가 해야 합니다.

## <a name="example"></a>예제
 다음 Visual Basic 예제에서는 `TypeB` <xref:System.Object.Finalize%2A> 기본 클래스에서 메서드를 올바르게 호출 하는 형식을 보여 줍니다.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>참고 항목
 [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
