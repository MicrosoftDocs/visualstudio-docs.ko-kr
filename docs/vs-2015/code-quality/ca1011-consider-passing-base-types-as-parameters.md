---
title: 'CA1011: 기본 형식을 매개 변수로 전달 하는 것이 좋습니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f689dfd6c1d39bbd03d522a33ed8c5639a3da9f8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545485"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: 기본 형식을 매개 변수로 전달해 보세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 메서드 선언에는 파생 형식인 정식 매개 변수가 포함 되 고, 메서드는 매개 변수의 기본 형식의 멤버만 호출 합니다.

## <a name="rule-description"></a>규칙 설명
 기본 형식이 메서드 선언의 매개 변수로 지정된 경우 기본 형식에서 파생된 모든 형식을 해당 인수로 메서드에 전달할 수 있습니다. 메서드 본문 내에서 인수를 사용 하는 경우 실행 되는 특정 메서드는 인수의 형식에 따라 달라 집니다. 파생 된 형식에서 제공 하는 추가 기능이 필요 하지 않은 경우에는 기본 형식을 사용 하 여 메서드를 광범위 하 게 사용할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 매개 변수의 형식을 기본 형식으로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시 하지 않는 것이 안전 합니다.

- 메서드가 파생 형식에서 제공 하는 특정 기능을 필요로 하는 경우

   \- 또는 -

- 파생 된 형식 또는 더 많이 파생 된 형식만 메서드에 전달 되도록 적용 하려면입니다.

  이러한 경우 컴파일러 및 런타임에서 제공 하는 강력한 형식 검사 때문에 코드가 더 강력 합니다.

## <a name="example"></a>예제
 다음 예제에서는 `ManipulateFileStream` 이 규칙을 위반 하는 개체에만 사용할 수 있는 메서드를 보여 줍니다 <xref:System.IO.FileStream> . 두 번째 메서드인 `ManipulateAnyStream` <xref:System.IO.FileStream> 는를 사용 하 여 매개 변수를 대체 하 여 규칙을 충족 합니다 <xref:System.IO.Stream> .

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1059: 멤버는 구체적인 특정 형식을 노출하면 안 됩니다.](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
