---
title: 'CA2111: 포인터를 표시 하지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7429251a66ce2fe22a825a153cb90248faabb9fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544367"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: 포인터는 노출되면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 또는 보호 된 <xref:System.IntPtr?displayProperty=fullName> 또는 <xref:System.UIntPtr?displayProperty=fullName> 필드가 읽기 전용이 아닙니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.IntPtr> 및 <xref:System.UIntPtr> 는 관리 되지 않는 메모리에 액세스 하는 데 사용 되는 포인터 형식입니다. 포인터가 전용, 내부 또는 읽기 전용이 아닌 경우 악성 코드는 포인터의 값을 변경 하 여 메모리의 임의 위치에 대 한 액세스를 허용 하거나 응용 프로그램 또는 시스템 오류를 발생 시킬 수 있습니다.

 포인터 필드를 포함 하는 형식에 대 한 액세스를 보호 하려는 경우 [CA2112: 보안 형식에서 필드를 노출 하면 안](../code-quality/ca2112-secured-types-should-not-expose-fields.md)됩니다 .를 참조 하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 포인터를 읽기 전용, 내부 또는 전용으로 설정 하 여 보안을 유지 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 포인터의 값에 의존 하지 않는 경우이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예
 다음 코드는 규칙을 위반 하 고 충족 하는 포인터를 보여 줍니다. Private이 아닌 포인터도 CA1051 규칙을 위반 합니다. [표시 되는 인스턴스 필드를 선언 하지 않습니다](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2112: 보안 형식은 필드를 노출하면 안 됩니다.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: 표시되는 인스턴스 필드를 선언하지 마세요.](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>관련 항목
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
