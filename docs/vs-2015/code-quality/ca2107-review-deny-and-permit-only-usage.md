---
title: 'CA2107: 거부를 검토 하 고 사용만 허용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f273ea5f58babf7a0c04f6b0758732d43aab7db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547773"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: deny 및 permit only 사용을 검토하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 메서드에는 PermitOnly 또는 Deny 보안 동작을 지정 하는 보안 검사가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 PermitOnly 메서드 및 보안 작업을 [사용 하](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) 는 것은 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> 보안에 대 한 고급 지식이 있는 사용자만 사용 해야 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . 이러한 보안 동작을 사용하는 코드는 보안 검토를 거쳐야 합니다.

 Deny는 보안 요청에 대 한 응답으로 발생 하는 스택 워크의 기본 동작을 변경 합니다. 호출 스택에 있는 호출자의 실제 사용 권한에 관계 없이 거부 메서드 기간에 대해 부여 되지 않아야 하는 사용 권한을 지정할 수 있습니다. 스택 워크에서 Deny로 보호 되는 메서드를 검색 하 고 요청 된 권한이 거부 된 권한에 포함 된 경우 스택 워크가 실패 합니다. 또한 PermitOnly는 스택 워크의 기본 동작을 변경 합니다. 호출자의 권한에 관계 없이 코드에서 부여할 수 있는 사용 권한만 지정할 수 있습니다. 스택 워크가 PermitOnly로 보호 되는 메서드를 검색 하 고 요청 된 권한이 PermitOnly로 지정 된 사용 권한에 포함 되지 않은 경우 스택 워크가 실패 합니다.

 이러한 작업에 의존 하는 코드는 제한 된 유용성 및 미묘한 동작으로 인해 보안 취약성에 대해 신중 하 게 평가 해야 합니다. 다음 사항을 고려합니다.

- [링크 요청](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) 은 Deny 또는 PermitOnly의 영향을 받지 않습니다.

- 스택 워크를 발생 시키는 요청과 동일한 스택 프레임에서 Deny 또는 PermitOnly가 발생 하는 경우 보안 작업은 아무런 영향을 주지 않습니다.

- 경로 기반 사용 권한을 구성 하는 데 사용 되는 값은 일반적으로 여러 가지 방법으로 지정할 수 있습니다. 특정 형식의 경로에 대 한 액세스를 거부 해도 모든 폼에 대 한 액세스를 거부 하는 것은 아닙니다. 예를 들어 파일 공유 \\ \Server\Share이 네트워크 드라이브 X:에 매핑되는 경우 공유 파일에 대 한 액세스를 거부 하려면 \\ \Server\Share\File, X:\File 및 파일에 액세스 하는 다른 모든 경로를 거부 해야 합니다.

- 는 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Deny 또는 PermitOnly에 도달할 때까지 스택 워크를 종료할 수 있습니다.

- Deny에 의해 차단 되는 사용 권한이 호출자에 게 적용 되는 경우, 즉 호출자는 거부를 무시 하 고 보호 된 리소스에 직접 액세스할 수 있습니다. 마찬가지로 호출자에 게 거부 된 권한이 없는 경우에는 거부 없이 스택 워크가 실패 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이러한 보안 동작을 사용 하면 위반이 발생 합니다. 위반 문제를 해결 하려면 이러한 보안 동작을 사용 하지 마십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 보안 검토를 완료 한 후에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제
 다음 예에서는 Deny의 몇 가지 제한 사항을 보여 줍니다.

 다음 라이브러리에는 두 개의 메서드를 보호 하는 보안 요구를 제외 하 고 동일한 두 개의 메서드를 포함 하는 클래스가 포함 되어 있습니다.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램은 라이브러리의 보안 방법에 대 한 Deny의 영향을 보여 줍니다.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **Demand: 호출자의 Deny는 어설션된 권한으로 요청에 영향을 주지 않습니다.** 
 **Linkdemand: 호출자의 Deny는 어설션된 권한이 있는 LinkDemand에 영향을 주지 않습니다.** 
 **Linkdemand: 호출자의 Deny는 linkdemand로 보호 된 코드에 영향을 주지 않습니다.** 
 **Linkdemand:이 거부는 LinkDemand로 보호 된 코드에는 적용 되지 않습니다.**
## <a name="see-also"></a>참고 항목
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 보안 [코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [PermitOnly 메서드를 사용 하 여](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) [보안 검사 재정의](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28)
