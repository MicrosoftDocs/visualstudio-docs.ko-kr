---
title: 'CA2123: Override 링크 요청은 base |와 동일 해야 합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a722eb95561a1a81b0d17b8876df8b4bac048b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544263"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: 재정의 링크 요청은 기본 링크 요청과 같아야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 형식의 public 또는 protected 메서드는 메서드를 재정의 하거나 인터페이스를 구현 하며 인터페이스 또는 가상 메서드와 동일한 [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) 을 포함 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 메서드를 다른 형식의 인터페이스이거나 가상 메서드인 기본 메서드에 일치시킨 다음 각각에 대해 링크 요청을 비교합니다. 메서드나 기본 메서드에 링크 요청이 있고 다른에는 없는 경우 위반이 보고 됩니다.

 이 규칙이 위반 되 면 악의적인 호출자가 보안 되지 않은 메서드를 호출 하 여 링크 요청을 우회할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 재정의 메서드나 구현에 동일한 링크 요청을 적용 합니다. 가능 하지 않은 경우 메서드를 전체 요청으로 표시 하거나 특성을 모두 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는이 규칙에 대 한 다양 한 위반을 보여 줍니다.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>관련 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [링크 요구](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
