---
title: 'CA1703: 리소스 문자열의 철자가 정확 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e720c1c491e88b6d89fb4b1f0175e8bc8a56e27
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544055"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|범주|Microsoft. 이름 지정|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 리소스 문자열에 Microsoft 맞춤법 검사 라이브러리에서 인식하지 못하는 단어가 하나 이상 있습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 리소스 문자열을 단어 (토큰화 복합 단어)로 구문 분석 하 고 각 단어/토큰의 맞춤법을 검사 합니다. 구문 분석 알고리즘에 대 한 자세한 내용은 [CA1704: identifier의 철자가 정확한](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)지 확인 하세요.

 기본적으로 영어 (en) 버전의 맞춤법 검사기가 사용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 올바른 철자의 단어 전체를 사용 하거나 사용자 지정 사전에 단어를 추가 합니다. 사용자 지정 사전을 사용 하는 방법에 대 한 자세한 내용은 [CA1704: identifier의 철자가](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)정확한 지 확인 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 철자가 잘못 된 단어를 통해 새 소프트웨어 라이브러리를 학습 하는 데 필요한 시간을 줄일 수 있습니다.

## <a name="related-rules"></a>관련 규칙
 [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: 식별자에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: 리터럴의 맞춤법이 정확해야 합니다.](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
