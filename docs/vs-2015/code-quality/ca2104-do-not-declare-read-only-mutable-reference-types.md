---
title: 'CA2104: 변경 가능한 읽기 전용 참조 형식을 선언 하지 마십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521045"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: 변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|범주|Microsoft.Security|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식에 변경 가능한 참조 형식인, 외부에서 볼 수 있는 읽기 전용 필드가 포함되었습니다.

## <a name="rule-description"></a>규칙 설명
 변경 가능한 형식은 해당 인스턴스 데이터를 수정할 수 있는 형식을 말합니다. <xref:System.Text.StringBuilder?displayProperty=fullName>클래스는 변경 가능한 참조 형식의 예입니다. 클래스의 인스턴스 값을 변경할 수 있는 멤버가 포함 되어 있습니다. 변경할 수 없는 참조 형식의 예는 클래스입니다 <xref:System.String?displayProperty=fullName> . 인스턴스화된 후에는 해당 값이 변경 되지 않습니다.

 참조 형식 필드 (c + +의 경우)에서 읽기 전용 한정자 (c #의 경우 readonly [, in c](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) + +의 경우[readonly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] )는 필드가 참조 형식의 다른 인스턴스로 대체 되지 않도록 방지 합니다. [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) 그러나 한정자는 필드의 인스턴스 데이터가 참조 형식을 통해 수정 되는 것을 방지 하지 않습니다.

 읽기 전용 배열 필드는이 규칙에서 제외 되지만 대신 [CA2105: array 필드를 읽기 전용](../code-quality/ca2105-array-fields-should-not-be-read-only.md) 규칙으로 위반 하 게 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 읽기 전용 한정자를 제거 하거나, 주요 변경 내용이 허용 되는 경우 필드를 변경할 수 없는 형식으로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 필드 형식을 변경할 수 없는 경우에는이 규칙에서 경고를 무시 해도 됩니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 필드 선언을 보여 줍니다.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
