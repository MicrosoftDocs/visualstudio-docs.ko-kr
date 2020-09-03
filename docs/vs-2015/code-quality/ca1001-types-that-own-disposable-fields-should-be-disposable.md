---
title: 'CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dab4532f082bd81eaa7b812eb038c5957636d453
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548319"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|범주|Microsoft 디자인|
|변경 수준|해당 형식이 어셈블리 외부에 표시 되지 않는 경우에는 중단 되지 않습니다.<br /><br /> 중단-형식이 어셈블리 외부에 표시 되는 경우입니다.|

## <a name="cause"></a>원인
 클래스가 형식이 고 클래스가 구현 하지 않는 인스턴스 필드를 선언 하 고 구현 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IDisposable> 합니다.

## <a name="rule-description"></a>규칙 설명
 클래스는 <xref:System.IDisposable> 소유 하 고 있는 관리 되지 않는 리소스를 삭제 하기 위해 인터페이스를 구현 합니다. 형식인 인스턴스 필드는 <xref:System.IDisposable> 필드가 관리 되지 않는 리소스를 소유 함을 나타냅니다. 필드를 선언 하는 클래스는 <xref:System.IDisposable> 관리 되지 않는 리소스를 간접적으로 소유 하 고 인터페이스를 구현 해야 합니다 <xref:System.IDisposable> . 클래스에서 관리 되지 않는 리소스를 직접 소유 하지 않는 경우 종료자를 구현 하지 않아야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드에서 및를 구현 하 <xref:System.IDisposable> 고 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.IDisposable.Dispose%2A> 필드의 메서드를 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 규칙을 위반 하는 클래스와을 구현 하 여 규칙을 충족 하는 클래스를 보여 줍니다 <xref:System.IDisposable> . 클래스는 관리 되지 않는 리소스를 직접 소유 하지 않으므로 종료자를 구현 하지 않습니다.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2213: 삭제 가능한 필드는 삭제해야 합니다.](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
