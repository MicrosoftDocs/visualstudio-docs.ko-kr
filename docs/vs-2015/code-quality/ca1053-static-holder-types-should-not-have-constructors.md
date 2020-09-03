---
title: 'CA1053: 정적 소유자 형식에는 생성자를 사용할 수 없습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 29cc322dd59dc0de66af8f92a46524d15b0022c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539583"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: 정적 소유자 형식에는 생성자를 사용하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 public 또는 중첩된 public 형식에서 정적 멤버만 선언하며 public 또는 protected 기본 생성자를 사용합니다.

## <a name="rule-description"></a>규칙 설명
 호출하는 정적 멤버에 형식의 인스턴스가 필요하지 않기 때문에 생성자가 필요 없습니다. 또한 형식이 비정적 멤버를 포함 하지 않기 때문에 인스턴스를 만들 때 형식의 멤버에 대 한 액세스 권한은 제공 되지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 기본 생성자를 제거 하거나 private으로 설정 합니다.

> [!NOTE]
> 일부 컴파일러는 형식이 생성자를 정의 하지 않는 경우 공용 기본 생성자를 자동으로 만듭니다. 이 경우 형식의 경우 전용 기본 생성자를 추가 하 여 위반을 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 생성자가 있으면 형식이 정적 형식이 아닌 것으로 제안 됩니다.

## <a name="example"></a>예
 다음 예제에서는이 규칙을 위반 하는 형식을 보여 줍니다. 소스 코드에 기본 생성자가 없습니다. 이 코드가 어셈블리로 컴파일될 때 c # 컴파일러는이 규칙을 위반 하는 기본 생성자를 삽입 합니다. 이를 해결 하려면 private 생성자를 선언 합니다.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
