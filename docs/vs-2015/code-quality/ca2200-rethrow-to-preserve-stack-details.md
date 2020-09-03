---
title: 'CA2200: 스택 정보를 유지 하도록 다시 Throw 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6d63ef6ff3647742e931fd05f59c66b40059ad00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546369"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: 스택 정보를 유지하도록 다시 throw하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 예외가 다시 throw 되 고 문에서 명시적으로 예외가 지정 됩니다 `throw` .

## <a name="rule-description"></a>규칙 설명
 예외가 throw 되 면 전달 되는 정보의 일부가 스택 추적입니다. 스택 추적은 예외를 throw 하 고 예외를 catch 하는 메서드로 끝나는 메서드 호출 계층 구조 목록입니다. 문에서 예외를 지정 하 여 예외를 다시 throw 하는 경우 `throw` 현재 메서드에서 스택 추적이 다시 시작 되 고 예외를 throw 한 원래 메서드 및 현재 메서드 간의 메서드 호출 목록이 손실 됩니다. 예외를 사용 하 여 원래 스택 추적 정보를 유지 하려면 `throw` 예외를 지정 하지 않고 문을 사용 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 예외를 명시적으로 지정 하지 않고 예외를 다시 throw 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 규칙을 위반 하는 메서드와 규칙을 충족 하는 메서드를 보여 줍니다 `CatchAndRethrowExplicitly` `CatchAndRethrowImplicitly` .

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
