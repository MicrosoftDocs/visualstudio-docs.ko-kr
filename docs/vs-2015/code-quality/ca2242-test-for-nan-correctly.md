---
title: 'CA2242: NaN을 올바르게 테스트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0c832b7eb4a94506c5e15dfa5858bb9f6753912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546265"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: NaN에 대해 정확하게 테스트하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 식은 또는에 대해 값을 <xref:System.Single.NaN?displayProperty=fullName> 테스트 <xref:System.Double.NaN?displayProperty=fullName> 합니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Double.NaN?displayProperty=fullName>-숫자가 아닌를 나타내는 이며 산술 연산이 정의 되지 않은 경우에 발생 합니다. 값이 같은지 여부를 테스트 하 고 항상를 반환 하는 식입니다 <xref:System.Double.NaN?displayProperty=fullName> `false` . 값이 같지 않은지 테스트 하 고 항상를 반환 하는 식입니다 <xref:System.Double.NaN?displayProperty=fullName> `true` .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하 고 값이 나타내는지 여부를 정확 하 게 확인 하려면 <xref:System.Double.NaN?displayProperty=fullName> <xref:System.Single.IsNaN%2A?displayProperty=fullName> 또는 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 를 사용 하 여 값을 테스트 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예에서는에 대해 잘못 된 값을 테스트 하는 두 개의 식 <xref:System.Double.NaN?displayProperty=fullName> 과 값을 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 테스트 하기 위해 올바르게 사용 하는 식을 보여 줍니다.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
