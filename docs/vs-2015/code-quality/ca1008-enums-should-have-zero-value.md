---
title: 'CA1008: 열거형에는 0 값이 있어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548345"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: 열거형에는 0 값이 있어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|범주|Microsoft 디자인|
|변경 수준|비-플래그 열거에 **None** 값을 추가 하 라는 메시지가 표시 되는 경우 중단-열거형 값의 이름을 바꾸거나 제거할 것인지 묻는 메시지가 표시 되 면입니다.|

## <a name="cause"></a>원인
 적용 된가 없는 열거형은 <xref:System.FlagsAttribute?displayProperty=fullName> 값이 0 인 멤버를 정의 하지 않습니다. 또는 적용 된가 있는 열거형에서 값이 0 인 멤버를 정의 하 고 <xref:System.FlagsAttribute> 해당 이름이 ' n o n e '이 아니거나 열거형이 여러 개의 0 값 멤버를 정의 합니다.

## <a name="rule-description"></a>규칙 설명
 다른 값 형식과 마찬가지로 초기화 되지 않은 열거형의 기본값은 0입니다. 플래그가 지정 되지 않은 특성을 가진 열거형은 기본값이 열거형의 유효한 값이 되도록 0 값을 가진 멤버를 정의 해야 합니다. 해당 하는 경우 멤버 이름을 ' n o n e '으로 합니다. 그렇지 않으면 가장 자주 사용 되는 멤버에 0을 할당 합니다. 기본적으로 선언에서 첫 번째 열거형 멤버의 값이 설정 되지 않은 경우 해당 값은 0입니다.

 를 적용 한 열거형이 0 값의 멤버를 정의 하는 경우 <xref:System.FlagsAttribute> 열거형에 값이 설정 되지 않았음을 나타내려면 해당 이름이 ' n o n e ' 이어야 합니다. 다른 용도에 대해 0 값 멤버를 사용 하는 것은 <xref:System.FlagsAttribute> 및 및 비트 연산자가 멤버와 쓸모가 없다는 점에서를 사용 하는 것과는 반대입니다. 이는 한 멤버만 값 0을 할당 해야 함을 의미 합니다. 플래그 특성이 지정 된 열거형에서 값이 0 인 멤버가 여러 개 발생 하는 경우는 `Enum.ToString()` 0이 아닌 멤버에 대해 잘못 된 결과를 반환 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 플래그가 지정 되지 않은 특성 사용 열거에 대 한이 규칙 위반 문제를 해결 하려면 값이 0 인 멤버를 정의 합니다. 이는 주요 변경 내용입니다. 0 값 멤버를 정의 하는 플래그 특성을 사용 하는 열거형의 경우이 멤버의 이름을 ' n o n e '으로 지정 하 고 값이 0 인 다른 멤버를 삭제 합니다. 이는 주요 변경 내용입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이전에 제공 된 플래그 특성을 사용 하는 열거형을 제외 하 고이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 충족 하는 열거형 두 개와 `BadTraceOptions` 규칙을 위반 하는 열거형을 보여 줍니다.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2217: 열거형을 FlagsAttribute로 표시하지 마세요.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: 열거형 값의 이름을 'Reserved'로 지정하지 마세요.](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: 열거형 값에 형식 이름을 접두사로 사용하지 마세요.](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: 열거형 스토리지는 Int32여야 합니다.](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: 열거형을 FlagsAttribute로 표시하세요.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Enum?displayProperty=fullName>
