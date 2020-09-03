---
title: 보안 경고 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.securityrules
helpviewer_keywords:
- security [Visual Studio ALM], Enterprise Templates
- security warnings
- managed code analysis warnings, security warnings
- warnings, security
ms.assetid: 60d4e8ea-230a-494f-aa6a-b91db77540e4
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5e30768ac6fa8c3c140156b94082bb2306efb51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655196"
---
# <a name="security-warnings"></a>보안 경고
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

보안 경고는 더 안전한 라이브러리 및 애플리케이션을 지원합니다. 이들 경고는 프로그램의 보안 결함을 방지하는 데 도움이 됩니다. 이들 경고를 비활성화하는 경우 코드에 그 이유를 명확하게 표시하고 개발 프로젝트의 지정된 보안 담당자에게 이 사실을 알려야 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA2100: 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|메서드가 메서드에 대한 문자열 인수로부터 만들어진 문자열을 사용하여 System.Data.IDbCommand.CommandText 속성을 설정합니다. 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다.|
|[CA2102: 일반 처리기에서 비 CLSCompliant 예외를 catch하세요.](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|RuntimeCompatibilityAttribute로 표시되지 않거나 RuntimeCompatibility(WrapNonExceptionThrows = false)로 표시된 어셈블리의 멤버에는 System.Exception을 처리하는 catch 블록이 포함되며 바로 뒤의 일반 catch 블록은 포함되지 않습니다.|
|[CA2103: 명령적 보안을 검토하세요.](../code-quality/ca2103-review-imperative-security.md)|메서드가 명령적 보안을 사용하고, 요청이 활성 상태인 동안 변경될 수 있는 반환 값 또는 상태 정보를 사용하여 권한을 구성하고 있습니다. 가능하면 선언적 보안을 사용합니다.|
|[CA2104: 변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|외부에서 볼 수 있는 형식에 변경 가능한 참조 형식인, 외부에서 볼 수 있는 읽기 전용 필드가 포함되었습니다. 변경 가능한 형식은 해당 인스턴스 데이터를 수정할 수 있는 형식을 말합니다.|
|[CA2105: 배열 필드는 읽기 전용이면 안 됩니다.](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|배열이 들어 있는 필드에 read-only(Visual Basic의 경우 ReadOnly) 한정자를 적용하면 필드를 변경하여 다른 배열을 참조할 수 없습니다. 그러나 읽기 전용 필드에 저장된 배열의 요소는 변경할 수 있습니다.|
|[CA2106: 어설션을 안전하게 보호하세요.](../code-quality/ca2106-secure-asserts.md)|메서드에서 권한을 어설션하는데 호출자에 대해 보안 검사가 수행되지 않습니다. 보안 검사를 수행하지 않고 보안 권한을 어설션하면 코드에 보안상 취약한 부분이 남아 있을 수 있습니다.|
|[CA2107: deny 및 permit only 사용을 검토하세요.](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|PermitOnly 메서드와 CodeAccessPermission.Deny 보안 동작은 .NET Framework 보안에 대해 잘 알고 있는 경우에만 사용해야 합니다. 이러한 보안 동작을 사용하는 코드는 보안 검토를 거쳐야 합니다.|
|[CA2108: 값 형식에서 선언적 보안을 검토하십시오.](../code-quality/ca2108-review-declarative-security-on-value-types.md)|public 또는 protected 값 형식이 데이터 액세스 또는 링크 요청에 의해 보안됩니다.|
|[CA2109: 표시되는 이벤트 처리기를 검토하세요.](../code-quality/ca2109-review-visible-event-handlers.md)|public 또는 protected 이벤트 처리 메서드를 발견했습니다. 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다.|
|[CA2111: 포인터는 노출되면 안 됩니다.](../code-quality/ca2111-pointers-should-not-be-visible.md)|포인터가 전용, 내부 또는 읽기 전용이 아닙니다. 악의적인 코드에서는 해당 포인터 값을 변경하여 메모리 내 임의의 위치에 액세스할 수 있게 되거나 애플리케이션 또는 시스템 오류를 발생시킬 수 있습니다.|
|[CA2112: 보안 형식은 필드를 노출하면 안 됩니다.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|public 또는 protected 형식이 public 필드를 포함하고 링크 요청에 의해 보안됩니다. 코드에 링크 요청으로 보안된 형식의 인스턴스에 대한 액세스 권한이 있으면 코드에서 링크 요청을 만족하지 않아도 해당 형식의 필드에 액세스할 수 있습니다.|
|[CA2114: 메서드 보안은 형식의 상위 집합이어야 합니다.](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|메서드에는 같은 동작에 대해 메서드 수준과 형식 수준의 선언적 보안이 모두 있으면 안 됩니다.|
|[CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|이 규칙에서는 관리되지 않는 리소스가 비관리 코드에서 여전히 사용되고 있는데 종료되려고 할 경우 발생할 수 있는 오류를 감지합니다.|
|[CA2116: APTCA 메서드는 APTCA 메서드만 호출해야 합니다.](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|완전히 신뢰할 수 있는 어셈블리에 APTCA(AllowPartiallyTrustedCallers) 특성이 있고 이 어셈블리가 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 다른 어셈블리의 코드를 실행하면 보안상 위험할 수 있습니다.|
|[CA2117: APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|완전히 신뢰할 수 있는 어셈블리에 APTCA(AllowPartiallyTrustedCallers) 특성이 있고 이 어셈블리의 형식이 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 형식에서 상속되면 보안상 위험할 수 있습니다.|
|[CA2118: SuppressUnmanagedCodeSecurityAttribute 사용을 검토하세요.](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|SuppressUnmanagedCodeSecurityAttribute는 COM interop 또는 플랫폼 호출을 사용하는 비관리 코드를 실행하는 멤버에 대해 기본 보안 시스템 동작을 변경합니다. 이 특성은 기본적으로 성능 향상을 위해 사용되지만 성능이 향상되는 대신 중대한 보안 위험이 발생합니다.|
|[CA2119: private 인터페이스를 만족하는 메서드를 봉인하세요.](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|상속할 수 있는 public 형식에서는 internal(Visual Basic의 경우 Friend) 인터페이스의 재정의 가능한 메서드 구현을 제공합니다. 이 규칙 위반 문제를 해결하려면 어셈블리 외부에서 메서드가 재정의되지 않도록 합니다.|
|[CA2120: serialization 생성자를 안전하게 하세요.](../code-quality/ca2120-secure-serialization-constructors.md)|이 형식에는 System.Runtime.Serialization.SerializationInfo 개체와 System.Runtime.Serialization.StreamingContext 개체(serialization 생성자 서명)를 사용하는 생성자가 있습니다. 이 생성자는 보안 검사를 통해 보안되지 않지만 형식에 있는 하나 이상의 정규 생성자가 보안됩니다.|
|[CA2121: 정적 생성자는 private이어야 합니다.](../code-quality/ca2121-static-constructors-should-be-private.md)|시스템에서는 형식의 첫 번째 인스턴스가 만들어지거나 static 멤버가 참조되기 전에 static 생성자를 호출합니다. static 생성자가 private이 아니면 시스템 이외의 코드에서 이를 호출할 수 있습니다. 이렇게 되면 생성자에서 수행하는 작업에 따라 예기치 않은 동작이 발생할 수 있습니다.|
|[CA2122: 링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|public 또는 protected 멤버에 링크 요청이 있으며 해당 멤버가 보안 검사를 수행하지 않는 멤버에 의해 호출됩니다. 링크 요청은 직접 실행 호출자의 권한만 검사합니다.|
|[CA2123: 재정의 링크 요청은 기본 링크 요청과 같아야 합니다.](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|이 규칙에서는 메서드를 다른 형식의 인터페이스이거나 가상 메서드인 기본 메서드에 일치시킨 다음 각각에 대해 링크 요청을 비교합니다. 이 규칙이 위반되면 악의적인 호출자가 보안되지 않은 메서드를 호출함으로써 링크 요청을 우회할 수 있습니다.|
|[CA2124: 취약한 finally 절을 외부 try에 래핑하십시오.](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|public 또는 protected 메서드에 try/finally 블록이 들어 있습니다. finally 블록이 보안 상태를 다시 설정하는 것으로 나타나며 finally 블록에 포함되어 있지 않습니다.|
|[CA2126: 형식 링크 요청에는 상속 요청이 필요합니다.](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|public unsealed 형식이 링크 요청으로 보호되며 재정의 가능한 메서드를 포함합니다. 형식이나 메서드는 모두 상속 요청으로 보호됩니다.|
|[CA2136: 멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|100% 투명 어셈블리에서는 중요 코드가 나타날 수 없습니다. 이 규칙은 형식, 필드 및 메서드 수준에서 100% 투명 어셈블리의 SecurityCritical 주석을 분석합니다.|
|[CA2147: 투명 메서드는 보안 어설션을 사용할 수 없습니다.](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|이 규칙은 100% 투명 어셈블리나 투명/중요 혼합 어셈블리의 모든 메서드와 형식을 분석하고 선언적이거나 명령적인 어설션 사용에 플래그를 지정합니다.|
|[CA2140: 투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|SecurityTransparentAttribute로 표시된 메서드가 SecurityCritical로 표시된 public이 아닌 멤버를 호출합니다. 이 규칙은 투명/중요 혼합 어셈블리의 모든 메서드와 형식을 분석하고 투명 코드에서 SecurityTreatAsSafe로 표시되지 않은 public이 아닌 중요 코드를 대상으로 하는 모든 호출을 플래그합니다.|

|[CA2130: 보안에 중요한 상수는 투명해야 합니다.](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|런타임에 조회가 필요하지 않도록 컴파일러에서 상수 값을 인라인하기 때문에 상수 값에 투명성이 적용되지 않습니다. 상수 필드는 보안 투명해야 하므로 코드 검토자는 투명 코드가 상수에 액세스할 수 없다고 가정하지 않습니다.|
|-----------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|[CA2131: 보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|형식이 형식 동등에 참여하는데, 해당 형식 자체 또는 해당 형식의 멤버나 필드가 SecurityCriticalAttribute 특성으로 표시되어 있습니다. 이 규칙은 중요한 형식 또는 중요한 메서드나 필드를 포함하는 형식이 형식 동등에 참여하는 경우에 적용됩니다. CLR에서 이러한 형식이 검색되면 런타임에 해당 형식이 로드되지 않고 TypeLoadException이 throw됩니다. 일반적으로 이 규칙은 사용자가 tlbimp와 컴파일러를 이용하여 형식 동등을 수행하지 않고 수동으로 형식 동등을 구현하는 경우에만 적용됩니다.|
|[CA2132: 기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|SecurityCriticalAttribute가 있는 형식 및 멤버는 Silverlight 애플리케이션 코드에서 사용할 수 없습니다. 보안에 중요한 형식 및 멤버는 .NET Framework for Silverlight 클래스 라이브러리의 신뢰할 수 있는 코드에서만 사용할 수 있습니다. 파생 클래스의 public 또는 protected 구성 요소는 투명성이 기본 클래스보다 높거나 같아야 하기 때문에 애플리케이션의 클래스는 SecurityCritical로 표시된 클래스에서 파생될 수 없습니다.|
|[CA2133: 대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|이 경고는 SecurityCriticalAttribute를 사용하여 표시된 대리자를 SecuritySafeCriticalAttribute를 사용하여 표시되거나 투명한 메서드에 바인딩하는 메서드에서 발생합니다. 또한 투명하거나 안전에 중요한 대리자를 중요한 메서드에 바인딩하는 메서드에서도 이 경고가 발생합니다.|
|[CA2134: 메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|이 규칙은 SecurityCriticalAttribute로 표시된 메서드가 SecuritySafeCriticalAttribute로 표시되거나 투명한 메서드를 재정의할 때 적용됩니다. 또한 SecuritySafeCriticalAttribute로 표시되거나 투명한 메서드가 SecurityCriticalAttribute로 표시된 메서드를 재정의할 때도 이 규칙이 적용됩니다. 이 규칙은 가상 메서드를 재정의하거나 인터페이스를 구현할 때 적용됩니다.|
|[CA2135: 수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|LinkDemands는 수준 2 보안 규칙 집합에서 사용되지 않습니다. JIT(Just-in-Time) 컴파일 시 보안을 적용하는 데 LinkDemands를 사용하는 대신, 해당 메서드, 형식 및 필드를 SecurityCriticalAttribute 특성으로 표시하세요.|
|[CA2136: 멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|투명성 특성은 큰 범위의 코드 요소에서 작은 범위의 요소에 적용됩니다. 범위가 큰 코드 요소의 투명성 특성은 첫 번째 요소에 포함된 코드 요소의 투명성 특성보다 우선합니다. 예를 들어 SecurityCriticalAttribute 특성으로 표시된 클래스에는 SecuritySafeCriticalAttribute 특성으로 표시된 메서드가 포함될 수 없습니다.|
|[CA2137: 투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|메서드가 확인할 수 없는 코드를 포함하거나 형식을 참조로 반환합니다. 이 규칙은 보안 투명 코드에서 확인할 수 없는 MSIL(Microsoft Intermediate Language)을 실행하려고 할 때 적용됩니다. 그러나 이 규칙은 완전한 IL 검증 도구를 포함하지 않으며 대신 추론을 사용하여 MSIL 확인 시 대부분의 위반을 catch합니다.|
|[CA2138: 투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|보안 투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 표시된 메서드를 호출합니다.|
|[CA2139: 투명 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다.](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|이 규칙은 HandleProcessCorruptedStateExceptionsAttribute 특성을 사용하여 프로세스 손상 예외를 처리하려고 시도하는 모든 투명한 메서드에 적용됩니다. 프로세스 손상 예외는 AccessViolationException과 같은 예외의 CLR 버전 4.0 예외 분류입니다. HandleProcessCorruptedStateExceptionsAttribute 특성은 보안에 중요한 메서드에서만 사용할 수 있으며 투명 메서드에 적용되는 경우 무시됩니다.|
|[CA2140: 투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|SecurityCriticalAttribute 특성으로 표시된 코드 요소는 보안에 중요합니다. 투명 메서드는 보안에 중요한 요소를 사용할 수 없습니다. 투명 형식이 보안에 중요한 형식을 사용하려고 시도하는 경우 TypeAccessException, MethodAccessException 또는 FieldAccessException이 발생합니다.|
|[CA2141: 투명한 메서드는 LinkDemands를 충족해서는 안 됩니다](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|보안 투명 메서드가 APTCA(AllowPartiallyTrustedCallersAttribute) 특성으로 표시되지 않은 어셈블리의 메서드를 호출하거나, 보안 투명 메서드가 형식 또는 메서드에 대한 LinkDemand를 충족합니다.|
|[CA2142: 투명 코드는 LinkDemands로 보호될 수 없습니다.](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|이 규칙은 액세스하는 데 LinkDemands가 필요한 투명한 메서드에 적용됩니다. 보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다.|
|[CA2143: 투명 메서드는 보안 요청을 사용할 수 없습니다.](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다. 보안 투명 코드는 보안에 중요한 결정을 내리는 데 전체 요청을 사용해야 하며 안전에 중요한 코드는 전체 요청을 위해 투명 코드를 사용해서는 안 됩니다.|
|[CA2144: 투명 코드는 바이트 배열에서 어셈블리를 로드할 수 없습니다.](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|투명 코드는 보안에 중요한 동작을 수행할 수 없기 때문에 투명 코드의 보안 검토는 중요 코드에 대한 보안 검토만큼 완벽하지 않습니다. 바이트 배열에서 로드된 어셈블리는 투명 코드에서 발견되지 않을 수 있으며 해당 바이트 배열은 감사할 필요가 없는 중요하거나 특히 안전에 중요한 코드를 포함할 수 있습니다.|
|[CA2145: 투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅할 수 없습니다.](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅된 메서드에 이를 호출하는 메서드에 대한 암시적 LinkDemand가 배치되어 있습니다. 이 LinkDemand는 호출 코드가 보안을 중요시 하도록 요구합니다. SuppressUnmanagedCodeSecurity를 사용하는 메서드를 SecurityCriticalAttribute 특성으로 표시하면 이 요구 사항이 메서드 호출자에 더욱 명확하게 전달됩니다.|
|[CA2146: 형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|이 규칙은 파생 형식에 기본 형식 또는 구현된 인터페이스만큼 중요하지 않은 보안 투명성 특성이 있을 때 적용됩니다. 중요한 기본 형식에서 파생되거나 중요한 인터페이스를 구현할 수 있는 것은 중요한 형식뿐이고, 안전에 중요한 기본 형식에서 파생되거나 안전에 중요한 인터페이스를 구현할 수 있는 것은 중요하거나 안전에 중요한 형식뿐입니다.|
|[CA2147: 투명 메서드는 보안 어설션을 사용할 수 없습니다.](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|SecurityTransparentAttribute로 표시된 코드에는 어설션하는 데 필요한 권한이 부여되지 않습니다.|
|[CA2149: 투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|이 규칙은 P/Invoke를 통해 네이티브 코드를 직접 호출하는 모든 투명 메서드에 적용됩니다. 이 규칙이 위반되면 수준 2 투명성 모델에서 MethodAccessException이 발생하고 수준 1 투명성 모델에서 UnmanagedCode에 대한 완전 요청이 발생합니다.|
|[CA2151: 중요한 형식이 포함된 필드는 보안에 중요한 필드여야 합니다.](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md)|보안 중요 형식을 사용하려면 이 형식을 참조하는 코드가 보안 중요 또는 보안 안전 중요여야 합니다. 참조가 간접적인 경우에도 마찬가지입니다. 따라서 투명 코드는 필드에 액세스할 수 없으므로 보안 투명 또는 보안 안전 중요 필드가 있을 경우 잘못 해석됩니다.|
|[CA5122 P/Invoke 선언이 안전 하 게 중요 한 것은 아닙니다.](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md)|메서드는 보안에 중요한 작업을 수행할 때 SecuritySafeCritical로 표시되지만, 투명 코드에서도 안전하게 사용할 수 있습니다. 투명 코드는 P/Invoke를 통해 절대 네이티브 코드를 직접 호출할 수 없습니다. 따라서 P/Invoke를 SecuritySafeCritical로 표시할 경우 투명 코드가 P/Invoke를 호출할 수 없으며, 보안 분석에서 잘못 해석하는 원인이 됩니다.|
|[CA2153: 손상된 상태 예외를 처리하지 마세요.](../code-quality/ca2153-avoid-handling-corrupted-state-exceptions.md)|[CSE(손상된 상태 예외)](https://msdn.microsoft.com/magazine/dd419661.aspx) 는 프로세스에 메모리 손상이 있음을 나타냅니다. 프로세스 충돌을 허용하는 대신 catch하면 공격자가 손상된 메모리 영역에 익스플로잇을 배치할 수 있는 경우 보안 취약점이 발생할 수 있습니다.|
|[CA3075: DTD 처리가 안전하지 않습니다.](../code-quality/ca3075-insecure-dtd-processing.md)|안전하지 않은 DTDProcessing 인스턴스를 사용하거나 외부 엔터티 소스를 참조하면 파서는 신뢰할 수 없는 입력을 허용하고 공격자에게 중요 한 정보를 공개할 수 있습니다.|
|[CA3076: XSLT 스크립트 실행이 안전하지 않습니다.](../code-quality/ca3076-insecure-xslt-script-execution.md)|.NET 애플리케이션에서 비보안 방식으로 XSLT(Extensible Stylesheets Language Transformations)를 실행하는 경우 프로세서는 공격자에게 중요한 정보를 노출하여 서비스 거부 및 사이트 간 공격을 유발할 수 있는 신뢰할 수 없는 URI 참조를 확인할 수 있습니다.|
|[CA3077: API 디자인, XML 문서 및 XML 텍스트 판독기의 처리가 안전하지 않습니다.](../code-quality/ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader.md)|XMLDocument 및 XMLTextReader에서 파생된 API를 디자인할 경우 DtdProcessing에 주의해야 합니다.  외부 엔터티 소스를 참조하거나 확인할 때 안전하지 않은 DTDProcessing 인스턴스를 사용하거나 XML에서 안전하지 않은 값을 설정하면 정보가 공개될 수 있습니다.|
