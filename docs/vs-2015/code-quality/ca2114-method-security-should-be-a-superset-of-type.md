---
title: 'CA2114: 메서드 보안은 형식의 상위 집합 이어야 합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534708"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: 메서드 보안은 형식의 상위 집합이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식에 선언적 보안이 있고, 해당 메서드 중 하나에 동일한 보안 작업에 대 한 선언적 보안이 있고, 보안 작업이 [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) 또는 [상속 요구가](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)아닌 경우, 해당 형식에 의해 확인 된 사용 권한이 메서드에서 확인 된 사용 권한의 하위 집합이 아닌 경우

## <a name="rule-description"></a>규칙 설명
 메서드에는 동일한 작업에 대 한 메서드 수준과 형식 수준의 선언적 보안이 모두 포함 되어서는 안 됩니다. 두 검사는 결합 되지 않습니다. 메서드 수준 수요만 적용 됩니다. 예를 들어, 형식이 권한을 요청 하 `X` 고 해당 메서드 중 하나가 권한을 요청 하는 경우 `Y` 코드는 메서드를 실행할 수 있는 권한이 필요 하지 않습니다 `X` .

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 코드를 검토 하 여 두 동작이 모두 필요한 지 확인 합니다. 두 작업을 모두 수행 해야 하는 경우 메서드 수준 작업에 형식 수준에서 지정 된 보안이 포함 되어 있는지 확인 합니다. 예를 들어 형식에서 권한을 요청 하 `X` 고 해당 메서드에 권한도 요청 해야 하는 경우이 `Y` 메서드는 및을 명시적으로 요청 해야 합니다 `X` `Y` .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 메서드에 형식으로 지정 된 보안이 필요 하지 않은 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 그러나이는 일반적인 시나리오가 아니므로 신중 하 게 디자인을 검토 해야 하는 경우를 나타낼 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 환경 사용 권한을 사용 하 여이 규칙을 위반 하는 위험을 보여 줍니다. 이 예제에서 응용 프로그램 코드는 형식에 필요한 사용 권한을 거부 하기 전에 보안 형식의 인스턴스를 만듭니다. 실제 위협 시나리오에서는 응용 프로그램에서 개체의 인스턴스를 가져오는 다른 방법이 필요 합니다.

 다음 예제에서는 라이브러리에서 메서드에 대 한 읽기 권한 및 형식에 대 한 쓰기 권한을 요청 합니다.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램 코드는 형식 수준 보안 요구 사항을 충족 하지 않는 경우에도 메서드를 호출 하 여 라이브러리의 취약성을 보여 줍니다.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **[모든 권한] 개인 정보: 오전 6/16/1964 12:00:00** 
 **[쓰기 권한 없음 (형식으로 요청)] 개인 정보: 오전 6/16/1964 12:00:00** 
 **[읽기 권한 없음 (메서드에서 요청 함)] 개인 정보에 액세스할 수 없습니다. 요청이 실패 했습니다.**
## <a name="see-also"></a>참고 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [상속 요청](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
