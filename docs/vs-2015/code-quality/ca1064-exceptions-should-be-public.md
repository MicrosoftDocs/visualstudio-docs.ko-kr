---
title: 'CA1064: 예외는 public 이어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc78c4eaacc3ef0a480b913d20537aeebe5bfc01
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539271"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: 예외는 public이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|범주|Microsoft 디자인|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 Public이 아닌 예외는, 또는에서 직접 파생 <xref:System.Exception> <xref:System.SystemException> <xref:System.ApplicationException> 됩니다.

## <a name="rule-description"></a>규칙 설명
 내부 예외는 자체 내부 범위 내부 에서만 볼 수 있습니다. 예외가 내부 범위 밖에 놓이게 되면 예외를 catch하는 데 기본 예외만 사용할 수 있습니다. 내부 예외에서 상속 되 면 <xref:System.Exception>, <xref:System.SystemException>, 또는 <xref:System.ApplicationException>, 외부 코드에 예외를 사용 하 여 수행할 작업을 알고에 충분 한 정보가 없습니다.

 그러나 코드에 나중에 내부 예외에 대 한 기준으로 사용 되는 공용 예외가 있는 경우 코드를 더 아웃 하면 기본 예외를 사용 하 여 지능적인 작업을 수행할 수 있다고 가정 하는 것이 합리적입니다. 공용 예외에는 T:System.Exception, T:System.SystemException 또는 T:System.ApplicationException.에서 제공 하는 것 보다 더 많은 정보가 포함 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 예외를 공용으로 설정 하거나, 또는이 아닌 공용 예외에서 내부 예외를 파생 <xref:System.Exception> 시킵니다 <xref:System.SystemException> <xref:System.ApplicationException> .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 모든 경우에 전용 예외가 자체 내부 범위 내에서 catch 될 것으로 확신 하는 경우에는이 규칙에서 메시지를 표시 하지 않습니다.

## <a name="example"></a>예제
 이 규칙은 예외 클래스가 예외에서 직접 파생 되 고 내부 이기 때문에 첫 번째 예제 메서드인 FirstCustomException에서 발생 합니다. 클래스는 예외에서 직접 파생 되 고 클래스가 public으로 선언 되기 때문에 SecondCustomException 클래스에서 규칙이 발생 하지 않습니다. 또한 세 번째 클래스는, 또는에서 직접 파생 되지 않으므로 규칙을 실행 하지 <xref:System.Exception?displayProperty=fullName> 않습니다 <xref:System.SystemException?displayProperty=fullName> <xref:System.ApplicationException?displayProperty=fullName> .

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
