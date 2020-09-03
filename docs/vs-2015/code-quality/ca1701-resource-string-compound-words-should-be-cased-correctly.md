---
title: 'CA1701: 리소스 문자열 복합 단어는 대/소문자를 올바르게 지정 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7c1c3b0fd6cf3a25d5db9e3039d4dc5d8364a18e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544107"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|범주|Microsoft. 이름 지정|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 리소스 문자열에는 대/소문자를 올바르게 표시 하지 않는 복합 단어가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 리소스 문자열의 각 단어는 대/소문자를 기반으로 하는 토큰으로 분할 됩니다. Microsoft 맞춤법 검사 라이브러리에서는 연속된 각 두 토큰의 조합을 검사합니다. 규칙 위반이 인식되면 단어에서 규칙 위반을 작성합니다. 위반을 야기 하는 복합 단어의 예로는 "CheckSum" 및 "MultiPart"가 있으며, 각각 "Checksum" 및 "Multipart"의 대/소문자를 지정 해야 합니다. 이전의 일반적인 사용으로 인해 몇 가지 예외가 규칙에 기본 제공 되 고, "도구 모음" 및 "파일 이름"과 같이 여러 개의 단어에 플래그가 지정 되며,이는 서로 다른 두 단어로만 대/소문자를 지정 해야 합니다. 이 예제에서는 "도구 모음" 및 "파일 이름"에 플래그가 지정 됩니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 단어의 대/소문자를 정확 하 게 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 복합 단어의 두 부분을 맞춤법 사전에서 인식 하 고 의도는 두 개의 단어를 사용 하는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

 맞춤법 검사기의 사용자 지정 사전에 복합 단어를 추가할 수도 있습니다. 사용자 지정 사전의 단어는 위반을 발생 시 키 지 않습니다. 자세한 내용은 [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md)을 참조 하세요.

## <a name="related-rules"></a>관련 규칙
 [CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>관련 항목
 [대문자 표기 규칙](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [명명 지침](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
