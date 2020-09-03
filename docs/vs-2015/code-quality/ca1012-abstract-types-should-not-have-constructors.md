---
title: 'CA1012: 추상 형식에는 생성자를 사용할 수 없습니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2c88144e788fb35a3c330aa28b4e9d8b91ff8003
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545459"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: 추상 형식에는 생성자를 사용하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 Public 형식은 abstract 이며 public 생성자를 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 추상 형식에 대한 생성자는 파생된 형식에서만 호출할 수 있습니다. public 생성자에서 형식의 인스턴스를 만들고 사용자는 추상 형식의 인스턴스를 만들 수 없기 때문에 public 생성자가 있는 추상 형식은 잘못 디자인된 것입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 생성자를 protected로 설정 하거나 형식을 abstract로 선언 하지 마십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 추상 형식에 public 생성자가 있습니다.

## <a name="example"></a>예
 다음 예제에는이 규칙을 위반 하는 추상 형식이 포함 되어 있습니다.

 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/cs/FxCop.Design.AbstractTypeBad.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/vb/FxCop.Design.AbstractTypeBad.vb#1)]

## <a name="example"></a>예
 다음 예제에서는 생성자의 액세스 가능성을에서로 변경 하 여 이전 위반을 수정 합니다 `public` `protected` .

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/cs/FxCop.Design.AbstractTypeGood.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/vb/FxCop.Design.AbstractTypeGood.vb#1)]
