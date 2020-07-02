---
title: 'CA1720: 식별자에 형식 이름을 포함 하면 안 됩니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f6d228b0fbf5507ba135f9ddc35d6d8b161f0011
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534851"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: 식별자에 형식 이름을 포함하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 표시 되는 멤버의 매개 변수 이름에는 데이터 형식 이름이 포함 됩니다.

 또는

 외부에 표시 되는 멤버의 이름에는 언어별 데이터 형식 이름이 포함 됩니다.

## <a name="rule-description"></a>규칙 설명
 매개 변수 및 멤버 이름은 개발 도구에서 제공 해야 하는 형식을 설명 하는 것 보다 의미를 전달 하는 데 더 적합 합니다. 멤버의 이름으로 데이터 형식 이름을 사용 해야 하는 경우 언어 관련 이름을 사용 하는 대신 언어 독립적 이름을 사용 합니다. 예를 들어 c # 형식 이름 ' int ' 대신 언어 독립적 데이터 형식 이름인 Int32를 사용 합니다.

 매개 변수 또는 멤버의 이름에 있는 각 불연속 토큰은 대/소문자를 구분 하지 않는 방식으로 다음과 같은 언어별 데이터 형식 이름에 대해 확인 됩니다.

- Bool

- WChar

- Int8

- UInt8

- Short

- UShort

- Int

- 단위

- 정수

- UInteger

- long

- ULong

- 부호 없음

- 서명

- Float

- Float32

- 아니면

  또한 매개 변수의 이름도 대/소문자를 구분 하지 않는 방식으로 다음과 같은 언어 독립적 데이터 형식 이름에 대해 확인 됩니다.

- Object

- 인스턴스인

- 부울

- Char

- String

- SByte

- Byte

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- Ptr

- 포인터

- UInptr

- UPtr

- UPointer

- Single

- Double

- Decimal

- Guid

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 **매개 변수에 대해 발생 하는 경우:**

 매개 변수 이름에 있는 데이터 형식 식별자를 의미를 더 잘 설명 하는 용어 또는 ' value '와 같은 보다 일반적인 용어로 바꾸십시오.

 **멤버에 대해 발생 한 경우:**

 멤버의 이름에 있는 언어별 데이터 형식 식별자를 의미, 언어에 관계 없이 해당 하는 용어 또는 ' value '와 같은 보다 일반적인 용어를 더 잘 설명 하는 용어로 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 때때로 형식 기반 매개 변수 및 멤버 이름을 사용 하는 것이 적절할 수 있습니다. 그러나 새로운 개발의 경우에는이 규칙에서 경고를 표시 하지 않아야 하는 알려진 시나리오가 발생 하지 않습니다. 이전에 제공 된 라이브러리의 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.

## <a name="related-rules"></a>관련 규칙
 [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: 식별자에는 밑줄을 사용할 수 없습니다.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: 매개 변수 이름은 멤버 이름과 달라야 합니다.](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
