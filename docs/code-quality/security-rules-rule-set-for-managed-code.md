---
title: 관리 코드에 대한 보안 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f3205bf3c81bbb9dac19c810e3a89a5fcd2227b
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658401"
---
# <a name="security-rules-rule-set-for-managed-code"></a>관리 코드에 대한 보안 규칙 규칙 집합

레거시 코드 분석에 대해 Microsoft 보안 규칙 규칙 집합을 사용 하 여 보고 되는 잠재적인 보안 문제 수를 최대화 합니다.

|규칙|설명|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.|
|[CA2102](../code-quality/ca2102.md)|일반 처리기에서 비 CLSCompliant 예외를 catch하세요.|
|[CA2103](../code-quality/ca2103.md)|명령적 보안을 검토하세요.|
|[CA2104](../code-quality/ca2104.md)|변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.|
|[CA2105](../code-quality/ca2105.md)|배열 필드는 읽기 전용이면 안 됩니다.|
|[CA2106](../code-quality/ca2106.md)|어설션을 안전하게 보호하세요.|
|[CA2107](../code-quality/ca2107.md)|deny 및 permit only 사용을 검토하세요.|
|[CA2108](../code-quality/ca2108.md)|값 형식에서 선언적 보안을 검토하십시오.|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|표시되는 이벤트 처리기를 검토하세요.|
|[CA2111](../code-quality/ca2111.md)|포인터는 노출되면 안 됩니다.|
|[CA2112](../code-quality/ca2112.md)|보안 형식은 필드를 노출하면 안 됩니다.|
|[CA2114](../code-quality/ca2114.md)|메서드 보안은 형식의 상위 집합이어야 합니다.|
|[CA2115](../code-quality/ca2115.md)|네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.|
|[CA2116](../code-quality/ca2116.md)|APTCA 메서드는 APTCA 메서드만 호출해야 합니다.|
|[CA2117](../code-quality/ca2117.md)|APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.|
|[CA2118](../code-quality/ca2118.md)|SuppressUnmanagedCodeSecurityAttribute 사용을 검토하세요.|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|private 인터페이스를 만족하는 메서드를 봉인하세요.|
|[CA2120](../code-quality/ca2120.md)|serialization 생성자를 안전하게 하세요.|
|[CA2121](../code-quality/ca2121.md)|정적 생성자는 private이어야 합니다.|
|[CA2122](../code-quality/ca2122.md)|링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.|
|[CA2123](../code-quality/ca2123.md)|재정의 링크 요청은 기본 링크 요청과 같아야 합니다.|
|[CA2124](../code-quality/ca2124.md)|취약한 finally 절을 외부 try에 래핑하십시오.|
|[CA2126](../code-quality/ca2126.md)|형식 링크 요청에는 상속 요청이 필요합니다.|
|[CA2130](../code-quality/ca2130.md)|보안에 중요한 상수는 투명해야 합니다.|
|[CA2131](../code-quality/ca2131.md)|보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.|
|[CA2132](../code-quality/ca2132.md)|기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.|
|[CA2133](../code-quality/ca2133.md)|대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.|
|[CA2134](../code-quality/ca2134.md)|메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.|
|[CA2135](../code-quality/ca2135.md)|수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.|
|[CA2136](../code-quality/ca2136.md)|멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.|
|[CA2137](../code-quality/ca2137.md)|투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.|
|[CA2138](../code-quality/ca2138.md)|투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.|
|[CA2139](../code-quality/ca2139.md)|투명 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다.|
|[CA2140](../code-quality/ca2140.md)|투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.|
|[CA2141](../code-quality/ca2141.md)|투명 메서드는 LinkDemands를 충족해서는 안 됩니다|
|[CA2142](../code-quality/ca2142.md)|투명 코드는 LinkDemands로 보호될 수 없습니다.|
|[CA2143](../code-quality/ca2143.md)|투명 메서드는 보안 요청을 사용할 수 없습니다.|
|[CA2144](../code-quality/ca2144.md)|투명 코드는 바이트 배열에서 어셈블리를 로드할 수 없습니다.|
|[CA2145](../code-quality/ca2145.md)|투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅할 수 없습니다.|
|[CA2146](../code-quality/ca2146.md)|형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.|
|[CA2147](../code-quality/ca2147.md)|투명 메서드는 보안 어설션을 사용할 수 없습니다.|
|[CA2149](../code-quality/ca2149.md)|투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.|
|[CA2210](../code-quality/ca2210.md)|어셈블리에는 올바른 강력한 이름을 사용해야 합니다.|
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|안전하지 않은 역직렬 변환기 BinaryFormatter를 사용하지 마세요.|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|먼저 BinaryFormatter.Binder를 설정하지 않고 BinaryFormatter.Deserialize를 호출하지 마세요.|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|BinaryFormatter.Deserialize를 호출하기 전에 BinaryFormatter.Binder가 설정되었는지 확인합니다.|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|안전하지 않은 역직렬 변환기 LosFormatter를 사용하지 마세요.|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|안전하지 않은 역직렬 변환기 NetDataContractSerializer를 사용하지 마세요.|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|먼저 NetDataContractSerializer.Binder를 설정하지 않고 역직렬화하지 마세요.|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|역직렬화하기 전에 NetDataContractSerializer.Binder를 설정해야 합니다.|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|안전하지 않은 역직렬 변환기 ObjectStateFormatter를 사용하지 마세요.|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|SimpleTypeResolver를 사용하여 JavaScriptSerializer를 통해 역직렬화하지 마세요.|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|JavaScriptSerializer가 역직렬화하기 전에 SimpleTypeResolver로 초기화되지 않는지 확인하세요.|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|코드에서 SQL 주입 취약점에 대해 검토합니다.|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|코드에서 XSS 취약점에 대해 검토합니다.|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|코드에서 파일 경로 삽입 취약성에 대해 검토합니다.|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|코드에서 정보 공개 취약성에 대해 검토합니다.|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|코드에서 LDAP 주입 취약점에 대해 검토합니다.|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|코드에서 프로세스 명령 주입 취약점에 대해 검토합니다.|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|코드에서 오픈 리디렉션 취약점에 대해 검토합니다.|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|코드에서 XPath 삽입 취약성에 대해 검토합니다.|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|코드에서 XML 삽입 취약성에 대해 검토합니다.|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|코드에서 XAML 삽입 취약성에 대해 검토합니다.|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|코드에서 DLL 삽입 취약성에 대해 검토합니다.|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|코드에서 regex 삽입 취약성에 대해 검토합니다.|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|안전하지 않은 암호화 모드를 사용하지 마세요.|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|인증서 하드 코딩 안 함|