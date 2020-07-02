---
title: 'CA1801: 사용 하지 않는 매개 변수를 검토 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c87836f99684c7e16c022e3e9f15bf546ba82d62
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547786"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: 사용되지 않은 매개 변수를 검토하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 [CA1801: 사용 하지 않는 매개 변수 검토](/visualstudio/code-quality/ca1801-review-unused-parameters)를 참조 하세요.

|항목|값|
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|범주|Microsoft 사용|
|변경 수준|중단-변경 내용에 관계 없이 멤버가 어셈블리 외부에 표시 되지 않는 경우입니다.<br /><br /> 중단-본문 내에서 매개 변수를 사용 하도록 멤버를 변경 하는 경우<br /><br /> 중단-매개 변수를 제거 하 고 어셈블리 외부에 표시 되는 경우입니다.|

## <a name="cause"></a>원인
 메서드 시그니처에 메서드 본문에서 사용되지 않는 매개 변수가 있습니다. 이 규칙은 다음 방법을 검사 하지 않습니다.

- 대리자가 참조 하는 메서드입니다.

- 이벤트 처리기로 사용 되는 메서드입니다.

- `abstract`(Visual Basic) 한정자를 사용 하 여 선언 된 메서드입니다 `MustOverride` .

- `virtual`(Visual Basic) 한정자를 사용 하 여 선언 된 메서드입니다 `Overridable` .

- `override`(Visual Basic) 한정자를 사용 하 여 선언 된 메서드입니다 `Overrides` .

- `extern`( `Declare` 문 Visual Basic) 한정자를 사용 하 여 선언 된 메서드입니다.

## <a name="rule-description"></a>규칙 설명
 메서드 본문에서 사용 되지 않는 비가상 메서드에서 매개 변수를 검토 하 여 액세스 실패와 관련 하 여 정확성을 보장 하지 않도록 합니다. 사용 하지 않는 매개 변수는 유지 관리 및 성능 비용을 초래 합니다.

 경우에 따라이 규칙의 위반이 메서드에서 구현 버그를 가리킬 수 있습니다. 예를 들어 매개 변수는 메서드 본문에서 사용 되어야 합니다. 이전 버전과의 호환성으로 인해 매개 변수가 존재 해야 하는 경우에는이 규칙의 경고를 표시 하지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 사용 하지 않는 매개 변수 (주요 변경 내용)를 제거 하거나 메서드 본문에서 매개 변수를 사용 합니다 (주요 변경 내용 아님).

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이전에 제공 된 코드에 대 한 경고를 수정 하 여 주요 변경 내용을 적용할 수 있는 것은 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 두 개의 메서드를 보여 줍니다. 하나는 규칙을 위반 하 고 다른 메서드는 규칙을 충족 합니다.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1811: 호출되지 않는 전용 코드를 사용하지 마세요.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: 사용되지 않는 로컬 항목을 제거하세요.](../code-quality/ca1804-remove-unused-locals.md)
