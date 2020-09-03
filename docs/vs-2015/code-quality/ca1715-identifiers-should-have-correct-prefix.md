---
title: 'CA1715: 식별자에는 올바른 접두사를 포함 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe362a58a047c8594d09bc6985c48d16f21d3b76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545602"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: 식별자에는 올바른 접두사를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 [CA1715: identifier에 올바른 접두사가](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix)있어야 합니다 .를 참조 하세요.

|항목|값|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|범주|Microsoft. 이름 지정|
|변경 수준|중단-인터페이스에서 발생 한 경우<br /><br /> 제네릭 형식 매개 변수에 대해 발생 하는 경우를 구분 하지 않습니다.|

## <a name="cause"></a>원인
 외부에 노출 되는 인터페이스의 이름이 대문자 ' I '로 시작 하지 않습니다.

 또는

 외부에서 볼 수 있는 형식 또는 메서드에 대 한 제네릭 형식 매개 변수의 이름이 대문자 ' t '로 시작 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 규칙에 따라 특정 프로그래밍 요소의 이름이 특정 접두사로 시작 합니다.

 인터페이스 이름은 대문자 ' I '로 시작 하 고 또 다른 대문자를 사용 해야 합니다. 이 규칙은 ' MyInterface ' 및 ' IsolatedInterface '과 같은 인터페이스 이름 위반을 보고 합니다.

 제네릭 형식 매개 변수 이름은 대문자 ' t '로 시작 해야 하며, 선택적으로 다른 대문자를 사용할 수 있습니다. 이 규칙은 ' V ' 및 ' Type '과 같은 제네릭 형식 매개 변수 이름에 대 한 위반을 보고 합니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 식별자의 이름을 적절 하 게 접두사로 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 **다음 예제에서는 잘못 명명 된 인터페이스를 보여 줍니다.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.vb#1)]

## <a name="example"></a>예
 **다음 예제에서는 인터페이스에 ' I '를 접두사로 사용 하 여 이전 위반을 수정 합니다.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.vb#1)]

## <a name="example"></a>예
 **다음 예제에서는 잘못 명명 된 제네릭 형식 매개 변수를 보여 줍니다.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.vb#1)]

## <a name="example"></a>예
 **다음 예제에서는 제네릭 형식 매개 변수를 ' t '로 접두사로 사용 하 여 이전 위반을 수정 합니다.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1722: 식별자에는 올바른 접두사를 사용해야 합니다.](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
