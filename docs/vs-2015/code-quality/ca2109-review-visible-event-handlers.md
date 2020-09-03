---
title: 'CA2109: visible 이벤트 처리기를 검토 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ddcab6e0f416837bcd7b01521a6d77ddce691b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520980"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: 표시되는 이벤트 처리기를 검토하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 public 또는 protected 이벤트 처리 메서드를 발견했습니다.

## <a name="rule-description"></a>규칙 설명
 외부에 노출 되는 이벤트 처리 메서드는 검토가 필요한 보안 문제를 제공 합니다.

 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다. 노출 된 메서드를 호출 하는 이벤트 처리기 인 대리자 형식은 처리기 및 이벤트 서명이 일치 하는 한 이벤트에 추가할 수 있습니다. 이벤트는 코드에 의해 발생할 수 있으며 단추 클릭과 같은 사용자 동작에 대 한 응답으로 항상 신뢰할 수 있는 시스템 코드에 의해 발생 하는 경우가 많습니다. 이벤트 처리 메서드에 보안 검사를 추가 해도 코드에서 메서드를 호출 하는 이벤트 처리기를 등록 하는 것을 방지할 수 없습니다.

 요청은 이벤트 처리기에 의해 호출 되는 메서드를 안정적으로 보호할 수 없습니다. 보안 요구는 호출 스택의 호출자를 검사 하 여 신뢰할 수 없는 호출자의 코드를 보호 하는 데 도움이 됩니다. 이벤트에 이벤트 처리기를 추가 하는 코드는 이벤트 처리기의 메서드가 실행 될 때 호출 스택에 반드시 있어야 하는 것은 아닙니다. 따라서 이벤트 처리기 메서드가 호출 될 때 호출 스택에는 항상 신뢰할 수 있는 호출자만 있을 수 있습니다. 이로 인해 이벤트 처리기 메서드에의 한 요청이 성공 합니다. 또한 메서드를 호출 하면 요청 된 사용 권한이 어설션 될 수 있습니다. 이러한 이유로 이벤트 처리 메서드를 검토 한 후에만이 규칙 위반 문제를 해결 하는 위험을 평가할 수 있습니다. 코드를 검토할 때 다음 문제를 고려 하십시오.

- 이벤트 처리기는 사용 권한 어설션 또는 비관리 코드 사용 권한 억제와 같이 위험 또는 악용이 가능한 모든 작업을 수행 합니까?

- 스택에서 항상 신뢰할 수 있는 호출자만을 사용 하 여 언제 든 지 실행할 수 있으므로 코드에서 발생 하는 보안 위협 요소는 무엇 인가요?

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드를 검토 하 고 다음을 평가 합니다.

- 이벤트 처리 메서드를 public이 아닌 것으로 만들 수 있나요?

- 모든 위험한 기능을 이벤트 처리기에서 이동할 수 있나요?

- 보안 요구가 적용 되는 경우 다른 방법으로이 작업을 수행할 수 있나요?

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 코드가 보안 위협에 노출 되지 않도록 신중한 보안 검토 후에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예
 다음 코드는 악의적인 코드에서 오용 될 수 있는 이벤트 처리 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [보안 요청](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
