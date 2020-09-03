---
title: 'CA1032: 표준 예외 생성자를 구현 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542287"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: 표준 예외 생성자를 구현하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식은를 확장 <xref:System.Exception?displayProperty=fullName> 하 고 모든 필수 생성자를 선언 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 예외 형식은 다음 생성자를 구현 해야 합니다.

- public NewException ()

- public NewException (string)

- public NewException (string, Exception)

- protected 또는 private NewException (SerializationInfo, StreamingContext)

  이들 생성자 집합을 전부 제공하지 못하면 예외를 제대로 처리하기 어려울 수 있습니다. 예를 들어, 시그니처가 있는 생성자를 `NewException(string, Exception)` 사용 하 여 다른 예외에 의해 발생 하는 예외를 만듭니다. 이 생성자를 사용 하지 않으면 이러한 상황에서 관리 코드를 수행 해야 하는 내부 (중첩 된) 예외가 포함 된 사용자 지정 예외의 인스턴스를 만들고 throw 할 수 없습니다. 처음 세 개의 예외 생성자는 규칙에 따라 public입니다. 네 번째 생성자는 봉인 되지 않은 클래스에서 보호 되 고 sealed 클래스에서는 private입니다. 자세한 내용은 [CA2229: serialization 생성자 구현](../code-quality/ca2229-implement-serialization-constructors.md) 을 참조 하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 예외에 누락 된 생성자를 추가 하 고 올바른 액세스 가능성이 있는지 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 Public 생성자에 대해 다른 액세스 수준을 사용 하 여 위반이 발생 하는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예
 다음 예제에는이 규칙을 위반 하는 예외 형식과 올바르게 구현 된 예외 형식이 포함 되어 있습니다.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
