---
title: 'CA1034: 중첩 형식은 표시 되지 않아야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04a982c993ffbb04a3e7600dfb93a00e80727b84
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542170"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: 중첩 형식은 노출되면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 노출 되는 형식에는 외부에서 볼 때 표시 되는 형식 선언이 포함 됩니다. 중첩 열거형 및 protected 형식은이 규칙에서 제외 됩니다.

## <a name="rule-description"></a>규칙 설명
 중첩 형식은 다른 형식의 범위 내에 선언 된 형식입니다. 중첩 형식은 포함 하는 형식의 개인 구현 세부 정보를 캡슐화 하는 데 유용 합니다. 이 용도로 사용할 경우 중첩 형식은 외부에 노출되면 안 됩니다.

 논리적 그룹화에 대해 외부에서 볼 수 있는 중첩 유형을 사용 하거나 이름 충돌을 방지 하려면 대신 네임 스페이스를 사용 합니다.

 중첩 형식에는 멤버 액세스 가능성 이라는 개념이 포함 되며 일부 프로그래머는 명확 하 게 이해할 수 없습니다.

 보호 된 형식은 미리 사용자 지정 시나리오에서 서브 클래스 및 중첩 형식에 사용할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 중첩 형식을 외부에서 볼 수 있도록 하려는 경우 형식의 액세스 가능성을 변경 합니다. 그렇지 않으면 부모에서 중첩 형식을 제거 합니다. 중첩의 목적이 중첩 된 형식을 범주화 하려면 네임 스페이스를 사용 하 여 계층을 만듭니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
