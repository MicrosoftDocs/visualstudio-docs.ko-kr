---
title: 'CA1707: 식별자에는 밑줄을 사용할 수 없습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe6b90ef971bd00392381f47860d85f34e10dc26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544029"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: 식별자에는 밑줄을 사용할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 [CA1707: 식별자에 밑줄을 사용할 수 없습니다](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).를 참조 하세요.

|항목|값|
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|범주|Microsoft. 이름 지정|
|변경 수준|중단-어셈블리에서 발생 하는 경우<br /><br /> 중단-형식 매개 변수에 대해 발생 하는 경우|

## <a name="cause"></a>원인
 식별자 이름에 밑줄 (_) 문자가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 규칙에 따라 식별자 이름에는 밑줄 문자(_)가 포함될 수 없습니다. 규칙은 네임 스페이스, 형식, 멤버 및 매개 변수를 확인 합니다.

 명명 규칙은 공용 언어 런타임을 대상으로 하는 라이브러리에 대 한 일반적인 모양을 제공 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 필요한 학습 곡선이 줄어들고, 관리 코드 개발에 대 한 전문 지식이 있는 사용자가 라이브러리를 개발 했을 때 고객의 자신감을 높일 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이름에서 밑줄 문자를 모두 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
