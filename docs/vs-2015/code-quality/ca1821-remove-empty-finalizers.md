---
title: 'CA1821: 빈 종료자를 제거 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545355"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: 빈 종료자를 제거하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|범주|Microsoft 성능|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식은 비어 있거나 기본 형식 종료자만 호출 하거나 조건부로 내보낸 메서드만 호출 하는 종료자를 구현 합니다.

## <a name="rule-description"></a>규칙 설명
 개체 수명을 추적할 때에는 추가로 성능 오버헤드가 발생하므로 가능한 경우 종료자를 사용하지 마십시오. 가비지 수집기는 개체를 수집 하기 전에 종료자를 실행 합니다. 즉, 두 컬렉션은 개체를 수집 해야 합니다. 빈 종료자를 사용 하면 어떠한 이점도 없이 오버 헤드가 추가 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 빈 종료자를 제거 합니다. 디버깅에 종료자가 필요한 경우 전체 종료자를 지시문으로 묶습니다 `#if DEBUG / #endif` .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 메시지를 표시 하지 마십시오. 종료를 표시 하지 않으면 성능이 저하 되 고 아무런 이점도 제공 되지 않습니다.

## <a name="example"></a>예제
 다음 예제에서는 제거 해야 하는 빈 종료자, 지시문에 포함 되어야 하는 종료자 `#if DEBUG / #endif` 및 지시문을 올바르게 사용 하는 종료자를 보여 줍니다 `#if DEBUG / #endif` .

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
