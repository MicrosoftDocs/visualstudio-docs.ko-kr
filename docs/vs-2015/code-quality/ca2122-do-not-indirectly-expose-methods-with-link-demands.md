---
title: 'CA2122: 링크 요청이 있는 메서드를 간접적으로 노출 하지 마십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 846ce010cddfd505bb967ec612a5c31dd8321977
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544328"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: 링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 Public 또는 protected 멤버에 [링크 요청이](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) 있으며 보안 검사를 수행 하지 않는 멤버에 의해 호출 됩니다.

## <a name="rule-description"></a>규칙 설명
 링크 요청은 직접 실행 호출자의 권한만 검사합니다. 멤버가 `X` 호출자의 보안 요구를 하지 않고 링크 요청에 의해 보호 되는 코드를 호출 하는 경우 필요한 권한이 없는 호출자는를 사용 `X` 하 여 보호 된 멤버에 액세스할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 링크 요청 시 보호 된 멤버에 대해 더 이상 보안 되지 않은 액세스를 제공 하지 않도록 멤버에 보안 [데이터와 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) 또는 링크 요청을 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 안전 하 게 표시 하지 않으려면 코드가 파괴적인 방식으로 사용할 수 있는 작업 또는 리소스에 대 한 액세스 권한을 호출자에 게 부여 하지 않도록 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 라이브러리 및 라이브러리의 약점을 보여 주는 응용 프로그램을 보여 줍니다. 샘플 라이브러리는 규칙을 위반 하는 두 가지 메서드를 제공 합니다. `EnvironmentSetting`메서드는 환경 변수에 대 한 무제한 액세스를 위해 링크 요청에 의해 보호 됩니다. 메서드는를 `DomainInformation` 호출 하기 전에 호출자의 보안 요구를 요구 하지 않습니다 `EnvironmentSetting` .

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램은 보안 되지 않은 라이브러리 멤버를 호출 합니다.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **보안 되지 않은 멤버의 값: seattle.corp.contoso.com**
## <a name="see-also"></a>참고 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
