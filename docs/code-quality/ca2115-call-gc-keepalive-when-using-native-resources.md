---
title: 'CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232718"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|범주|Microsoft.Security|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

종료자를 사용 하 여 형식에서 선언 된 메서드가 <xref:System.IntPtr?displayProperty=fullName> 또는 <xref:System.UIntPtr?displayProperty=fullName> 필드를 참조 하지만를 호출 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>하지 않습니다.

## <a name="rule-description"></a>규칙 설명

관리 코드에서 개체에 대 한 참조가 더 이상 없으면 가비지 수집에서 개체를 종료 합니다. 개체에 대 한 관리 되지 않는 참조는 가비지 수집을 방지 하지 않습니다. 이 규칙에서는 관리되지 않는 리소스가 비관리 코드에서 여전히 사용되고 있는데 종료되려고 할 경우 발생할 수 있는 오류를 감지합니다.

이 규칙은 <xref:System.IntPtr> 및 <xref:System.UIntPtr> 필드가 관리 되지 않는 리소스에 대 한 포인터를 저장 한다고 가정 합니다. 종료자의 용도는 관리 되지 않는 리소스를 해제 하는 것 이므로 규칙에서는 종료 자가 포인터 필드에서 가리키는 관리 되지 않는 리소스를 해제 하는 것으로 가정 합니다. 또한이 규칙은 메서드가 포인터 필드를 참조 하 여 관리 되지 않는 리소스를 비관리 코드에 전달 하는 것으로 가정 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 <xref:System.GC.KeepAlive%2A> 하려면 메서드에 호출을 추가 하 여 및`this` C# C++의 현재 인스턴스를 인수로 전달 합니다. 가비지 수집에서 개체를 보호 해야 하는 코드의 마지막 줄 뒤에 호출을 배치 합니다. 를 <xref:System.GC.KeepAlive%2A>호출한 직후에는 개체에 대 한 관리 되는 참조가 없다는 가정 하에 개체를 다시 가비지 수집 준비로 간주 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이 규칙은 가양성을 일으킬 수 있는 몇 가지 가정을 합니다. 다음 경우에는이 규칙에서 경고를 안전 하 게 표시 하지 않을 수 있습니다.

- 종료자는 메서드가 참조 하는 <xref:System.IntPtr> 또는 <xref:System.UIntPtr> 필드의 콘텐츠를 해제 하지 않습니다.

- 메서드는 <xref:System.IntPtr> 또는 <xref:System.UIntPtr> 필드를 비관리 코드에 전달 하지 않습니다.

제외 하기 전에 다른 메시지를 신중 하 게 검토 합니다. 이 규칙은 재현 및 디버깅 하기 어려운 오류를 검색 합니다.

## <a name="example"></a>예제

다음 예제에서 `BadMethod`에는 `GC.KeepAlive`에 대한 호출이 포함되지 않으므로 규칙을 위반합니다. `GoodMethod`수정 된 코드를 포함 합니다.

> [!NOTE]
> 이 예제는 의사 (pseudo) 코드입니다. 코드를 컴파일하고 실행 하더라도 관리 되지 않는 리소스가 만들어지거나 해제 되기 때문에 경고가 발생 하지 않습니다.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>참고 항목

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)