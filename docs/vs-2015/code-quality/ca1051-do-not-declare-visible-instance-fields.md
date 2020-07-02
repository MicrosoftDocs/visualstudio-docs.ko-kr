---
title: 'CA1051: 표시 되는 인스턴스 필드를 선언 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 076ce3858774d44e2d6c4c25205ced74b7a41bf0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539765"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: 표시되는 인스턴스 필드를 선언하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 표시 되는 형식에는 외부에서 표시 되는 인스턴스 필드가 있습니다.

## <a name="rule-description"></a>규칙 설명
 필드의 주된 용도는 구현을 세부적으로 설명하는 것입니다. 필드는 또는 여야 하 `private` `internal` 고 속성을 사용 하 여 노출 되어야 합니다. 필드에 액세스 하는 것과 같이 속성에 쉽게 액세스할 수 있으며, 형식의 기능이 주요 변경 사항을 도입 하지 않고 확장 될 때 속성의 접근자에 있는 코드가 변경 될 수 있습니다. 전용 또는 내부 필드의 값을 반환 하는 속성은 필드 액세스와 동일 하 게 수행 하도록 최적화 되어 있습니다. 속성에 대해 외부적으로 표시 되는 필드의 사용과 관련 하 여 성능 향상이 거의 없습니다.

 외부적으로 표시 되는 `public` 는,, `protected` 및 `protected internal` ( `Public` `Protected` `Protected Friend` Visual Basic) 액세스 가능성 수준에서, 및를 나타냅니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 필드를 설정 `private` 하거나 `internal` 외부에서 볼 수 있는 속성을 사용 하 여 노출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 외부적으로 표시 되는 필드는 속성에 사용할 수 없는 이점을 제공 하지 않습니다. 또한 public 필드는 [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)으로 보호할 수 없습니다. [CA2112: 보안 형식은 필드를 노출 하면](../code-quality/ca2112-secured-types-should-not-expose-fields.md)안 됩니다 .를 참조 하세요.

## <a name="example"></a>예제
 다음 예제에서는 `BadPublicInstanceFields` 이 규칙을 위반 하는 형식 ()을 보여 줍니다. `GoodPublicInstanceFields`수정 된 코드를 표시 합니다.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2112: 보안 형식은 필드를 노출하면 안 됩니다.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>참고 항목
 [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
