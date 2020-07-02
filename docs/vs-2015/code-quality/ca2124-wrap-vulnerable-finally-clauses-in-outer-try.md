---
title: 'CA2124: 취약 한 finally 절을 외부 try에 래핑합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544302"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: 취약한 finally 절을 외부 try에 래핑하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 의 버전 1.0 및 1.1에서 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] public 또는 protected 메서드는 블록을 포함 `try` / `catch` / `finally` 합니다. `finally`블록이 보안 상태를 다시 설정 하는 것으로 표시 되 고 블록에 포함 되지 않습니다 `finally` .

## <a name="rule-description"></a>규칙 설명
 이 규칙은 `try` / `finally` [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 호출 스택에 있는 악성 예외 필터에 취약할 수 있는의 버전 1.0 및 1.1를 대상으로 하는 코드 블록을 찾습니다. Try 블록에서 가장과 같은 중요 한 작업이 발생 하 고 예외가 throw 되는 경우 필터는 블록 이전에 실행할 수 있습니다 `finally` . 가장 예제에서는 필터가 가장 된 사용자로 실행 됨을 의미 합니다. 필터는 현재 Visual Basic 에서만 구현 됩니다.

> [!WARNING]
> 2.0 이상 버전에서는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `try` / `catch` /  `finally` 예외가 예외 블록을 포함 하는 메서드 내에서 직접 다시 설정 되는 경우 런타임은 악성 예외 필터에서 블록을 자동으로 보호 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 래핑 되지 `try` / `finally` 않은를 외부 try 블록에 넣습니다. 다음 두 번째 예제를 참조 하세요. 이렇게 하면가 `finally` 필터 코드 보다 먼저 실행 됩니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="pseudo-code-example"></a>의사 코드 예제

### <a name="description"></a>설명
 다음 의사 코드에서는 이 규칙에 의해 검색되는 패턴을 보여 줍니다.

### <a name="code"></a>코드

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>예제
 다음 의사 코드는 코드를 보호 하 고이 규칙을 충족 하는 데 사용할 수 있는 패턴을 보여 줍니다.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
