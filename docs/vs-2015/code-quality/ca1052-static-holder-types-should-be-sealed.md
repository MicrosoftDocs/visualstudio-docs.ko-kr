---
title: 'CA1052: 정적 소유자 형식은 sealed 여야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14231cc4dcde5aed5cabc2d8a6172a002c0ba6bf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539752"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: 정적 소유자 형식은 sealed여야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 정적 멤버만 포함 하며 [sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) 한정자로 선언 되지 않았습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 파생 형식에서 재정의할 수 있는 기능을 제공 하지 않기 때문에 정적 멤버만 포함 된 형식이 상속 되도록 설계 되지 않았다고 가정 합니다. 상속되지 않는 형식은 기본 형식으로 사용되지 않도록 `sealed` 한정자로 표시해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 형식을로 표시 합니다 `sealed` . 2.0 이전 버전을 대상으로 하는 경우 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식을로 표시 하는 것이 더 좋습니다 `static` . 이러한 방식으로 클래스가 생성 되지 않도록 private 생성자를 선언 하지 않아도 됩니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식을 상속 하도록 디자인 된 경우에만이 규칙에서 경고를 표시 하지 않습니다. 한정자가 없으면 `sealed` 형식이 기본 형식으로 유용한 것으로 제안 합니다.

## <a name="example-of-a-violation"></a>위반 예

### <a name="description"></a>설명
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

### <a name="code"></a>코드
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Static 한정자를 사용 하 여 수정

### <a name="description"></a>설명
 다음 예제에서는 형식을 한정자로 표시 하 여이 규칙 위반 문제를 해결 하는 방법을 보여 줍니다 `static` .

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1053: 정적 소유자 형식에는 생성자를 사용하면 안 됩니다.](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
