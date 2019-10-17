---
title: 'CA2204: 리터럴의 맞춤법이 정확해야 합니다.'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6763fd9f8999bd590511026f6571db6a747c43bc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231851"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: 리터럴의 맞춤법이 정확해야 합니다.

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

리터럴 문자열은 지역화할 수 있는 매개 변수 또는 지역화 가능한 속성에 대 한 인수로 전달 되 고, 문자열에는 Microsoft 맞춤법 검사 라이브러리에서 인식 하지 못하는 단어가 하나 이상 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명

이 규칙은 다음 중 하나 이상에 해당 하는 경우 매개 변수 또는 속성에 값으로 전달 되는 리터럴 문자열을 검사 합니다.

- 매개 변수 또는 속성의 특성이true로설정되어있습니다.<xref:System.ComponentModel.LocalizableAttribute>

- 매개 변수 또는 속성 이름에 "Text", "Message" 또는 "Caption"이 포함 되어 있습니다.

- <xref:System.Console.Write%2A> 또는<xref:System.Console.WriteLine> 메서드에 전달 되는 문자열 변수의 이름은 "value" 또는 "format"입니다.

이 규칙은 리터럴 문자열을 단어로 구문 분석 하 고, 복합 단어를 토큰화 각 단어 또는 토큰의 맞춤법을 검사 합니다. 구문 분석 알고리즘에 대 한 자세한 내용은 [CA1704를 참조 하세요. 식별자의 철자가 정확한](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)지 확인 해야 합니다.

## <a name="language"></a>언어

맞춤법 검사기는 현재 영어 기반 문화권 사전에 대해서만 확인 합니다. **CodeAnalysisCulture** 요소를 추가 하 여 프로젝트 파일에서 프로젝트의 문화권을 변경할 수 있습니다.

예:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 문화권을 영어 기반 문화권 이외의 값으로 설정 하면이 코드 분석 규칙이 자동으로 사용 되지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 단어의 철자를 수정 하거나 사용자 지정 사전에 단어를 추가 합니다. 사용자 지정 사전을 [사용 하는 방법에 대 한 자세한 내용은 방법: 코드 분석 사전을](../code-quality/how-to-customize-the-code-analysis-dictionary.md)사용자 지정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이 규칙에서는 경고를 표시해야 합니다. 철자가 잘못 된 단어를 통해 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어듭니다.

## <a name="related-rules"></a>관련 규칙

- [CA1704: 식별자의 철자가 정확한 지 확인 해야 합니다.](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: 리소스 문자열의 철자가 정확한 지 확인 해야 합니다.](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)