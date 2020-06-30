---
title: 'CA1702: 복합 단어는 대/소문자를 올바르게 지정 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f9dc15cec4012d2b63eb5f21c25bd709961c95c8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544081"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 CA1702을 참조 하세요. [복합 단어](/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly)는 대/소문자를 올바르게 지정 해야 합니다.

|항목|값|
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|범주|Microsoft. 이름 지정|
|변경 수준|중단-어셈블리에서 발생 한 경우<br /><br /> 형식 매개 변수에 대해 발생 하는 경우에는 중단 되지 않습니다.|

## <a name="cause"></a>원인
 식별자 이름에 여러 단어가 포함 되어 있으며, 단어 중 하나 이상이 대/소문자를 올바르게 나타내지 않는 복합 단어로 표시 됩니다.

## <a name="rule-description"></a>규칙 설명
 식별자의 이름은 대/소문자를 기준으로 하는 단어로 분할 됩니다. Microsoft 맞춤법 검사 라이브러리에서 연속 된 두 단어 조합을 확인 합니다. 인식 되는 경우 식별자는 규칙 위반을 생성 합니다. 위반을 야기 하는 복합 단어의 예로는 "CheckSum" 및 "MultiPart"가 있으며, 각각 "Checksum" 및 "Multipart"의 대/소문자를 지정 해야 합니다. 이전의 일반적인 사용으로 인해 규칙에 몇 가지 예외가 기본적으로 제공 되며, "도구 모음" 및 "파일 이름"과 같이 여러 개의 단일 단어가 플래그 지정 됩니다 (이 경우 "도구 모음" 및 "파일 이름").

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 대/소문자를 올바르게 변경 하려면 이름을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 복합 단어의 두 부분을 맞춤법 사전에서 인식 하 고 의도는 두 개의 단어를 사용 하는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>참고 항목
 [명명 지침](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) 의 [대문자 표기 규칙](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
