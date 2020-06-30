---
title: 'CA1065: 예기치 않은 위치에서 예외를 발생 시 키 지 않음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ddfc95d27179f48aef9444819cc0437a3143d5a0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539258"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: 예기치 않은 위치에서 예외를 발생시키지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|범주|Microsoft 디자인|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 예외를 throw하지 않아야 하는 메서드가 예외를 throw했습니다.

## <a name="rule-description"></a>규칙 설명
 예외를 throw 하지 않을 것으로 예상 되는 메서드는 다음과 같이 분류할 수 있습니다.

- Property Get 메서드

- 이벤트 접근자 메서드

- Equals 메서드

- GetHashCode 메서드

- ToString 메서드

- 정적 생성자

- 종료자

- Dispose 메서드

- 같음 연산자

- 암시적 캐스트 연산자

  다음 섹션에서는 이러한 메서드 형식에 대해 설명 합니다.

### <a name="property-get-methods"></a>Property Get 메서드
 속성은 기본적으로 스마트 필드입니다. 따라서 필드는 가능한 한 필드 처럼 동작 합니다. 필드는 예외를 throw 하지 않으며 속성을 지정 하지 않습니다. 예외를 throw 하는 속성이 있는 경우 해당 속성을 메서드로 만드는 것이 좋습니다.

 다음 예외는 속성 get 메서드에서 throw 될 수 있습니다.

- <xref:System.InvalidOperationException?displayProperty=fullName>및 모든 파생 (포함 <xref:System.ObjectDisposedException?displayProperty=fullName> )

- <xref:System.NotSupportedException?displayProperty=fullName>및 all 파생

- <xref:System.ArgumentException?displayProperty=fullName>(인덱싱된 get 에서만)

- <xref:System.Collections.Generic.KeyNotFoundException>(인덱싱된 get 에서만)

### <a name="event-accessor-methods"></a>이벤트 접근자 메서드
 이벤트 접근자는 예외를 throw 하지 않는 간단한 작업 이어야 합니다. 이벤트는 이벤트 처리기를 추가 하거나 제거 하려고 할 때 예외를 throw 해서는 안 됩니다.

 다음 예외는 이벤트 accesor throw 될 수 있습니다.

- <xref:System.InvalidOperationException?displayProperty=fullName>및 모든 파생 (포함 <xref:System.ObjectDisposedException?displayProperty=fullName> )

- <xref:System.NotSupportedException?displayProperty=fullName>및 all 파생

- <xref:System.ArgumentException>및 파생물

### <a name="equals-methods"></a>Equals 메서드
 다음 **Equals** 메서드는 예외를 throw 해서는 안 됩니다.

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](https://msdn2.microsoft.com/library/ms131190(VS.80).aspx)

  **Equals** 메서드는 예외를 throw 하는 대신 또는를 반환 해야 합니다 `true` `false` . 예를 들어 Equals가 두 개의 일치 하지 않는 형식을 전달 하는 경우를 throw 하는 대신를 반환 해야 `false` <xref:System.ArgumentException> 합니다.

### <a name="gethashcode-methods"></a>GetHashCode 메서드
 다음 **GetHashCode** 메서드는 일반적으로 예외를 throw 하지 않아야 합니다.

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode (T)](https://msdn2.microsoft.com/library/system.collections.iequalitycomparer.gethashcode.aspx)

  **GetHashCode** 는 항상 값을 반환 해야 합니다. 그렇지 않으면 해시 테이블의 항목이 손실 될 수 있습니다.

  인수를 사용 하는 **GetHashCode** 버전은을 throw 할 수 있습니다 <xref:System.ArgumentException> . 그러나 **개체 GetHashCode** 는 예외를 throw 해서는 안 됩니다.

### <a name="tostring-methods"></a>ToString 메서드
 디버거에서는 <xref:System.Object.ToString%2A?displayProperty=fullName> 를 사용 하 여 개체에 대 한 정보를 문자열 형식으로 표시 합니다. 따라서 **ToString** 은 개체의 상태를 변경 하면 안 되며 예외를 throw 해서는 안 됩니다.

### <a name="static-constructors"></a>정적 생성자
 정적 생성자에서 예외를 throw 하면 현재 응용 프로그램 도메인에서 형식을 사용할 수 없게 됩니다. 정적 생성자에서 예외를 throw 하기 위한 매우 좋은 이유 (예: 보안 문제)가 있어야 합니다.

### <a name="finalizers"></a>종료자
 종료자에서 예외를 throw 하면 CLR이 신속 하 게 실패 하 여 프로세스가 중단 됩니다. 따라서 종료자에서 예외 throw는 항상 피해 야 합니다.

### <a name="dispose-methods"></a>Dispose 메서드
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>메서드는 예외를 throw 해서는 안 됩니다. Dispose는 절에서 정리 논리의 일부로 호출 되는 경우가 많습니다 `finally` . 따라서 Dispose에서 명시적으로 예외를 throw 하면 사용자가 절 내에서 예외 처리를 추가 하 게 `finally` 됩니다.

 **Dispose (false)** 코드 경로는 거의 항상 종료자에서 호출 되기 때문에 예외를 throw 해서는 안 됩니다.

### <a name="equality-operators--"></a>같음 연산자 (= =,! =)
 Equals 메서드와 마찬가지로 같음 연산자는 또는 중 하나를 반환 해야 하며 예외를 throw 해서는 안 됩니다 `true` `false` .

### <a name="implicit-cast-operators"></a>암시적 캐스트 연산자
 사용자는 암시적 캐스트 연산자가 호출 되었음을 인식 하지 못하는 경우가 많으므로 암시적 캐스트 연산자에 의해 throw 된 예외는 완전히 예기치 않은 것입니다. 따라서 암시적 캐스트 연산자에서 예외가 throw 되어서는 안 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 속성 getter의 경우 더 이상 예외를 throw 할 필요가 없도록 논리를 변경 하거나 속성을 메서드로 변경 합니다.

 이전에 나열 된 다른 모든 메서드 형식의 경우 더 이상 예외를 throw 하지 않도록 논리를 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 위반이 throw 된 예외 대신 예외 선언에 의해 발생 한 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA2219: exception 절에서 예외를 발생시키지 마세요.](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>참고 항목
 [디자인 경고](../code-quality/design-warnings.md)
