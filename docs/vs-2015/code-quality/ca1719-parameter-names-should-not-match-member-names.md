---
title: 'CA1719: 매개 변수 이름은 멤버 이름과 일치 하지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545368"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: 매개 변수 이름은 멤버 이름과 달라야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|범주|Microsoft. 이름 지정|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 노출 되는 멤버의 이름 (대/소문자를 구분 하지 않는 비교)에서 해당 매개 변수 중 하나의 이름입니다.

## <a name="rule-description"></a>규칙 설명
 매개 변수 이름은 매개 변수의 의미를 나타내고 멤버 이름은 멤버의 의미를 나타내야 합니다. 매개 변수와 멤버의 의미가 같게 디자인되는 경우는 드뭅니다. 매개 변수의 이름을 멤버 이름과 동일하게 지정하는 것은 비직관적이고 라이브러리 사용을 어렵게 만듭니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 멤버 이름과 일치 하지 않는 매개 변수 이름을 선택 하십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 새 개발을 위해이 규칙에서 경고를 표시 하지 않아야 하는 알려진 시나리오가 발생 하지 않습니다. 배송 라이브러리의 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.

## <a name="related-rules"></a>관련 규칙
 [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: 식별자에는 밑줄을 사용할 수 없습니다.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
