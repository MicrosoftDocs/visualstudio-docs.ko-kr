---
title: 'CA2226: 연산자에는 대칭 오버 로드가 있어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 430a8d3cfd3b8ced45b60bd9dc70211711886d43
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540571"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: 연산자에는 대칭 오버로드가 있어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 형식이 같음 연산자 또는 같지 않음 연산자를 구현하면서 그 반대 연산자를 구현하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 같음 또는 같지 않음이 형식의 인스턴스에 적용 되 고 반대쪽 연산자는 정의 되지 않은 상황이 발생 하지 않습니다. 형식은 일반적으로 같음 연산자의 부정 값을 반환 하 여 같지 않음 연산자를 구현 합니다.

 C # 컴파일러는이 규칙의 위반에 대해 오류를 발생 시킵니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 같음 연산자와 같지 않음 연산자를 모두 구현 하거나 존재 하는 연산자를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 형식이와 일치 하는 방식으로 작동 하지 않습니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="related-rules"></a>관련 규칙
 [CA1046: 참조 형식에 같음 연산자를 오버로드하지 마세요.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: 연산자 오버로드에는 명명된 대체 항목이 있습니다.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: 같음 연산자를 오버로드할 때 Equals를 재정의하세요.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Equals를 재정할 때 GetHashCode를 재정의하세요.](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
