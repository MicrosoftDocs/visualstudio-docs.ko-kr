---
title: 보안 경고
ms.date: 10/02/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.securityrules
helpviewer_keywords:
- security [Visual Studio ALM], Enterprise Templates
- security warnings
- managed code analysis warnings, security warnings
- warnings, security
ms.assetid: 60d4e8ea-230a-494f-aa6a-b91db77540e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 713787472ac9c9320bf94c430108aaf330908496
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184603"
---
# <a name="security-warnings"></a>보안 경고

보안 경고는 더 안전한 라이브러리 및 애플리케이션을 지원합니다. 이들 경고는 프로그램의 보안 결함을 방지하는 데 도움이 됩니다. 이들 경고를 비활성화하는 경우 코드에 그 이유를 명확하게 표시하고 개발 프로젝트의 지정된 보안 담당자에게 이 사실을 알려야 합니다.

## <a name="in-this-section"></a>단원 내용

|규칙|설명|
|----------|-----------------|
|[CA2100: 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.](../code-quality/ca2100.md)|메서드가 메서드에 대한 문자열 인수로부터 만들어진 문자열을 사용하여 System.Data.IDbCommand.CommandText 속성을 설정합니다. 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다.|
|[CA2102: 일반 처리기에서 비 CLSCompliant 예외를 catch하세요.](../code-quality/ca2102.md)|RuntimeCompatibilityAttribute로 표시되지 않거나 RuntimeCompatibility(WrapNonExceptionThrows = false)로 표시된 어셈블리의 멤버에는 System.Exception을 처리하는 catch 블록이 포함되며 바로 뒤의 일반 catch 블록은 포함되지 않습니다.|
|[CA2103: 명령적 보안을 검토하세요.](../code-quality/ca2103.md)|메서드가 명령적 보안을 사용하고, 요청이 활성 상태인 동안 변경될 수 있는 반환 값 또는 상태 정보를 사용하여 권한을 구성하고 있습니다. 가능하면 선언적 보안을 사용합니다.|
|[CA2104: 변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.](../code-quality/ca2104.md)|외부에서 볼 수 있는 형식에 변경 가능한 참조 형식인, 외부에서 볼 수 있는 읽기 전용 필드가 포함되었습니다. 변경 가능한 형식은 해당 인스턴스 데이터를 수정할 수 있는 형식을 말합니다.|
|[CA2105: 배열 필드는 읽기 전용이면 안 됩니다.](../code-quality/ca2105.md)|배열이 들어 있는 필드에 read-only(Visual Basic의 경우 ReadOnly) 한정자를 적용하면 필드를 변경하여 다른 배열을 참조할 수 없습니다. 그러나 읽기 전용 필드에 저장된 배열의 요소는 변경할 수 있습니다.|
|[CA2106: 어설션을 안전하게 보호하세요.](../code-quality/ca2106.md)|메서드에서 권한을 어설션하는데 호출자에 대해 보안 검사가 수행되지 않습니다. 보안 검사를 수행하지 않고 보안 권한을 어설션하면 코드에 보안상 취약한 부분이 남아 있을 수 있습니다.|
|[CA2107: deny 및 permit only 사용을 검토하세요.](../code-quality/ca2107.md)|PermitOnly 메서드 및 CodeAccessPermission 사용. 보안 거부 동작은 .NET 보안에 대 한 고급 지식이 있는 경우에만 사용 해야 합니다. 이러한 보안 동작을 사용하는 코드는 보안 검토를 거쳐야 합니다.|
|[CA2108: 값 형식에서 선언적 보안을 검토하십시오.](../code-quality/ca2108.md)|public 또는 protected 값 형식이 데이터 액세스 또는 링크 요청에 의해 보안됩니다.|
|[CA2109: 표시되는 이벤트 처리기를 검토하세요.](../code-quality/ca2109.md)|public 또는 protected 이벤트 처리 메서드를 발견했습니다. 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다.|
|[CA2111: 포인터는 노출되면 안 됩니다.](../code-quality/ca2111.md)|포인터가 전용, 내부 또는 읽기 전용이 아닙니다. 악의적인 코드에서는 해당 포인터 값을 변경하여 메모리 내 임의의 위치에 액세스할 수 있게 되거나 애플리케이션 또는 시스템 오류를 발생시킬 수 있습니다.|
|[CA2112: 보안 형식은 필드를 노출하면 안 됩니다.](../code-quality/ca2112.md)|public 또는 protected 형식이 public 필드를 포함하고 링크 요청에 의해 보안됩니다. 코드에 링크 요청으로 보안된 형식의 인스턴스에 대한 액세스 권한이 있으면 코드에서 링크 요청을 만족하지 않아도 해당 형식의 필드에 액세스할 수 있습니다.|
|[CA2114: 메서드 보안은 형식의 상위 집합이어야 합니다.](../code-quality/ca2114.md)|메서드에는 같은 동작에 대해 메서드 수준과 형식 수준의 선언적 보안이 모두 있으면 안 됩니다.|
|[CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.](../code-quality/ca2115.md)|이 규칙에서는 관리되지 않는 리소스가 비관리 코드에서 여전히 사용되고 있는데 종료되려고 할 경우 발생할 수 있는 오류를 감지합니다.|
|[CA2116: APTCA 메서드는 APTCA 메서드만 호출해야 합니다.](../code-quality/ca2116.md)|완전히 신뢰할 수 있는 어셈블리에 APTCA(AllowPartiallyTrustedCallers) 특성이 있고 이 어셈블리가 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 다른 어셈블리의 코드를 실행하면 보안상 위험할 수 있습니다.|
|[CA2117: APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.](../code-quality/ca2117.md)|완전히 신뢰할 수 있는 어셈블리에 APTCA(AllowPartiallyTrustedCallers) 특성이 있고 이 어셈블리의 형식이 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 형식에서 상속되면 보안상 위험할 수 있습니다.|
|[CA2118: SuppressUnmanagedCodeSecurityAttribute 사용을 검토하세요.](../code-quality/ca2118.md)|SuppressUnmanagedCodeSecurityAttribute는 COM interop 또는 플랫폼 호출을 사용하는 비관리 코드를 실행하는 멤버에 대해 기본 보안 시스템 동작을 변경합니다. 이 특성은 기본적으로 성능 향상을 위해 사용되지만 성능이 향상되는 대신 중대한 보안 위험이 발생합니다.|
|[CA2119: private 인터페이스를 만족하는 메서드를 봉인하세요.](../code-quality/ca2119.md)|상속할 수 있는 public 형식에서는 internal(Visual Basic의 경우 Friend) 인터페이스의 재정의 가능한 메서드 구현을 제공합니다. 이 규칙 위반 문제를 해결하려면 어셈블리 외부에서 메서드가 재정의되지 않도록 합니다.|
|[CA2120: serialization 생성자를 안전하게 하세요.](../code-quality/ca2120.md)|이 형식에는 System.Runtime.Serialization.SerializationInfo 개체와 System.Runtime.Serialization.StreamingContext 개체(serialization 생성자 서명)를 사용하는 생성자가 있습니다. 이 생성자는 보안 검사를 통해 보안되지 않지만 형식에 있는 하나 이상의 정규 생성자가 보안됩니다.|
|[CA2121: 정적 생성자는 private이어야 합니다.](../code-quality/ca2121.md)|시스템에서는 형식의 첫 번째 인스턴스가 만들어지거나 static 멤버가 참조되기 전에 static 생성자를 호출합니다. static 생성자가 private이 아니면 시스템 이외의 코드에서 이를 호출할 수 있습니다. 이렇게 되면 생성자에서 수행하는 작업에 따라 예기치 않은 동작이 발생할 수 있습니다.|
|[CA2122: 링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.](../code-quality/ca2122.md)|public 또는 protected 멤버에 링크 요청이 있으며 해당 멤버가 보안 검사를 수행하지 않는 멤버에 의해 호출됩니다. 링크 요청은 직접 실행 호출자의 권한만 검사합니다.|
|[CA2123: 재정의 링크 요청은 기본 링크 요청과 같아야 합니다.](../code-quality/ca2123.md)|이 규칙에서는 메서드를 다른 형식의 인터페이스이거나 가상 메서드인 기본 메서드에 일치시킨 다음 각각에 대해 링크 요청을 비교합니다. 이 규칙이 위반되면 악의적인 호출자가 보안되지 않은 메서드를 호출함으로써 링크 요청을 우회할 수 있습니다.|
|[CA2124: 취약한 finally 절을 외부 try에 래핑하십시오.](../code-quality/ca2124.md)|public 또는 protected 메서드에 try/finally 블록이 들어 있습니다. finally 블록이 보안 상태를 다시 설정하는 것으로 나타나며 finally 블록에 포함되어 있지 않습니다.|
|[CA2126: 형식 링크 요청에는 상속 요청이 필요합니다.](../code-quality/ca2126.md)|public unsealed 형식이 링크 요청으로 보호되며 재정의 가능한 메서드를 포함합니다. 형식이나 메서드는 모두 상속 요청으로 보호됩니다.|
|[CA2130: 보안에 중요한 상수는 투명해야 합니다.](../code-quality/ca2130.md)|런타임에 조회가 필요하지 않도록 컴파일러에서 상수 값을 인라인하기 때문에 상수 값에 투명성이 적용되지 않습니다. 상수 필드는 보안 투명해야 하므로 코드 검토자는 투명 코드가 상수에 액세스할 수 없다고 가정하지 않습니다.|
|[CA2131: 보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.](../code-quality/ca2131.md)|형식이 동등성에 참여 하 고 형식 자체 또는 형식의 멤버 또는 필드 중 하나가 SecurityCriticalAttribute 특성으로 표시 됩니다. 이 규칙은 중요한 형식 또는 중요한 메서드나 필드를 포함하는 형식이 형식 동등에 참여하는 경우에 적용됩니다. CLR에서 이러한 형식이 검색되면 런타임에 해당 형식이 로드되지 않고 TypeLoadException이 throw됩니다. 일반적으로 이 규칙은 사용자가 tlbimp와 컴파일러를 이용하여 형식 동등을 수행하지 않고 수동으로 형식 동등을 구현하는 경우에만 적용됩니다.|
|[CA2132: 기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.](../code-quality/ca2132.md)|SecurityCriticalAttribute가 있는 형식 및 멤버는 Silverlight 애플리케이션 코드에서 사용할 수 없습니다. 보안에 중요한 형식 및 멤버는 .NET Framework for Silverlight 클래스 라이브러리의 신뢰할 수 있는 코드에서만 사용할 수 있습니다. 파생 클래스의 public 또는 protected 구성 요소는 투명성이 기본 클래스보다 높거나 같아야 하기 때문에 애플리케이션의 클래스는 SecurityCritical로 표시된 클래스에서 파생될 수 없습니다.|
|[CA2133: 대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.](../code-quality/ca2133.md)|이 경고는 SecurityCriticalAttribute를 사용하여 표시된 대리자를 SecuritySafeCriticalAttribute를 사용하여 표시되거나 투명한 메서드에 바인딩하는 메서드에서 발생합니다. 또한 투명하거나 안전에 중요한 대리자를 중요한 메서드에 바인딩하는 메서드에서도 이 경고가 발생합니다.|
|[CA2134: 메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.](../code-quality/ca2134.md)|이 규칙은 SecurityCriticalAttribute로 표시된 메서드가 SecuritySafeCriticalAttribute로 표시되거나 투명한 메서드를 재정의할 때 적용됩니다. 또한 SecuritySafeCriticalAttribute로 표시되거나 투명한 메서드가 SecurityCriticalAttribute로 표시된 메서드를 재정의할 때도 이 규칙이 적용됩니다. 이 규칙은 가상 메서드를 재정의하거나 인터페이스를 구현할 때 적용됩니다.|
|[CA2135: 수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.](../code-quality/ca2135.md)|LinkDemands는 수준 2 보안 규칙 집합에서 사용되지 않습니다. JIT(Just-in-Time) 컴파일 시 보안을 적용하는 데 LinkDemands를 사용하는 대신, 해당 메서드, 형식 및 필드를 SecurityCriticalAttribute 특성으로 표시하세요.|
|[CA2136: 멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.](../code-quality/ca2136.md)|투명성 특성은 큰 범위의 코드 요소에서 작은 범위의 요소에 적용됩니다. 범위가 큰 코드 요소의 투명성 특성은 첫 번째 요소에 포함된 코드 요소의 투명성 특성보다 우선합니다. 예를 들어 SecurityCriticalAttribute 특성으로 표시된 클래스에는 SecuritySafeCriticalAttribute 특성으로 표시된 메서드가 포함될 수 없습니다.|
|[CA2137: 투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.](../code-quality/ca2137.md)|메서드가 확인할 수 없는 코드를 포함하거나 형식을 참조로 반환합니다. 이 규칙은 보안 투명 코드에서 확인할 수 없는 MSIL(Microsoft Intermediate Language)을 실행하려고 할 때 적용됩니다. 그러나 이 규칙은 완전한 IL 검증 도구를 포함하지 않으며 대신 추론을 사용하여 MSIL 확인 시 대부분의 위반을 catch합니다.|
|[CA2138: 투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.](../code-quality/ca2138.md)|보안 투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 표시된 메서드를 호출합니다.|
|[CA2139: 투명 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다.](../code-quality/ca2139.md)|이 규칙은 투명 하 고 HandleProcessCorruptedStateExceptionsAttribute 특성을 사용 하 여 프로세스 손상 예외를 처리 하려고 시도 하는 모든 메서드에서 발생 합니다. 프로세스 손상 예외는와 같은 예외의 CLR 버전 4.0 예외 분류입니다 <xref:System.AccessViolationException> . HandleProcessCorruptedStateExceptionsAttribute 특성은 보안에 중요한 메서드에서만 사용할 수 있으며 투명 메서드에 적용되는 경우 무시됩니다.|
|[CA2140: 투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.](../code-quality/ca2140.md)|SecurityTransparentAttribute로 표시된 메서드가 SecurityCritical로 표시된 public이 아닌 멤버를 호출합니다. 이 규칙은 투명 하 고 중요 한 어셈블리의 모든 메서드와 형식을 분석 하 고 투명 코드의 모든 호출을 Securitytreatassafe로로 표시 되지 않은 public이 아닌 중요 코드로 플래그를 표시 합니다.|
|[CA2141: 투명한 메서드는 LinkDemands를 충족해서는 안 됩니다](../code-quality/ca2141.md)|보안 투명 메서드가 APTCA(AllowPartiallyTrustedCallersAttribute) 특성으로 표시되지 않은 어셈블리의 메서드를 호출하거나, 보안 투명 메서드가 형식 또는 메서드에 대한 LinkDemand를 충족합니다.|
|[CA2142: 투명 코드는 LinkDemands로 보호될 수 없습니다.](../code-quality/ca2142.md)|이 규칙은 액세스하는 데 LinkDemands가 필요한 투명한 메서드에 적용됩니다. 보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다.|
|[CA2143: 투명 메서드는 보안 요청을 사용할 수 없습니다.](../code-quality/ca2143.md)|보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다. 보안 투명 코드는 보안에 중요한 결정을 내리는 데 전체 요청을 사용해야 하며 안전에 중요한 코드는 전체 요청을 위해 투명 코드를 사용해서는 안 됩니다.|
|[CA2144: 투명 코드는 바이트 배열에서 어셈블리를 로드할 수 없습니다.](../code-quality/ca2144.md)|투명 코드는 보안에 중요한 동작을 수행할 수 없기 때문에 투명 코드의 보안 검토는 중요 코드에 대한 보안 검토만큼 완벽하지 않습니다. 바이트 배열에서 로드된 어셈블리는 투명 코드에서 발견되지 않을 수 있으며 해당 바이트 배열은 감사할 필요가 없는 중요하거나 특히 안전에 중요한 코드를 포함할 수 있습니다.|
|[CA2145: 투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅할 수 없습니다.](../code-quality/ca2145.md)|SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅된 메서드에 이를 호출하는 메서드에 대한 암시적 LinkDemand가 배치되어 있습니다. 이 LinkDemand는 호출 코드가 보안을 중요시 하도록 요구합니다. SuppressUnmanagedCodeSecurity를 사용하는 메서드를 SecurityCriticalAttribute 특성으로 표시하면 이 요구 사항이 메서드 호출자에 더욱 명확하게 전달됩니다.|
|[CA2146: 형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.](../code-quality/ca2146.md)|이 규칙은 파생 형식에 기본 형식 또는 구현된 인터페이스만큼 중요하지 않은 보안 투명성 특성이 있을 때 적용됩니다. 중요한 기본 형식에서 파생되거나 중요한 인터페이스를 구현할 수 있는 것은 중요한 형식뿐이고, 안전에 중요한 기본 형식에서 파생되거나 안전에 중요한 인터페이스를 구현할 수 있는 것은 중요하거나 안전에 중요한 형식뿐입니다.|
|[CA2147: 투명 메서드는 보안 어설션을 사용할 수 없습니다.](../code-quality/ca2147.md)|이 규칙은 100% 투명 어셈블리나 투명/중요 혼합 어셈블리의 모든 메서드와 형식을 분석하고 선언적이거나 명령적인 어설션 사용에 플래그를 지정합니다.|
|[CA2149: 투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.](../code-quality/ca2149.md)|이 규칙은 P/Invoke를 통해 네이티브 코드를 직접 호출 하는 모든 투명 메서드에 대해 발생 합니다. 이 규칙이 위반되면 수준 2 투명성 모델에서 MethodAccessException이 발생하고 수준 1 투명성 모델에서 UnmanagedCode에 대한 완전 요청이 발생합니다.|
|[CA2151: 중요한 형식이 포함된 필드는 보안에 중요한 필드여야 합니다.](../code-quality/ca2151.md)|보안 중요 형식을 사용하려면 이 형식을 참조하는 코드가 보안 중요 또는 보안 안전 중요여야 합니다. 참조가 간접적인 경우에도 마찬가지입니다. 따라서 투명 코드는 필드에 액세스할 수 없으므로 보안 투명 또는 보안 안전 중요 필드가 있을 경우 잘못 해석됩니다.|
|[CA2153: 손상된 상태 예외를 처리하지 마세요.](../code-quality/ca2153.md)|[CSE(손상된 상태 예외)](https://msdn.microsoft.com/magazine/dd419661.aspx) 는 프로세스에 메모리 손상이 있음을 나타냅니다. 프로세스 충돌을 허용하는 대신 catch하면 공격자가 손상된 메모리 영역에 익스플로잇을 배치할 수 있는 경우 보안 취약점이 발생할 수 있습니다.|
|[CA2300: 안전하지 않은 역직렬 변환기 BinaryFormatter를 사용하지 마세요.](../code-quality/ca2300.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2301: 먼저 BinaryFormatter.Binder를 설정하지 않고 BinaryFormatter.Deserialize를 호출하지 마세요.](../code-quality/ca2301.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2302: BinaryFormatter.Deserialize를 호출하기 전에 BinaryFormatter.Binder가 설정되었는지 확인합니다.](../code-quality/ca2302.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2305: 안전하지 않은 역직렬 변환기 LosFormatter를 사용하지 마세요.](../code-quality/ca2305.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2310: 안전하지 않은 역직렬 변환기 NetDataContractSerializer를 사용하지 마세요.](../code-quality/ca2310.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2311: 먼저 NetDataContractSerializer.Binder를 설정하지 않고 역직렬화하지 마세요.](../code-quality/ca2311.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2312: 역직렬화하기 전에 NetDataContractSerializer.Binder를 설정해야 합니다.](../code-quality/ca2312.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2315: 안전하지 않은 역직렬 변환기 ObjectStateFormatter를 사용하지 마세요.](../code-quality/ca2315.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2321: SimpleTypeResolver를 사용하여 JavaScriptSerializer를 통해 역직렬화하지 마세요.](../code-quality/ca2321.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2322: JavaScriptSerializer가 역직렬화하기 전에 SimpleTypeResolver로 초기화되지 않는지 확인하세요.](../code-quality/ca2322.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2326: None 이외의 TypeNameHandling 값을 사용하지 마세요.](../code-quality/ca2326.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2327: 안전하지 않은 JsonSerializerSettings를 사용하지 마세요.](../code-quality/ca2327.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2328: JsonSerializerSettings가 안전한지 확인하세요.](../code-quality/ca2328.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2329: 안전하지 않은 구성을 사용하여 JsonSerializer로 역직렬화하지 마세요.](../code-quality/ca2329.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2330: 역직렬화할 때 JsonSerializer에 보안 구성이 있는지 확인하세요.](../code-quality/ca2330.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA3001: 코드에서 SQL 주입 취약점에 대해 검토합니다.](../code-quality/ca3001.md)|신뢰할 수 없는 입력 및 SQL 명령으로 작업 하는 경우 SQL 삽입 공격에 유의 해야 합니다. SQL 삽입 공격은 악의적인 SQL 명령을 실행 하 여 응용 프로그램의 보안 및 무결성을 손상 시킬 수 있습니다.|
|[CA3002: 코드에서 XSS 취약점에 대해 검토합니다.](../code-quality/ca3002.md)|웹 요청에서 신뢰할 수 없는 입력으로 작업할 때는 XSS (사이트 간 스크립팅) 공격에 주의 해야 합니다. XSS 공격은 신뢰할 수 없는 입력을 원시 HTML 출력에 삽입 하 여 공격자가 악의적인 스크립트를 실행 하거나 웹 페이지의 콘텐츠를 악의적으로 수정할 수 있도록 합니다.|
|[CA3003: 코드에서 파일 경로 삽입 취약성에 대해 검토합니다.](../code-quality/ca3003.md)|웹 요청에서 신뢰할 수 없는 입력으로 작업 하는 경우 파일에 대 한 경로를 지정 하는 경우 사용자가 제어 하는 입력을 사용할 수 있습니다.|
|[CA3004: 코드에서 정보 공개 취약성에 대해 검토합니다.](../code-quality/ca3004.md)|예외 정보를 공개 하면 공격자가 응용 프로그램의 내부 정보를 파악할 수 있으므로 공격자가 다른 취약점을 악용할 수 있습니다.|
|[CA3006: 코드에서 프로세스 명령 주입 취약점에 대해 검토합니다.](../code-quality/ca3006.md)|신뢰할 수 없는 입력으로 작업 하는 경우 명령 삽입 공격에 유의 해야 합니다. 명령 삽입 공격은 서버와의 보안 및 무결성을 손상 시키는 기본 운영 체제에서 악성 명령을 실행할 수 있습니다.|
|[CA3007: 코드에서 오픈 리디렉션 취약점에 대해 검토합니다.](../code-quality/ca3007.md)|신뢰할 수 없는 입력으로 작업 하는 경우 개방형 리디렉션 취약성에 유의 해야 합니다. 공격자는 오픈 리디렉션 취약성을 악용 하 여 합법적인 URL의 모양을 제공 하는 데 웹 사이트를 사용할 수 있지만, 의심 되는 방문자를 피싱 또는 기타 악성 웹 페이지로 리디렉션할 수 있습니다.|
|[CA3008: 코드에서 XPath 삽입 취약성에 대해 검토합니다.](../code-quality/ca3008.md)|신뢰할 수 없는 입력으로 작업할 때는 XPath 삽입 공격에 유의 해야 합니다. 신뢰할 수 없는 입력을 사용 하 여 XPath 쿼리를 생성 하면 공격자가 쿼리를 악의적으로 조작 하 여 의도 하지 않은 결과를 반환 하 고 쿼리 된 XML의 콘텐츠를 공개할 수 있습니다.|
|[CA3009: 코드에서 XML 삽입 취약성에 대해 검토합니다.](../code-quality/ca3009.md)|신뢰할 수 없는 입력으로 작업 하는 경우 XML 삽입 공격에 유의 해야 합니다.|
|[CA3010: 코드에서 XAML 삽입 취약성에 대해 검토합니다.](../code-quality/ca3010.md)|신뢰할 수 없는 입력으로 작업 하는 경우 XAML 삽입 공격에 유의 해야 합니다. XAML은 개체 인스턴스화 및 실행을 직접적으로 나타내는 태그 언어입니다. 즉, XAML로 생성 된 요소는 시스템 리소스 (예: 네트워크 액세스 및 파일 시스템 IO)와 상호 작용할 수 있습니다.|
|[CA3011: 코드에서 DLL 삽입 취약성에 대해 검토합니다.](../code-quality/ca3011.md)|신뢰할 수 없는 입력으로 작업할 때는 신뢰할 수 없는 코드를 로드 하는 것에 유의 해야 합니다. 웹 응용 프로그램이 신뢰할 수 없는 코드를 로드 하는 경우 공격자가 프로세스에 악성 Dll을 삽입 하 고 악성 코드를 실행할 수 있습니다.|
|[CA3012: 코드에서 regex 삽입 취약성에 대해 검토합니다.](../code-quality/ca3012.md)|신뢰할 수 없는 입력으로 작업할 때는 regex 삽입 공격에 유의 해야 합니다. 공격자는 regex 주입을 사용 하 여 정규식을 악의적으로 수정 하거나 regex가 의도 하지 않은 결과와 일치 하도록 하거나 regex가 과도 한 CPU를 사용 하 여 서비스 거부 공격을 내릴 수 있습니다.|
|[CA3061: URL로 스키마를 추가하지 마세요.](../code-quality/ca3061.md)|위험한 외부 참조를 유발할 수 있으므로 Add 메서드의 unsafe 오버 로드를 사용 하지 마세요.|
|[CA3075: DTD 처리가 안전하지 않습니다.](../code-quality/ca3075.md)|안전하지 않은 DTDProcessing 인스턴스를 사용하거나 외부 엔터티 소스를 참조하면 파서는 신뢰할 수 없는 입력을 허용하고 공격자에게 중요 한 정보를 공개할 수 있습니다.|
|[CA3076: XSLT 스크립트 실행이 안전하지 않습니다.](../code-quality/ca3076.md)|.NET 응용 프로그램에서 비보안 방식에서 XSLT (Extensible Stylesheet Language) 변환 (XSLT)을 실행 하는 경우 프로세서는 공격자에 게 중요 한 정보를 노출 하 여 서비스 거부 및 사이트 간 공격을 유발할 수 있는 신뢰할 수 없는 URI 참조를 해결할 수 있습니다.|
|[CA3077: API 디자인, XML 문서 및 XML 텍스트 판독기의 처리가 안전하지 않습니다.](../code-quality/ca3077.md)|XMLDocument 및 XMLTextReader에서 파생된 API를 디자인할 경우 DtdProcessing에 주의해야 합니다. 외부 엔터티 소스를 참조하거나 확인할 때 안전하지 않은 DTDProcessing 인스턴스를 사용하거나 XML에서 안전하지 않은 값을 설정하면 정보가 공개될 수 있습니다.|
|[CA3147: ValidateAntiForgeryToken을 사용하여 동사 처리기를 표시하세요.](../code-quality/ca3147.md)|ASP.NET MVC 컨트롤러를 설계할 때 사이트 간 요청 위조 공격을 염두에 둘 수 있습니다. 교차 사이트 요청 위조 공격은 인증 된 사용자의 악성 요청을 ASP.NET MVC 컨트롤러로 보낼 수 있습니다.|
|[CA5122 P/Invoke 선언이 안전 하 게 중요 한 것은 아닙니다.](../code-quality/ca5122.md)|메서드는 보안에 중요한 작업을 수행할 때 SecuritySafeCritical로 표시되지만, 투명 코드에서도 안전하게 사용할 수 있습니다. 투명 코드는 P/Invoke를 통해 절대 네이티브 코드를 직접 호출할 수 없습니다. 따라서 P/Invoke를 SecuritySafeCritical로 표시할 경우 투명 코드가 P/Invoke를 호출할 수 없으며, 보안 분석에서 잘못 해석하는 원인이 됩니다.|
|[CA5359: 인증서 유효성 검사를 사용 하지 않도록 설정 하지 마십시오.](../code-quality/ca5359.md)|인증서는 서버의 id를 인증 하는 데 도움이 될 수 있습니다. 클라이언트는 서버 인증서의 유효성을 검사 하 여 요청이 원하는 서버로 전송 되도록 해야 합니다. ServerCertificateValidationCallback에서 항상를 반환 `true` 하는 경우 모든 인증서가 유효성 검사를 통과 합니다.|
|[CA5361: 강력한 암호의 SChannel 사용을 비활성화하지 마세요.](../code-quality/ca5361.md)|`Switch.System.Net.DontEnableSchUseStrongCrypto`를로 설정 `true` 하면 weakens TLS (전송 계층 보안) 연결에 사용 되는 암호화가 사용 됩니다. 약한 암호화는 응용 프로그램과 서버 간 통신의 기밀성을 손상 시켜 공격자가 중요 한 데이터를 보다 쉽게 도청 수 있도록 합니다.|
|[CA5362: deserialize 된 개체 그래프의 잠재적 참조 주기](../code-quality/ca5362.md)|신뢰할 수 없는 데이터를 deserialize 하는 경우 deserialize 된 개체 그래프를 처리 하는 모든 코드는 무한 루프로 이동 하지 않고 참조 주기를 처리 해야 합니다. 여기에는 deserialization 콜백의 일부인 코드와 deserialization 완료 후 개체 그래프를 처리 하는 코드가 모두 포함 됩니다. 그렇지 않으면 공격자가 참조 주기를 포함 하는 악성 데이터를 사용 하 여 서비스 거부 공격을 수행할 수 있습니다.|
|[CA5363: 요청 유효성 검사를 사용하지 않도록 설정하지 마세요.](../code-quality/ca5363.md)|요청 유효성 검사는 HTTP 요청을 검사 하 고 사이트 간 스크립팅을 포함 하 여 삽입 공격으로 이어질 수 있는 잠재적으로 위험한 콘텐츠가 포함 되어 있는지 여부를 확인 하는 ASP.NET의 기능입니다.|
|[CA5364: 사용되지 않는 보안 프로토콜을 사용하지 마세요.](../code-quality/ca5364.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다.|
|[CA5365: HTTP 헤더 검사를 사용 하지 않도록 설정 하지 마십시오.](../code-quality/ca5365.md)|HTTP 헤더 검사는 응답 헤더에 있는 캐리지 리턴 및 줄 바꿈 문자 (\r 및 \n)의 인코딩을 사용할 수 있도록 합니다. 이 인코딩 헤더에 포함 된 신뢰할 수 없는 데이터를 표시 하는 애플리케이션을 악용 하는 삽입 공격을 방지 하는 데 도움이 됩니다.|
|[CA5366: DataSet에 XmlReader를 사용 하 여 XML 읽기](../code-quality/ca5366.md)|를 사용 하 여 <xref:System.Data.DataSet> 신뢰할 수 없는 데이터가 있는 XML을 읽으면 <xref:System.Xml.XmlReader> 보안 해결 프로그램을 사용 하거나 DTD 처리를 사용할 수 없는를 사용 하 여 제한 해야 하는 위험한 외부 참조가 로드 될 수 있습니다.|
|[CA5367: 포인터 필드를 사용 하 여 형식을 직렬화 하지 마십시오.](../code-quality/ca5367.md)|이 규칙은 포인터 필드 또는 속성이 있는 serializable 클래스가 있는지 여부를 확인 합니다. Serialize 할 수 없는 멤버는 정적 멤버 또는로 표시 된 필드와 같은 포인터 일 수 있습니다 <xref:System.NonSerializedAttribute> .|
|[CA5368: 페이지에서 파생 된 클래스에 대 한 ViewStateUserKey 설정](../code-quality/ca5368.md)|속성을 설정 하면 공격자가 변수를 사용 하 여 <xref:System.Web.UI.Page.ViewStateUserKey> 공격을 생성할 수 없도록 개별 사용자의 뷰 상태 변수에 식별자를 할당할 수 있으므로 응용 프로그램에 대 한 공격을 방지할 수 있습니다. 그렇지 않으면 교차 사이트 요청 위조에 대 한 취약성이 있습니다.|
|[CA5369: 역직렬화에 XmlReader를 사용하세요.](../code-quality/ca5369.md)|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 해야 하는 위험한 외부 참조를 로드할 수 있습니다.|
|[CA5370: 판독기 유효성 검사에 XmlReader를 사용하세요.](../code-quality/ca5370.md)|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 이 위험한 로드는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 하 여 제한할 수 있습니다.|
|[CA5371: 스키마 읽기에 XmlReader를 사용하세요.](../code-quality/ca5371.md)|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 보안 해결 프로그램을 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않는 XmlReader를 사용 하면이이 제한 됩니다.|
|[CA5372: XPathDocument에 XmlReader를 사용하세요.](../code-quality/ca5372.md)|신뢰할 수 없는 데이터에서 XML을 처리 하면 위험한 외부 참조가 로드 될 수 있으며,이는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 처리를 사용 하지 않도록 설정할 수 있습니다.|
|[CA5373: 사용되지 않는 키 파생 함수를 사용하지 마세요.](../code-quality/ca5373.md)|이 규칙은 약한 키 파생 메서드 및의 호출을 검색 합니다 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName>약한 알고리즘 PBKDF1을 사용 했습니다.|
|[CA5374: XslTransform를 사용 하지 마십시오.](../code-quality/ca5374.md)|이 규칙 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 은가 코드에서 인스턴스화되어 있는지 확인 합니다. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>는 이제 사용 되지 않으며 사용할 수 없습니다.|
|[CA5378: ServicePointManagerSecurityProtocols를 비활성화하지 마세요.](../code-quality/ca5378.md)|`Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`로 설정 `true` 하면 Windows Communication FRAMEWORK의 Tls (전송 계층 보안) 연결을 tls 1.0을 사용 하도록 제한 합니다. 해당 버전의 TLS는 더 이상 사용 되지 않습니다.|
|[CA5379: weak 키 파생 함수 알고리즘을 사용 하지 마십시오.](../code-quality/ca5379.md)|<xref:System.Security.Cryptography.Rfc2898DeriveBytes>클래스는 기본적으로 알고리즘을 사용 <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> 합니다. 이상에서 생성자의 일부 오버 로드에 사용할 해시 알고리즘을 지정 해야 합니다 <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> . 속성에는 <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> 접근자만 있으며 `get` 한정자가 없습니다 `overriden` .|
|[CA5380: 루트 저장소에 인증서를 추가하지 마세요.](../code-quality/ca5380.md)|이 규칙은 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca 집합을 사용 하 여 구성 됩니다.|
|[CA5381: 인증서가 루트 저장소에 추가되지 않았는지 확인하세요.](../code-quality/ca5381.md)|이 규칙은 잠재적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca (인증 기관) 집합으로 구성 됩니다.|
|[CA5382: ASP.NET Core에서 보안 쿠키를 사용 합니다.](../code-quality/ca5382.md)|HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 TLS (전송 계층 보안)를 사용 하 여 쿠키를 전송 해야 함을 브라우저에 표시 합니다.|
|[CA5383: ASP.NET Core에서 보안 쿠키 사용 확인](../code-quality/ca5383.md)|HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 TLS (전송 계층 보안)를 사용 하 여 쿠키를 전송 해야 함을 브라우저에 표시 합니다.|
|[CA5384: DSA (디지털 서명 알고리즘)를 사용 하지 마십시오.](../code-quality/ca5384.md)|DSA는 약한 비대칭 암호화 알고리즘입니다.|
|[CA5385: 키 크기가 충분 한 Rivest – Rivest-shamir-adleman – Rivest-shamir-adleman (RSA) 알고리즘을 사용 합니다.](../code-quality/ca5385.md)|2048 비트 보다 작은 RSA 키는 무차별 암호 대입 공격에 보다 취약 합니다.|
|[CA5386: SecurityProtocolType 값을 하드 코딩하지 마세요.](../code-quality/ca5386.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램의 보안을 유지 하려면 프로토콜 버전을 하드 코딩 하지 않고 .NET Framework v 4.7.1 이상을 대상으로 해야 합니다.|
|[CA5387: 충분 한 반복 횟수로 약한 키 파생 함수를 사용 하지 마십시오.](../code-quality/ca5387.md)|이 규칙은 암호화 키가 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다.|
|[CA5388: 약한 키 파생 함수를 사용 하는 경우 충분 한 반복 횟수를 확인 합니다.](../code-quality/ca5388.md)|이 규칙은 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 암호화 키가 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다.|
|[CA5389: 대상 파일 시스템 경로에 보관 항목의 경로를 추가하지 마세요.](../code-quality/ca5389.md)|파일 경로는 상대적일 수 있으며, 예상 된 파일 시스템 대상 경로 외부에서 파일 시스템에 액세스할 수 있으며,이로 인해 악의적인 구성 변경 내용 및 대기 방식 기술을 통해 원격 코드를 실행할 수 있습니다.|
|[CA5390: 암호화 키를 하드 코딩 하지 마십시오.](../code-quality/ca5390.md)|대칭 알고리즘을 성공적으로 수행 하려면 비밀 키를 발신자와 수신자 에게만 인식 해야 합니다. 키가 하드 코드 되 면 쉽게 검색 됩니다. 컴파일된 이진 파일의 경우에도 악의적인 사용자가 쉽게 추출할 수 있습니다. 개인 키가 손상 되 면 암호화 텍스트를 직접 해독 하 여 더 이상 보호할 수 없습니다.|
|[CA5394: 보안 되지 않은 임의성을 사용 하지 마십시오.](../code-quality/ca5394.md)|공격자는 암호화 된 약한 의사 난수 생성기를 사용 하 여 보안에 중요 한 값이 생성 되는 것을 예측할 수 있습니다.|
|[CA5396: 되어에 대해 HttpOnly를 true로 설정 합니다.](../code-quality/ca5396.md)|심층 방어 수단으로 보안에 민감한 HTTP 쿠키가 HttpOnly로 표시 되어 있는지 확인 합니다. 이는 웹 브라우저에서 스크립트가 쿠키에 액세스 하지 못하도록 하는 것을 의미 합니다. 삽입 된 악성 스크립트는 쿠키를 도용 하는 일반적인 방법입니다.|
|[CA5397: 사용되지 않는 SslProtocols 값을 사용하지 마세요.](../code-quality/ca5397.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다.|
|[CA5398: SslProtocols 값을 하드 코딩하지 마세요.](../code-quality/ca5398.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램이 안전 하 게 유지 되도록 하려면 프로토콜 버전을 하드 코딩 하지 마십시오.|
|[CA5399: 확실히 HttpClient 인증서 해지 목록 확인을 사용 하지 않도록 설정](../code-quality/ca5399.md)|해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다.|
|[CA5400: HttpClient 인증서 해지 목록 확인이 사용 하도록 설정 되어 있지 않은지 확인 합니다.](../code-quality/ca5400.md)|해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다.|
|[CA5401: 기본값이 아닌 IV와 함께 CreateEncryptor를 사용 하지 마십시오.](../code-quality/ca5401.md)|대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다.|
|[CA5402: 기본 IV와 함께 CreateEncryptor를 사용 합니다.](../code-quality/ca5402.md)|대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다.|
