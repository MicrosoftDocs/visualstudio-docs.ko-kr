---
title: 'CA2230: 가변 인수에 params를 사용 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540363"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: 가변 인수로 params를 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|범주|Microsoft 사용|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 또는 보호 된 형식에 호출 규칙을 사용 하는 public 또는 protected 메서드가 포함 되어 있습니다 `VarArgs` .

## <a name="rule-description"></a>규칙 설명
 `VarArgs`호출 규칙은 다양 한 매개 변수를 사용 하는 특정 메서드 정의와 함께 사용 됩니다. 호출 규칙을 사용 하는 메서드는 `VarArgs` CLS (공용 언어 사양) 규격이 아니고 프로그래밍 언어에서 액세스 하지 못할 수 있습니다.

 C #에서는 `VarArgs` 메서드의 매개 변수 목록이 키워드로 끝나는 경우 호출 규칙이 사용 됩니다 `__arglist` . Visual Basic는 `VarArgs` 호출 규칙을 지원 하지 않으며 Visual C++는 타원 표기법을 사용 하는 비관리 코드 에서만 사용할 수 있습니다 `...` .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 C #에서이 규칙 위반 문제를 해결 하려면 대신 [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) 키워드를 사용 `__arglist` 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 규칙을 위반 하는 메서드와 규칙을 충족 하는 두 가지 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [언어 독립성 및 언어 독립적 구성 요소](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
