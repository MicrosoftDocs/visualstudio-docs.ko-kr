---
title: 'CA2139: 투명 한 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 233e4366befd2a5a0d5690b14198ac13e2fcc957
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546486"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: 투명 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 투명 메서드는 특성으로 표시 됩니다 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> .

## <a name="rule-description"></a>규칙 설명
 이 규칙은 특성을 사용 하 여 프로세스 손상 예외를 처리 하려고 시도 하는 투명 한 모든 메서드를 발생 시킵니다 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> . 프로세스 손상 예외는 CLR 버전 4.0 예외 분류입니다 <xref:System.AccessViolationException> . HandleProcessCorruptedStateExceptionsAttribute 특성은 보안에 중요한 메서드에서만 사용할 수 있으며 투명 메서드에 적용되는 경우 무시됩니다. 프로세스 손상 예외를 처리 하려면이 메서드는 보안에 중요 하거나 보안 안전에 중요 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 특성을 제거 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 하거나 또는 특성을 사용 하 여 메서드를 표시 합니다 <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 이 예제에서 투명 메서드는 특성으로 표시 되 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 고 규칙은 실패 합니다. 또한 메서드는 또는 특성으로 표시 되어야 합니다 <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> .

 [!code-csharp[FxCop.Security.CA2139#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139/cs/ca2139.cs#1)]
