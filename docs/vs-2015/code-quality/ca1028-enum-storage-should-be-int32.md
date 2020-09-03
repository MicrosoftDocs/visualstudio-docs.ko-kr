---
title: 'CA1028: Enum 저장소는 Int32 여야 합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0b2e8ebcc7720f5cd9dc6c700bcc08b68f89e275
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542495"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: 열거형 스토리지는 Int32여야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 열거형의 내부 형식이 <xref:System.Int32?displayProperty=fullName> 가 아닌 경우

## <a name="rule-description"></a>규칙 설명
 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 기본적으로 <xref:System.Int32?displayProperty=fullName> 데이터 형식은 상수 값을 저장 하는 데 사용 됩니다. 이 기본 형식을 변경할 수 있지만 대부분의 시나리오에서는 필요 하지 않거나 권장 되지 않습니다. 보다 작은 데이터 형식을 사용 하 여 성능이 크게 향상 되는 것은 아닙니다 <xref:System.Int32> . 기본 데이터 형식을 사용할 수 없는 경우 cls 규격 정수 형식,,, 또는 중 하나를 사용 <xref:System.Byte> <xref:System.Int16> 하 여 <xref:System.Int32> <xref:System.Int64> 열거형의 모든 값을 cls 규격 프로그래밍 언어로 표현할 수 있는지 확인 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 크기 또는 호환성 문제가 있는 경우를 제외 하 고이 규칙 위반 문제를 해결 하려면를 사용 <xref:System.Int32> 합니다. <xref:System.Int32>가 값을 저장할 수 있을 정도로 크지 않은 경우를 사용 <xref:System.Int64> 합니다. 이전 버전과의 호환성을 위해 더 작은 데이터 형식이 필요한 경우 또는를 사용 <xref:System.Byte> <xref:System.Int16> 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이전 버전과의 호환성 문제를 필요로 하는 경우에만이 규칙에서 경고를 표시 하지 않습니다. 응용 프로그램에서이 규칙을 준수 하지 않으면 일반적으로 문제가 발생 하지 않습니다. 언어 상호 운용성이 필요한 라이브러리에서이 규칙을 준수 하지 않으면 사용자에 게 부정적인 영향을 줄 수 있습니다.

## <a name="example-of-a-violation"></a>위반 예

### <a name="description"></a>설명
 다음 예에서는 권장 되는 기본 데이터 형식을 사용 하지 않는 두 개의 열거형을 보여 줍니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>해결 방법의 예

### <a name="description"></a>설명
 다음 예에서는 기본 데이터 형식을로 변경 하 여 이전 위반을 수정 합니다 <xref:System.Int32> .

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1008: 열거형에는 0 값이 있어야 합니다.](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: 열거형을 FlagsAttribute로 표시하세요.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: 열거형을 FlagsAttribute로 표시하지 마세요.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: 열거형 값의 이름을 'Reserved'로 지정하지 마세요.](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: 열거형 값에 형식 이름을 접두사로 사용하지 마세요.](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>관련 항목
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
