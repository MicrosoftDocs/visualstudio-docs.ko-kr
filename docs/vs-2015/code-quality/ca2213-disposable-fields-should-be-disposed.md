---
title: 'CA2213: 삭제 가능한 필드는 삭제 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534578"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: 삭제 가능한 필드는 삭제해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 을 구현 하는 형식은 <xref:System.IDisposable?displayProperty=fullName> 도 구현 하는 형식의 필드를 선언 <xref:System.IDisposable> 합니다. <xref:System.IDisposable.Dispose%2A>필드의 메서드는 선언 형식의 메서드에서 호출 되지 않습니다 <xref:System.IDisposable.Dispose%2A> .

## <a name="rule-description"></a>규칙 설명
 형식은 관리 되지 않는 모든 리소스의 삭제를 담당 합니다. 이는을 구현 하 여 수행 됩니다 <xref:System.IDisposable> . 이 규칙은 삭제 `T` 가능한 형식이 삭제 가능한 형식의 인스턴스인 필드를 선언 하는지 여부를 확인 `F` `FT` 합니다. 각 필드에 대해 `F` 규칙은에 대 한 호출을 찾으려고 시도 `FT.Dispose` 합니다. 규칙은에 의해 호출 되는 메서드를 검색 `T.Dispose` 하 고, 한 수준 낮은 (에서 호출 하는 메서드에 의해 호출 되는 메서드)를 검색 `FT.Dispose` 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable> 필드가 보유 하 고 있는 관리 되지 않는 리소스를 할당 하 고 해제 해야 하는 경우를 구현 하는 형식의 필드에 대해를 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 필드에서 보유 하는 리소스를 해제 하는 것을 담당 하지 않는 경우 또는에 대 한 호출이 <xref:System.IDisposable.Dispose%2A> 규칙 검사 보다 깊은 호출 수준에서 발생 하는 경우에는이 규칙에서 경고를 표시 하지 않아도 됩니다.

## <a name="example"></a>예
 다음 예제에서는 `TypeA` <xref:System.IDisposable> 이전 설명에서를 구현 하는 형식을 보여 줍니다 `FT` .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>예
 다음 예제에서는 필드 `TypeB` `aFieldOfADisposableType` `F` `TypeA` 에 대해를 호출 하지 않고 이전 설명의 필드를 삭제 가능한 형식 ()으로 선언 하 여이 규칙을 위반 하는 형식을 보여 줍니다 <xref:System.IDisposable.Dispose%2A> . `TypeB``T`이전 논의의에 해당 합니다.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.IDisposable?displayProperty=fullName> [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
