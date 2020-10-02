---
title: 관리 코드에 대한 확장 수정 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 00295a8485fa80d2aa6cf1977e014b191b28ba7e
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658609"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>관리 코드에 대한 확장 수정 규칙 규칙 집합

Microsoft 확장 수정 규칙 규칙 집합은 코드 분석을 통해 보고 되는 논리 및 프레임 워크 사용 오류를 최대화 합니다. COM 상호 운용성 및 모바일 응용 프로그램과 같은 특정 시나리오에 대 한 추가 강조가 있습니다. 이러한 시나리오 중 하나가 프로젝트에 적용 되거나 프로젝트에서 추가 문제를 발견 하는 경우이 규칙 집합을 포함 하는 것을 고려해 야 합니다.

Microsoft 확장 수정 규칙 규칙 집합에는 [관리 권장 규칙](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) 규칙 집합에 있는 규칙을 포함 하는 [기본 수정 규칙](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) 규칙 집합에 있는 규칙이 포함 됩니다.

다음 표에서는 Microsoft 확장 수정 규칙 규칙 집합의 모든 규칙에 대해 설명 합니다.

|규칙|설명|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.|
|[CA1009](../code-quality/ca1009.md)|이벤트 처리기를 제대로 선언하십시오.|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|AssemblyVersionAttribute로 어셈블리 표시|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.|
|[CA1049](../code-quality/ca1049.md)|네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|P/Invoke를 NativeMethods 클래스로 이동|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|기본 클래스 메서드를 숨기지 마십시오.|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|IDisposable을 올바르게 구현하십시오.|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|예기치 않은 위치에서 예외를 발생시키지 마십시오.|
|[CA1301](../code-quality/ca1301.md)|중복 액셀러레이터 키를 사용하지 마십시오.|
|[CA1400](../code-quality/ca1400.md)|P/Invoke 진입점이 있어야 합니다.|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|P/Invoke는 노출되지 않아야 합니다.|
|[CA1403](../code-quality/ca1403.md)|자동 레이아웃 형식은 COM 노출이면 안 됩니다.|
|[CA1404](../code-quality/ca1404.md)|P/Invoke 다음에 바로 GetLastError를 호출하십시오.|
|[CA1405](../code-quality/ca1405.md)|COM 노출 형식의 기본 형식은 COM 노출이어야 합니다.|
|[CA1410](../code-quality/ca1410.md)|COM 등록 메서드는 일치해야 합니다.|
|[CA1415](../code-quality/ca1415.md)|P/Invoke를 올바르게 선언하십시오.|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|빈 종료자를 제거하십시오.|
|[CA1900](../code-quality/ca1900.md)|값 형식 필드는 이식 가능해야 합니다.|
|[CA1901](../code-quality/ca1901.md)|P/Invoke 선언은 이식 가능해야 합니다.|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|약한 ID를 가진 개체를 잠그지 마십시오.|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|P/Invoke 문자열 인수에 대해 마샬링을 지정하십시오.|
|[CA2108](../code-quality/ca2108.md)|값 형식에서 선언적 보안을 검토하십시오.|
|[CA2111](../code-quality/ca2111.md)|포인터는 노출되면 안 됩니다.|
|[CA2112](../code-quality/ca2112.md)|보안 형식은 필드를 노출하면 안 됩니다.|
|[CA2114](../code-quality/ca2114.md)|메서드 보안은 형식의 상위 집합이어야 합니다.|
|[CA2116](../code-quality/ca2116.md)|APTCA 메서드는 APTCA 메서드만 호출해야 합니다.|
|[CA2117](../code-quality/ca2117.md)|APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.|
|[CA2122](../code-quality/ca2122.md)|링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.|
|[CA2123](../code-quality/ca2123.md)|재정의 링크 요청은 기본 링크 요청과 같아야 합니다.|
|[CA2124](../code-quality/ca2124.md)|취약한 finally 절을 외부 try에 래핑하십시오.|
|[CA2126](../code-quality/ca2126.md)|형식 링크 요청에는 상속 요청이 필요합니다.|
|[CA2131](../code-quality/ca2131.md)|보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.|
|[CA2132](../code-quality/ca2132.md)|기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.|
|[CA2133](../code-quality/ca2133.md)|대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.|
|[CA2134](../code-quality/ca2134.md)|메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.|
|[CA2137](../code-quality/ca2137.md)|투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.|
|[CA2138](../code-quality/ca2138.md)|투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.|
|[CA2140](../code-quality/ca2140.md)|투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.|
|[CA2141](../code-quality/ca2141.md)|투명 메서드는 LinkDemands를 충족해서는 안 됩니다|
|[CA2146](../code-quality/ca2146.md)|형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.|
|[CA2147](../code-quality/ca2147.md)|투명 메서드는 보안 어설션을 사용할 수 없습니다.|
|[CA2149](../code-quality/ca2149.md)|투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|스택 정보를 유지하도록 다시 throw하십시오.|
|[CA2202](../code-quality/ca2202.md)|개체를 여러 번 삭제하지 마십시오.|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|값 형식 정적 필드 인라인을 초기화하십시오.|
|[CA2212](../code-quality/ca2212.md)|서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|삭제 가능한 필드는 삭제해야 합니다.|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|재정의 가능한 메서드를 생성자에서 호출하지 마십시오.|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|삭제 가능한 형식은 종료자를 선언해야 합니다.|
|[CA2220](../code-quality/ca2220.md)|종료자는 기본 클래스 종료자를 호출해야 합니다.|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|serialization 생성자를 구현하십시오.|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|모두 serialize할 수 없는 필드로 표시하십시오.|
|[CA2236](../code-quality/ca2236.md)|ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|SerializableAttribute로 ISerializable 형식 표시|
|[CA2238](../code-quality/ca2238.md)|serialization 메서드를 올바르게 구현하십시오.|
|[CA2240](../code-quality/ca2240.md)|ISerializable을 올바르게 구현하십시오.|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|서식 지정 메서드에 올바른 인수를 제공하십시오.|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|NaN에 대해 정확하게 테스트하십시오.|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|열거형에는 0 값이 있어야 합니다.|
|[CA1013](../code-quality/ca1013.md)|더하기 및 빼기를 오버로드할 때 같음 연산자를 오버로드하세요.|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|리터럴을 지역화된 매개 변수로 전달하지 마세요.|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|대문자로 문자열을 정규화하세요.|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|메서드 결과를 무시하지 마세요.|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|GC.SuppressFinalize를 올바르게 호출하세요.|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|속성은 배열을 반환해서는 안 됩니다.|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|문자열 길이를 사용하여 빈 문자열을 테스트하세요.|
|[CA1903](../code-quality/ca1903.md)|대상 프레임워크의 API만 사용하세요.|
|[CA2004](../code-quality/ca2004.md)|GC.KeepAlive에 대한 호출을 제거하세요.|
|[CA2006](../code-quality/ca2006.md)|SafeHandle을 사용하여 네이티브 리소스를 캡슐화하세요.|
|[CA2102](../code-quality/ca2102.md)|일반 처리기에서 비 CLSCompliant 예외를 catch하세요.|
|[CA2104](../code-quality/ca2104.md)|변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.|
|[CA2105](../code-quality/ca2105.md)|배열 필드는 읽기 전용이면 안 됩니다.|
|[CA2106](../code-quality/ca2106.md)|어설션을 안전하게 보호하세요.|
|[CA2115](../code-quality/ca2115.md)|네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|private 인터페이스를 만족하는 메서드를 봉인하세요.|
|[CA2120](../code-quality/ca2120.md)|serialization 생성자를 안전하게 하세요.|
|[CA2121](../code-quality/ca2121.md)|정적 생성자는 private이어야 합니다.|
|[CA2130](../code-quality/ca2130.md)|보안에 중요한 상수는 투명해야 합니다.|
|[CA2205](../code-quality/ca2205.md)|Win32 API의 동일한 관리형 기능을 사용하세요.|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.|
|[CA2221](../code-quality/ca2221.md)|종료자는 protected여야 합니다.|
|[CA2222](../code-quality/ca2222.md)|상속된 멤버 노출 수준을 낮추지 마세요.|
|[CA2223](../code-quality/ca2223.md)|멤버는 반환 형식 이외의 것도 달라야 합니다.|
|[CA2224](../code-quality/ca2224.md)|같음 연산자를 오버로드할 때 Equals를 재정의하세요.|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|연산자에는 대칭 오버로드가 있어야 합니다.|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|컬렉션 속성은 읽기 전용이어야 합니다.|
|[CA2239](../code-quality/ca2239.md)|선택적 필드에 deserialization 메서드를 제공하세요.|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|표준 예외 생성자를 구현하세요.|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|URI 매개 변수는 문자열이면 안 됩니다.|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|URI 반환 값은 문자열이면 안 됩니다.|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|URI 속성은 문자열이면 안 됩니다.|
|[CA1057](../code-quality/ca1057.md)|문자열 URI 오버로드는 System.Uri 오버로드를 호출합니다.|
|[CA1402](../code-quality/ca1402.md)|COM 노출 인터페이스에서 오버로드를 사용하지 마세요.|
|[CA1406](../code-quality/ca1406.md)|Visual Basic 6 클라이언트에서는 Int64 인수를 사용하지 마세요.|
|[CA1407](../code-quality/ca1407.md)|COM 노출 형식에 정적 멤버를 사용하지 마세요.|
|[CA1408](../code-quality/ca1408.md)|AutoDual ClassInterfaceType을 사용하지 마세요.|
|[CA1409](../code-quality/ca1409.md)|Com 노출 형식을 만들 수 있어야 합니다.|
|[CA1411](../code-quality/ca1411.md)|COM 등록 메서드는 노출되면 안 됩니다.|
|[CA1412](../code-quality/ca1412.md)|ComSource 인터페이스를 IDispatch로 표시하세요.|
|[CA1413](../code-quality/ca1413.md)|COM 노출 값 형식에 public이 아닌 필드를 사용하지 마세요.|
|[CA1414](../code-quality/ca1414.md)|부울 P/Invoke 인수를 MarshalAs로 표시하세요.|
|[CA1600](../code-quality/ca1600.md)|유휴 프로세스 우선 순위를 사용하지 마세요.|
|[CA1601](../code-quality/ca1601.md)|전원 상태 변경을 방해하는 타이머를 사용하지 마세요.|
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|NeutralResourcesLanguageAttribute로 어셈블리를 표시하세요.|
|[CA2001](../code-quality/ca2001.md)|문제가 있는 메서드는 호출하지 마세요.|
|[CA2003](../code-quality/ca2003.md)|파이버를 스레드로 취급하지 마세요.|
|[CA2135](../code-quality/ca2135.md)|수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.|
|[CA2136](../code-quality/ca2136.md)|멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.|
|[CA2139](../code-quality/ca2139.md)|투명 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다.|
|[CA2142](../code-quality/ca2142.md)|투명 코드는 LinkDemands로 보호될 수 없습니다.|
|[CA2143](../code-quality/ca2143.md)|투명 메서드는 보안 요청을 사용할 수 없습니다.|
|[CA2144](../code-quality/ca2144.md)|투명 코드는 바이트 배열에서 어셈블리를 로드할 수 없습니다.|
|[CA2145](../code-quality/ca2145.md)|투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅할 수 없습니다.|
|[CA2204](../code-quality/ca2204.md)|리터럴의 맞춤법이 정확해야 합니다.|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|비상수 필드는 노출되면 안 됩니다.|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|열거형을 FlagsAttribute로 표시하지 마세요.|
|[CA2218](../code-quality/ca2218.md)|Equals를 재정할 때 GetHashCode를 재정의하세요.|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|exception 절에서 예외를 발생시키지 마세요.|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|연산자 오버로드에는 명명된 대체 항목이 있습니다.|
|[CA2228](../code-quality/ca2228.md)|릴리스되지 않은 리소스 형식을 제공하지 마세요.|
|[CA2230](../code-quality/ca2230.md)|가변 인수로 params를 사용하세요.|
|[CA2233](../code-quality/ca2233.md)|연산은 오버플로되지 않아야 합니다.|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|문자열 대신 System.Uri 개체를 전달하세요.|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|특성 문자열 리터럴이 올바르게 구문 분석되어야 합니다.|
