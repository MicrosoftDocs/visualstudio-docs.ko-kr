---
title: 'CA2225: 연산자 오버 로드에 대체 이름이 있습니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2dc43e92b92b6f963900057a76dfe88e38a3638f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545225"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: 연산자 오버로드에는 명명된 대체 항목이 있습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 연산자 오버로드가 감지되었으며 예상되는 이름의 대체 메서드를 찾을 수 없습니다.

## <a name="rule-description"></a>규칙 설명
 연산자 오버 로드를 사용 하면 기호를 사용 하 여 형식에 대 한 계산을 나타낼 수 있습니다. 예를 들어 더하기 기호 (+)를 오버 로드 하는 형식에는 일반적으로 ' Add ' 라는 대체 멤버가 있습니다. 명명 된 대체 멤버는 연산자와 같은 기능에 대 한 액세스를 제공 하며 오버 로드 된 연산자를 지원 하지 않는 언어로 프로그래밍 하는 개발자를 위해 제공 됩니다.

 이 규칙은 다음 표에 나열 된 연산자를 검사 합니다.

|C#|Visual Basic|C++|대체 이름|
|---------|------------------|-----------|--------------------|
|+ (이진)|+|+ (이진)|추가|
|+=|+=|+=|추가|
|&|and|&|BitwiseAnd|
|&=|및 =|&=|BitwiseAnd|
|&#124;|또는|&#124;|BitwiseOr|
|&#124;=|또는 =|&#124;=|BitwiseOr|
|--|해당 없음|--|감소|
|/|/|/|나누기|
|/=|/=|/=|나누기|
|==|=|==|같음|
|^|Xor|^|Xor|
|^=|Xor =|^=|Xor|
|>|>|>|비교|
|>=|>=|>=|비교|
|++|해당 없음|++|ID 증가값|
|<>|!=|같음|
|<<|<<|<<|왼쪽 shift|
|<<=|<<=|<<=|왼쪽 shift|
|<|<|<|비교|
|<=|<=|\<=|비교|
|&&|해당 없음|&&|LogicalAnd|
|&#124;&#124;|해당 없음|&#124;&#124;|LogicalOr|
|!|해당 없음|!|LogicalNot|
|%|Mod|%|Mod 또는 나머지가|
|%=|해당 없음|%=|Mod|
|* (이진)|*|*|곱하기|
|*=|해당 없음|*=|곱하기|
|~|Not|~|OnesComplement|
|>>|>>|>>|창에서|
=|해당 없음|>>=|창에서|
|-(이진)|-(이진)|-(이진)|빼기|
|-=|해당 없음|-=|빼기|
|true|IsTrue|해당 없음|IsTrue (속성)|
| - (단항)   |해당 없음|-|Negate|
|+ (단항)|해당 없음|+|더하기|
|false|IsFalse|False|IsTrue (속성)|

 해당 없음 = = 선택한 언어로 오버 로드 될 수 없습니다.

 또한이 규칙은 `SomeType` 및 라는 메서드를 확인 하 여 형식 ()에서 암시적 및 명시적 캐스트 연산자를 확인 합니다 `ToSomeType` `FromSomeType` .

 C #에서 이항 연산자가 오버 로드 되 면 해당 할당 연산자 (있는 경우)도 암시적으로 오버 로드 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 연산자에 대 한 대체 메서드를 구현 합니다. 권장 되는 대체 이름을 사용 하 여 이름을로 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 공유 라이브러리를 구현 하는 경우에는이 규칙의 경고를 표시 하지 마십시오. 응용 프로그램은이 규칙의 경고를 무시할 수 있습니다.

## <a name="example"></a>예
 다음 예제에서는이 규칙을 위반 하는 구조체를 정의 합니다. 예제를 수정 하려면 구조체에 공용 메서드를 추가 합니다 `Add(int x, int y)` .

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1046: 참조 형식에 같음 연산자를 오버로드하지 마세요.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: 연산자에는 대칭 오버로드가 있어야 합니다.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: 같음 연산자를 오버로드할 때 Equals를 재정의하세요.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Equals를 재정할 때 GetHashCode를 재정의하세요.](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
