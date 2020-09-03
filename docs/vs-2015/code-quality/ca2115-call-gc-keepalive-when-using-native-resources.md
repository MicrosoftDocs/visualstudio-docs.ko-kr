---
title: 'CA2115: GC를 호출 합니다. 네이티브 리소스를 사용 하는 경우 KeepAlive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c668172ca318000068fb4e90f4848e456c32208d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543626"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 종료자를 사용 하 여 형식에서 선언 된 메서드가 <xref:System.IntPtr?displayProperty=fullName> 또는 필드를 참조 <xref:System.UIntPtr?displayProperty=fullName> 하지만를 호출 하지 않습니다 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> .

## <a name="rule-description"></a>규칙 설명
 관리 코드에서 개체에 대 한 참조가 더 이상 없으면 가비지 수집에서 개체를 종료 합니다. 개체에 대 한 관리 되지 않는 참조는 가비지 수집을 방지 하지 않습니다. 이 규칙에서는 관리되지 않는 리소스가 비관리 코드에서 여전히 사용되고 있는데 종료되려고 할 경우 발생할 수 있는 오류를 감지합니다.

 이 규칙은 <xref:System.IntPtr> 및 <xref:System.UIntPtr> 필드가 관리 되지 않는 리소스에 대 한 포인터를 저장 한다고 가정 합니다. 종료자의 용도는 관리 되지 않는 리소스를 해제 하는 것 이므로 규칙에서는 종료 자가 포인터 필드에서 가리키는 관리 되지 않는 리소스를 해제 하는 것으로 가정 합니다. 또한이 규칙은 메서드가 포인터 필드를 참조 하 여 관리 되지 않는 리소스를 비관리 코드에 전달 하는 것으로 가정 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드에 호출을 추가 하 여 <xref:System.GC.KeepAlive%2A> 현재 인스턴스 ( `this` c # 및 c + +)를 인수로 전달 합니다. 가비지 수집에서 개체를 보호 해야 하는 코드의 마지막 줄 뒤에 호출을 배치 합니다. 를 호출한 직후에는 <xref:System.GC.KeepAlive%2A> 개체에 대 한 관리 되는 참조가 없다는 가정 하에 개체를 다시 가비지 수집 준비로 간주 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙은 가양성을 일으킬 수 있는 몇 가지 가정을 합니다. 다음 경우에는이 규칙에서 경고를 안전 하 게 표시 하지 않을 수 있습니다.

- 종료자는 메서드가 참조 하는 또는 필드의 콘텐츠를 해제 하지 않습니다 <xref:System.IntPtr> <xref:System.UIntPtr> .

- 메서드는 <xref:System.IntPtr> 또는 <xref:System.UIntPtr> 필드를 비관리 코드에 전달 하지 않습니다.

  제외 하기 전에 다른 메시지를 신중 하 게 검토 합니다. 이 규칙은 재현 및 디버깅 하기 어려운 오류를 검색 합니다.

## <a name="example"></a>예
 다음 예제에서 `BadMethod`에는 `GC.KeepAlive`에 대한 호출이 포함되지 않으므로 규칙을 위반합니다. `GoodMethod` 수정 된 코드를 포함 합니다.

> [!NOTE]
> 이 예제는 의사 코드입니다. 코드가 컴파일되고 실행되더라도 관리되지 않는 리소스가 생성 또는 해제되지 않으므로 경고가 발생하지 않습니다.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
