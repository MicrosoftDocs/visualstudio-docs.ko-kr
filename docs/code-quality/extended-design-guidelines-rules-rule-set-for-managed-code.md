---
title: 관리 코드에 대한 확장 디자인 지침 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8062ef99d3c1ad43b633e896617e95851a40930a
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658596"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>관리 코드에 대한 확장 디자인 지침 규칙 규칙 집합

Microsoft 확장 디자인 지침 규칙 규칙 집합은 기본 디자인 지침 규칙을 확장 하 여 보고 되는 유용성 및 유지 관리 문제를 최대화 합니다. 이름 지정 지침에 대 한 추가 강조를 추가 합니다. 프로젝트에 라이브러리 코드가 포함 되어 있거나 유지 관리가 쉬운 코드를 작성 하는 데 가장 높은 표준을 적용 하려는 경우이 규칙 집합을 포함 하는 것이 좋습니다.

확장 된 디자인 지침 규칙에는 [기본 디자인 지침](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) 규칙 규칙 집합의 모든 규칙이 포함 됩니다. 여기에는 [관리 권장 규칙](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) 규칙 집합의 규칙이 포함 됩니다.

다음 표에서는 Microsoft 확장 디자인 지침 규칙 규칙 집합의 모든 규칙에 대해 설명 합니다.

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
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|정적 멤버를 제네릭 형식으로 선언하지 마세요.|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|제네릭 목록을 노출하지 마세요.|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|제네릭 이벤트 처리기 인스턴스를 사용하세요.|
|[CA1004](../code-quality/ca1004.md)|제네릭 메서드는 형식 매개 변수를 제공해야 합니다.|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.|
|[CA1006](../code-quality/ca1006.md)|멤버 시그니처에 제네릭 형식을 중첩하지 마세요.|
|[CA1007](../code-quality/ca1007.md)|적합한 제네릭을 사용하세요.|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|열거형에는 0 값이 있어야 합니다.|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|컬렉션은 제네릭 인터페이스를 구현해야 합니다.|
|[CA1011](../code-quality/ca1011.md)|기본 형식을 매개 변수로 전달해 보세요.|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|추상 형식에는 생성자를 사용하면 안 됩니다.|
|[CA1013](../code-quality/ca1013.md)|더하기 및 빼기를 오버로드할 때 같음 연산자를 오버로드하세요.|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|CLSCompliantAttribute로 어셈블리를 표시하세요.|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|ComVisibleAttribute로 어셈블리를 표시하세요.|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|AttributeUsageAttribute로 특성을 표시하세요.|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|특성 인수의 접근자를 정의하세요.|
|[CA1023](../code-quality/ca1023.md)|다차원 인덱서를 사용하지 마세요.|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|적합한 속성을 사용하세요.|
|[CA1025](../code-quality/ca1025.md)|반복 인수를 매개 변수 배열로 바꾸세요.|
|[CA1026](../code-quality/ca1026.md)|기본 매개 변수를 사용하면 안 됩니다.|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|열거형을 FlagsAttribute로 표시하세요.|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|열거형 스토리지는 Int32여야 합니다.|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|적절한 경우 이벤트를 사용하세요.|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|일반적인 예외 형식을 catch하지 마세요.|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|표준 예외 생성자를 구현하세요.|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|중첩 형식은 노출되면 안 됩니다.|
|[CA1035](../code-quality/ca1035.md)|ICollection 구현에 강력한 형식의 멤버가 있습니다.|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|비교 가능한 형식에 메서드를 재정의하세요.|
|[CA1038](../code-quality/ca1038.md)|열거자는 강력한 형식이어야 합니다.|
|[CA1039](../code-quality/ca1039.md)|목록은 강력한 형식이어야 합니다.|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|ObsoleteAttribute 메시지를 제공하세요.|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|인덱서에 정수 또는 문자열 인수를 사용하세요.|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|속성은 쓰기 전용이면 안 됩니다.|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|참조 형식에 같음 연산자를 오버로드하지 마세요.|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|protected 멤버를 sealed 형식으로 선언하지 마세요.|
|[CA1048](../code-quality/ca1048.md)|가상 멤버를 sealed 형식으로 선언하지 마세요.|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|네임스페이스에 형식을 선언하세요.|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|표시되는 인스턴스 필드를 선언하지 마세요.|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|정적 소유자 형식은 sealed여야 합니다.|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|정적 소유자 형식에는 생성자를 사용하면 안 됩니다.|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|URI 매개 변수는 문자열이면 안 됩니다.|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|URI 반환 값은 문자열이면 안 됩니다.|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|URI 속성은 문자열이면 안 됩니다.|
|[CA1057](../code-quality/ca1057.md)|문자열 URI 오버로드는 System.Uri 오버로드를 호출합니다.|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|형식은 특정 기본 형식을 확장하면 안 됩니다.|
|[CA1059](../code-quality/ca1059.md)|멤버는 구체적인 특정 형식을 노출하면 안 됩니다.|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|예외는 public이어야 합니다.|
|[CA1500](../code-quality/ca1500.md)|변수 이름은 필드 이름과 달라야 합니다.|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|지나치게 복잡하게 만들지 마세요.|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|식별자는 키워드와 달라야 합니다.|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|사용되지 않은 매개 변수를 검토하세요.|
|[CA1804](../code-quality/ca1804.md)|사용되지 않는 로컬 항목을 제거하세요.|
|[CA1809](../code-quality/ca1809.md)|불필요한 로컬 항목을 사용하지 마세요.|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|참조 형식 정적 필드를 인라인으로 초기화하세요.|
|[CA1811](../code-quality/ca1811.md)|호출되지 않는 전용 코드를 사용하지 마세요.|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|인스턴스화되지 않은 내부 클래스를 사용하지 마세요.|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|봉인되지 않은 특성을 사용하지 마세요.|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|다차원 배열보다 가변 배열을 사용하세요.|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|값 형식에서 Equals 또는 같음 연산자를 재정의하세요.|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|속성은 배열을 반환해서는 안 됩니다.|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|문자열 길이를 사용하여 빈 문자열을 테스트하세요.|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|멤버를 static으로 표시하세요.|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|사용되지 않는 전용 필드를 사용하지 마세요.|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|예약된 예외 형식을 발생시키지 마세요.|
|[CA2205](../code-quality/ca2205.md)|Win32 API의 동일한 관리형 기능을 사용하세요.|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|인수 예외를 올바르게 인스턴스화하세요.|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|비상수 필드는 노출되면 안 됩니다.|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|열거형을 FlagsAttribute로 표시하지 마세요.|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|exception 절에서 예외를 발생시키지 마세요.|
|[CA2221](../code-quality/ca2221.md)|종료자는 protected여야 합니다.|
|[CA2222](../code-quality/ca2222.md)|상속된 멤버 노출 수준을 낮추지 마세요.|
|[CA2223](../code-quality/ca2223.md)|멤버는 반환 형식 이외의 것도 달라야 합니다.|
|[CA2224](../code-quality/ca2224.md)|같음 연산자를 오버로드할 때 Equals를 재정의하세요.|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|연산자 오버로드에는 명명된 대체 항목이 있습니다.|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|연산자에는 대칭 오버로드가 있어야 합니다.|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|컬렉션 속성은 읽기 전용이어야 합니다.|
|[CA2230](../code-quality/ca2230.md)|가변 인수로 params를 사용하세요.|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|문자열 대신 System.Uri 개체를 전달하세요.|
|[CA2239](../code-quality/ca2239.md)|선택적 필드에 deserialization 메서드를 제공하세요.|
|[CA1020](../code-quality/ca1020.md)|형식이 부족한 네임스페이스를 사용하지 마세요.|
|[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021)|out 매개 변수를 사용하지 마세요.|
|[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040)|빈 인터페이스를 사용하지 마세요.|
|[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045)|참조로 형식을 전달하지 마세요.|
|[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062)|public 메서드의 인수에 대한 유효성을 검사하세요.|
|[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)|상속성을 너무 많이 사용하지 마세요.|
|[CA1504](../code-quality/ca1504.md)|잘못된 필드 이름을 검토하세요.|
|[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)|유지 관리할 수 없는 코드를 사용하지 마세요.|
|[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)|클래스를 지나치게 많이 결합하지 마세요.|
|[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700)|열거형 값의 이름을 'Reserved'로 지정하지 마세요.|
|[CA1701](../code-quality/ca1701.md)|리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.|
|[CA1702](../code-quality/ca1702.md)|복합 단어는 정확한 대/소문자를 사용해야 합니다.|
|[CA1703](../code-quality/ca1703.md)|리소스 문자열에는 정확한 철자를 사용해야 합니다.|
|[CA1704](../code-quality/ca1704.md)|식별자에는 정확한 철자를 사용해야 합니다.|
|[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707)|식별자에는 밑줄을 사용할 수 없습니다.|
|[CA1709](../code-quality/ca1709.md)|식별자는 정확한 대/소문자를 사용해야 합니다.|
|[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)|식별자에는 올바른 접미사를 사용해야 합니다.|
|[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711)|식별자에는 올바른 접미사를 사용해야 합니다.|
|[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712)|열거형 값에 형식 이름을 접두사로 사용하지 마세요.|
|[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713)|이벤트에 Before 또는 After 접두사를 사용하지 마세요.|
|[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714)|플래그 열거형에는 복수형 이름을 사용해야 합니다.|
|[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715)|식별자에는 올바른 접두사를 사용해야 합니다.|
|[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717)|FlagsAttribute 열거형만 복수형 이름을 가질 수 있습니다.|
|[CA1719](../code-quality/ca1719.md)|매개 변수 이름은 멤버 이름과 달라야 합니다.|
|[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720)|식별자에 형식 이름을 포함하면 안 됩니다.|
|[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721)|속성 이름은 Get 메서드와 달라야 합니다.|
|[CA1722](../code-quality/ca1722.md)|식별자에는 올바른 접두사를 사용해야 합니다.|
|[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724)|형식 이름은 네임스페이스와 달라야 합니다.|
|[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725)|매개 변수 이름은 기본 선언과 일치해야 합니다.|
|[CA1726](../code-quality/ca1726.md)|기본 설정 용어를 사용하세요.|
|[CA2204](../code-quality/ca2204.md)|리터럴의 맞춤법이 정확해야 합니다.|
