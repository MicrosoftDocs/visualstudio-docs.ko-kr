---
title: 'CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1616e889b3892aa656692a3e5b0895d4b131b7f1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231249"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

을 구현 <xref:System.IDisposable?displayProperty=fullName>하 고 관리 되지 않는 리소스의 사용을 제안 하는 필드를 포함 하는 형식에서는에 <xref:System.Object.Finalize%2A?displayProperty=fullName>설명 된 대로 종료자를 구현 하지 않습니다.

## <a name="rule-description"></a>규칙 설명

삭제 가능한 형식에 다음 형식의 필드가 포함 되어 있으면이 규칙의 위반이 보고 됩니다.

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 <xref:System.IDisposable.Dispose%2A> 메서드를 호출 하는 종료자를 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

형식이 관리 되지 않는 리소스를 해제 하기 위해를 구현 <xref:System.IDisposable> 하지 않는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제

다음 예제에서는이 규칙을 위반 하는 형식을 보여 줍니다.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>관련 규칙

[CA2115: GC를 호출 합니다. 네이티브 리소스를 사용 하는 경우 KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: GC를 호출 합니다. Gc.suppressfinalize 올바르게](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: 네이티브 리소스를 소유 하는 형식은 삭제 가능 해야 합니다.](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>참고 항목

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)