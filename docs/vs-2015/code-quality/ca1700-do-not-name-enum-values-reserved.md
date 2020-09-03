---
title: 'CA1700: 예약&#39; &#39;열거형 값의 이름을 만들지 않습니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57f2a2e5959860a99a921101ff5782f9bce9ace3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545654"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: 예약&#39; &#39;열거형 값의 이름을 하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 열거형 멤버의 이름에는 "reserved" 라는 단어가 포함 됩니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 "reserved"라는 단어가 포함된 이름을 갖는 열거형 멤버가 현재 사용되지는 않지만 이후 버전에서 이름이 바뀌거나 제거될 자리 표시자라고 가정합니다. 멤버의 이름을 바꾸거나 멤버를 제거하는 것은 주요 변경에 해당합니다. 사용자가 해당 이름에 "reserved"가 포함 되어 있거나 사용자가 문서를 읽거나 준수 하지 못하도록 하는 경우에만 멤버를 무시 하는 것은 아닙니다. 또한 예약 된 멤버는 개체 브라우저 및 스마트 통합 개발 환경에 표시 되기 때문에 실제로 사용 되는 멤버에 대해 혼동을 일으킬 수 있습니다.

 예약 된 멤버를 사용 하는 대신 이후 버전의 열거에 새 멤버를 추가 합니다. 대부분의 경우 새 멤버를 추가 하는 것은 원래 멤버의 값이 변경 되지 않는 한 새로운 변경 내용이 아닙니다.

 제한 된 수의 사례에서 원래 멤버가 원래 값을 유지 하는 경우에도 멤버를 추가 하는 것은 주요 변경 사항입니다. 주로 `switch` `Select` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 전체 멤버 목록을 포함 하 고 기본 사례에서 예외를 throw 하는 반환 값에 대해 (in) 문을 사용 하는 호출자를 중단 하지 않고 기존 코드 경로에서 새 멤버를 반환할 수 없습니다. 두 번째 문제는 클라이언트 코드가와 같은 리플렉션 메서드에서의 동작 변경을 처리 하지 않을 수 있다는 것입니다 <xref:System.Enum.IsDefined%2A?displayProperty=fullName> . 따라서 새 멤버가 기존 메서드에서 반환 되어야 하는 경우 또는 알려진 응용 프로그램 비 호환성이 잘못 된 리플렉션 사용으로 인해 발생 하는 경우 유일한 해결책은 다음과 같습니다.

1. 원래 및 새 멤버를 포함 하는 새 열거형을 추가 합니다.

2. 원래 열거를 특성으로 표시 합니다 <xref:System.ObsoleteAttribute?displayProperty=fullName> .

   원래 열거를 표시 하는 외부에 표시 되는 형식 또는 멤버에 대해 동일한 절차를 수행 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 멤버를 제거 하거나 이름을 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 현재 사용 중인 멤버나 이전에 제공 된 라이브러리에 대해서는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA2217: 열거형을 FlagsAttribute로 표시하지 마세요.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: 열거형 값에 형식 이름을 접두사로 사용하지 마세요.](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: 열거형 스토리지는 Int32여야 합니다.](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: 열거형에는 0 값이 있어야 합니다.](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: 열거형을 FlagsAttribute로 표시하세요.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
