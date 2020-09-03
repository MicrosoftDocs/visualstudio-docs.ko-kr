---
title: 'CA2204: 리터럴의 철자가 정확 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ecf829251cbeab600cb95f8f0c0b0173cd7338d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546278"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: 리터럴의 맞춤법이 정확해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드는 지역화 된 문자열이 필요한 매개 변수 또는 속성에서 사용 되는에 리터럴 문자열을 전달 하 고, 리터럴 문자열에 Microsoft 맞춤법 검사 라이브러리에서 인식 하지 못하는 단어가 하나 이상 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 다음 중 하나 이상에 해당 하는 경우 매개 변수 또는 속성에 값으로 전달 되는 리터럴 문자열을 검사 합니다.

- <xref:System.ComponentModel.LocalizableAttribute>매개 변수 또는 속성의 특성이 true로 설정 되어 있습니다.

- 매개 변수 또는 속성 이름에 "Text", "Message" 또는 "Caption"이 포함 되어 있습니다.

- 콘솔에 전달 되는 문자열 매개 변수의 이름입니다. Write 또는 Console. WriteLine 메서드는 "value" 또는 "format"입니다.

  이 규칙은 리터럴 문자열을 단어로 구문 분석 하 고, 복합 단어를 토큰화 각 단어/토큰의 맞춤법을 검사 합니다. 구문 분석 알고리즘에 대 한 자세한 내용은 [CA1704: identifier의 철자가 정확한](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)지 확인 하세요.

  기본적으로 영어 (en) 버전의 맞춤법 검사기가 사용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 단어의 철자를 수정 하거나 사용자 지정 사전에 단어를 추가 합니다. 사용자 지정 사전을 사용 하는 방법에 대 한 자세한 내용은 [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md)을 참조 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 철자가 잘못 된 단어를 통해 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어듭니다.

## <a name="related-rules"></a>관련 규칙
 [CA1704: 식별자에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
