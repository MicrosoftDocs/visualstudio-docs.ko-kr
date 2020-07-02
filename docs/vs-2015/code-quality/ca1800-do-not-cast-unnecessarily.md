---
title: 'CA1800: 불필요 하 게 캐스팅 하지 않음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547799"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: 불필요하게 캐스트하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|범주|Microsoft 성능|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드는 해당 인수 또는 지역 변수 중 하나에 대해 중복 캐스트를 수행 합니다. 이 규칙에의 한 전체 분석을 수행 하려면 디버깅 정보를 사용 하 여 테스트 된 어셈블리를 빌드해야 하며 연결 된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
 중복 캐스팅을 수행하면 성능이 저하됩니다. 특히 간단한 반복 문에서 캐스팅이 수행될 때 더욱 그러합니다. 명시적 중복 캐스트 작업의 경우 캐스트 결과를 지역 변수에 저장 하 고 중복 캐스트 작업 대신 지역 변수를 사용 합니다.

 `is`실제 캐스트를 수행 하기 전에 캐스팅이 성공할 지 여부를 테스트 하는 데 c # 연산자를 사용 하는 경우에는 연산자의 결과를 테스트 하는 것이 좋습니다 `as` . 이는 연산자가 수행 하는 암시적 캐스트 연산 없이 동일한 기능을 제공 합니다 `is` .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 캐스트 작업 수를 최소화 하도록 메서드 구현을 수정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 성능이 중요 하지 않은 경우이 규칙에서 경고를 표시 하지 않거나 규칙을 완전히 무시 해도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 c # 연산자를 사용 하 여 규칙을 위반 하는 메서드를 보여 줍니다 `is` . 두 번째 메서드는 연산자 `is` 의 결과에 대 한 테스트를 사용 하 여 연산자의 결과에 대 한 테스트로 연산자를 대체 하 여 규칙을 충족 시킵니다 `as` .

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하 `start_Click` 는 중복 된 명시적 캐스팅이 여러 개 있고 `reset_Click` 지역 변수에 캐스트를 저장 하 여 규칙을 충족 하는 메서드를 여러 개 포함 하는 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>참고 항목
 있는 [그대로](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
