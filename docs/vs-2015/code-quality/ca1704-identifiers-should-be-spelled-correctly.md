---
title: 'CA1704: 식별자의 철자가 정확한 지 확인 하십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5e078fc1bb7fe247d541e7695e98c2de76c2466
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544068"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: 식별자에는 정확한 철자를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 식별자 이름에 Microsoft 맞춤법 검사 라이브러리에서 인식 하지 못하는 단어가 하나 이상 포함 되어 있습니다. 이 규칙은 get 및 set 속성 접근자와 같은 특수 명명 된 멤버나 생성자를 검사 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 식별자를 토큰으로 구문 분석 하 고 각 토큰의 맞춤법을 검사 합니다. 구문 분석 알고리즘은 다음 변환을 수행 합니다.

- 대문자는 새 토큰을 시작 합니다. 예를 들어 MyNameIsJoe 토큰화는 "My", "Name", "Is", "Joe"입니다.

- 대문자를 여러 개 사용할 경우 마지막 대문자는 새 토큰을 시작 합니다. 예를 들어, GUIEditor 토큰화을 "GUI", "Editor"로 변환할 수 있습니다.

- 선행 및 후행 아포스트로피는 제거 됩니다. 예를 들어 ' sender '는 "sender"로 토큰화.

- 밑줄은 토큰의 끝을 나타내고 제거 됩니다. 예를 들어, "Hello", "토큰화" Hello_world.

- 포함 된 앰퍼샌드는 제거 됩니다. 예를 들어&대/토큰화의 경우 "format"입니다.

  기본적으로 영어 (en) 버전의 맞춤법 검사기가 사용 됩니다. 현재 다른 언어 사전을 사용할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 단어의 철자를 수정 하거나 CustomDictionary.xml 라는 사용자 지정 사전에 단어를 추가 합니다. 도구, 프로젝트 디렉터리 또는 사용자의 프로필 아래에 있는 도구와 연결 된 디렉터리 (%USERPROFILE%\Application Data ...)의 설치 디렉터리에 사전을 추가 합니다. \\ 에서 프로젝트에 사용자 지정 사전을 추가 하는 방법에 대 한 자세한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 내용은 [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md) 을 참조 하세요.

- 사전/단어/인식 된 경로에서 위반을 발생 시 키 지 않아야 하는 단어를 추가 합니다.

- 사전/단어/인식할 수 없는 경로에서 위반을 발생 시켜야 하는 단어를 추가 합니다.

- 사전/단어/사용 되지 않는 경로에서 사용 되지 않는 것으로 플래그가 지정 되어야 하는 단어를 추가 합니다. 자세한 내용은 관련 규칙 항목 [CA1726: 선호 하는 용어 사용](../code-quality/ca1726-use-preferred-terms.md)을 참조 하세요.

- 머리글자어 대/소문자 구분 규칙에 대 한 예외를 Dictionary/머리글자어/CasingExceptions 경로에 추가 합니다.

  다음은 사용자 지정 사전 파일의 구조에 대 한 예입니다.

```
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 단어의 철자가 잘못 입력 되 고 word가 제한 된 라이브러리 집합에 적용 되는 경우에만이 규칙에서 경고를 표시 하지 않습니다. 철자가 잘못 된 단어를 입력 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어듭니다.

## <a name="related-rules"></a>관련 규칙
 [CA2204: 리터럴의 맞춤법이 정확해야 합니다.](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: 식별자에는 밑줄을 사용할 수 없습니다.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: 기본 설정 용어를 사용하세요.](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>관련 항목
 [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
