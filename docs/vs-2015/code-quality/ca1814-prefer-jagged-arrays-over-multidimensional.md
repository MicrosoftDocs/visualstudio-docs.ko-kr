---
title: 'CA1814: 다차원 배열 보다 가변 배열을 선호 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ece9105e8a0a854837924e4a2d4f4ec485a5e202
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543938"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: 다차원 배열보다 가변 배열을 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|범주|Microsoft 성능|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 멤버가 다차원 배열로 선언 됩니다.

## <a name="rule-description"></a>규칙 설명
 가변 배열의 요소에는 배열이 사용됩니다. 요소를 구성하는 배열의 크기는 서로 다를 수 있습니다. 이 경우 일부 데이터 집합에 대한 공간을 절약할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 다차원 배열을 가변 배열로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 다차원 배열이 공간을 낭비 하지 않는 경우이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는 가변 및 다차원 배열에 대 한 선언을 보여 줍니다.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
