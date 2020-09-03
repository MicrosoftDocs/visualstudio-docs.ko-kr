---
title: 'CA1005: 제네릭 형식에 대해 과도 한 매개 변수를 사용 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56c69badf76a05351b37a7c8a41a9cacf54f9974
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539726"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 노출 되는 제네릭 형식에는 두 개 이상의 형식 매개 변수가 있습니다.

## <a name="rule-description"></a>규칙 설명
 제네릭 형식에 포함된 형식 매개 변수가 많을수록 각 형식 매개 변수가 무엇을 나타내는지를 파악하거나 기억하기가 더 어렵습니다. 일반적으로에서와 같이 하나의 형식 매개 변수를 사용 하는 `List<T>` 경우와 같이 두 개의 형식 매개 변수를 사용 하는 것이 명확 `Dictionary<TKey, TValue>` 합니다. 세 개 이상의 형식 매개 변수가 있는 경우 대부분의 사용자에 게 어려움 (예: `TooManyTypeParameters<T, K, V>` c # 또는 `TooManyTypeParameters(Of T, K, V)` 의)이 너무 유용 합니다 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 두 개 이상의 형식 매개 변수를 사용 하도록 디자인을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 디자인에서 두 개 이상의 형식 매개 변수를 요구 하지 않는 한이 규칙에서 경고를 표시 하지 마십시오. 쉽게 이해 하 고 사용할 수 있는 구문에서 제네릭을 제공 하면 새 라이브러리의 도입 률을 배우고 늘리는 데 필요한 시간이 단축 됩니다.

## <a name="related-rules"></a>관련 규칙
 [CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: 제네릭 목록을 노출하지 마세요.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩하지 마세요.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드는 형식 매개 변수를 제공해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적합한 제네릭을 사용하세요.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>관련 항목
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
