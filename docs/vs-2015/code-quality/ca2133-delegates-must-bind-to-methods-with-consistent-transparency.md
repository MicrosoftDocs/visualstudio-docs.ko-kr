---
title: 'CA2133: 대리자는 투명도가 일관 된 메서드에 바인딩해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 12132622900d5698a6b78a1914c687a369d7dc03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547734"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: 대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

> [!NOTE]
> 이 경고는 CoreCLR (Silverlight 웹 응용 프로그램과 관련 된 CLR 버전)을 실행 하는 코드에만 적용 됩니다.

## <a name="cause"></a>원인
 이 경고는로 표시 된 대리자를 <xref:System.Security.SecurityCriticalAttribute> 투명 하거나로 표시 된 메서드에 바인딩하는 메서드에서 발생 합니다 <xref:System.Security.SecuritySafeCriticalAttribute> . 또한 투명하거나 안전에 중요한 대리자를 중요한 메서드에 바인딩하는 메서드에서도 이 경고가 발생합니다.

## <a name="rule-description"></a>규칙 설명
 대리자 형식 및 대리자 형식에 바인딩되는 메서드는 일관 된 투명도를 가져야 합니다. 투명 하 고 안전에 중요 한 대리자는 다른 투명 하거나 안전에 중요 한 메서드에만 바인딩할 수 있습니다. 마찬가지로 중요 한 대리자는 중요 한 메서드에만 바인딩할 수 있습니다. 이러한 바인딩 규칙은 대리자를 통해 메서드를 호출할 수 있는 코드의 경우에도 동일한 메서드를 직접 호출할 수 있는지 확인 합니다. 예를 들어 바인딩 규칙은 투명 코드가 투명 한 대리자를 통해 직접 중요 한 코드를 호출 하는 것을 방지 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 경고를 위반 하는 문제를 해결 하려면 대리자의 투명도 또는 대리자가 바인딩하는 메서드의 투명도를 변경 하 여 두 값의 투명도가 동일 하도록 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
