---
title: 'CA1031: 일반적인 예외 형식을 catch 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542404"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: 일반적인 예외 형식을 catch하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 또는와 같은 일반 예외 <xref:System.Exception?displayProperty=fullName> 는 <xref:System.SystemException?displayProperty=fullName> `catch` 문에 catch 되거나와 같은 일반 catch 절 `catch()` 이 사용 됩니다.

## <a name="rule-description"></a>규칙 설명
 일반 예외는 catch하면 안 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 보다 구체적인 예외를 catch 하거나 일반 예외를 블록의 마지막 문으로 다시 throw 합니다 `catch` .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 일반적인 예외 형식을 catch 하면 라이브러리 사용자의 런타임 문제를 숨기고 디버깅을 더 어렵게 만들 수 있습니다.

> [!NOTE]
> [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)]부터 시작해서, CLR(공용 언어 런타임)은 관리 코드에서 처리되어야 하는 [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]의 액세스 위반과 같이 운영 체제 및 관리 코드에서 발생하는 손상된 상태 예외를 더 이상 제공하지 않습니다. 이상 버전에서 응용 프로그램을 컴파일하고 손상 된 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 상태 예외 처리를 유지 하려는 경우 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 손상 된 상태 예외를 처리 하는 메서드에 특성을 적용할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 형식과 블록을 올바르게 구현 하는 형식을 보여 줍니다 `catch` .

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2200: 스택 정보를 유지하도록 다시 throw하십시오.](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
