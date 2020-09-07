---
title: FxCop 규칙 포트 상태
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508368"
---
# <a name="fxcop-rule-port-status"></a>Fxcop 규칙 포트 상태

이전에 Visual Studio에서 정적 코드 분석을 사용한 경우 현재 구현에서 [FxCop 분석기](install-fxcop-analyzers.md)로 사용할 수 있는 규칙을 궁금할 수 있습니다. 이 페이지에는 이식 된 규칙이 나열 됩니다. 이식 되지 않은 규칙 및 포트를 이식할 계획이 있는지 여부는 이식 되지 않은 [규칙](fxcop-unported-rules.md) 을 참조 하세요.

## <a name="ported-rules"></a>포팅된 규칙

Roslyn-분석기 리포지토리의 자동 [생성 된 설명서 페이지](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) 에는 FxCop 분석기로 이식 된 규칙의 최신 목록이 있습니다. 또한이 페이지에는 규칙이 기본적으로 사용 하도록 설정 되어 있고 연결 된 *코드 수정*이 있는지 여부와 같은 추가 정보가 있습니다. [코드 수정](../ide/quick-actions.md) 사항은 Visual Studio의 전구 아이콘 메뉴에서 사용할 수 있는 한 번 클릭으로 수정 되었습니다.

이 페이지의 날짜를 기준으로 [fxcop 분석기](install-fxcop-analyzers.md) 로 이식 된 fxcop 규칙의 목록에는 다음이 포함 됩니다.

규칙 ID | 제목
--------|---------
[CA1000](ca1000.md) | 정적 멤버를 제네릭 형식으로 선언하지 마세요.
[CA1001](ca1001.md) | 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.
[CA1002](ca1002.md) | 제네릭 목록을 노출하지 마세요.
[CA1003](ca1003.md) | 제네릭 이벤트 처리기 인스턴스를 사용하세요.
[CA1005](ca1005.md) | 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.
[CA1008](ca1008.md) | 열거형에는 0 값이 있어야 합니다.
[CA1010](ca1010.md) | 컬렉션은 제네릭 인터페이스를 구현해야 합니다.
[CA1012](ca1012.md) | 추상 형식에는 생성자를 사용하면 안 됩니다.
[CA1014](ca1014.md) | CLSCompliant로 어셈블리 표시
[CA1016](ca1016.md) | 어셈블리 버전으로 어셈블리 표시
[CA1017](ca1017.md) | ComVisible로 어셈블리 표시
[CA1018](ca1018.md) | AttributeUsageAttribute로 특성을 표시하세요.
[CA1019](ca1019.md) | 특성 인수의 접근자를 정의하세요.
[CA1021](ca1021.md) | out 매개 변수를 사용하지 마세요.
[CA1024](ca1024.md) | 적합한 속성을 사용하세요.
[CA1027](ca1027.md) | 열거형을 FlagsAttribute로 표시하세요.
[CA1028](ca1028.md) | Enum 저장소는 Int32 여야 합니다.
[CA1030](ca1030.md) | 적절한 경우 이벤트를 사용하세요.
[CA1031](ca1031.md) | 일반적인 예외 형식을 catch하지 마세요.
[CA1032](ca1032.md) | 표준 예외 생성자를 구현하세요.
[CA1033](ca1033.md) | 인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.
[CA1034](ca1034.md) | 중첩 형식은 노출되면 안 됩니다.
[CA1036](ca1036.md) | 비교 가능한 형식에 메서드를 재정의하세요.
[CA1040](ca1040.md) | 빈 인터페이스를 사용하지 마세요.
[CA1041](ca1041.md) | ObsoleteAttribute 메시지를 제공하세요.
[CA1043](ca1043.md) | 인덱서에 정수 또는 문자열 인수를 사용 하십시오.
[CA1044](ca1044.md) | 속성은 쓰기 전용이면 안 됩니다.
[CA1045](ca1045.md) | 참조로 형식을 전달하지 마세요.
[CA1046](ca1046.md) | 참조 형식에 같음 연산자를 오버로드하지 마세요.
[CA1047](ca1047.md) | protected 멤버를 sealed 형식으로 선언하지 마세요.
[CA1050](ca1050.md) | 네임스페이스에 형식을 선언하세요.
[CA1051](ca1051.md) | 표시되는 인스턴스 필드를 선언하지 마세요.
[CA1052](ca1052.md) | 정적 소유자 형식은 정적 또는 NotInheritable 이어야 합니다.
[CA1053](ca1053.md) | 정적 소유자 형식에는 생성자를 사용할 수 없습니다 (CA1053는 FxCop 분석기의 [CA1052](ca1052.md) 에 포함 됨).
[CA1054](ca1054.md) | Uri 매개 변수는 문자열이 면 안 됩니다.
[CA1055](ca1055.md) | Uri 반환 값은 문자열이 면 안 됩니다.
[CA1056](ca1056.md) | Uri 속성은 문자열이 면 안 됩니다.
[CA1058](ca1058.md) | 형식은 특정 기본 형식을 확장하면 안 됩니다.
[CA1060](ca1060.md) | Pinvokes를 네이티브 메서드 클래스로 이동
[CA1061](ca1061.md) | 기본 클래스 메서드를 숨기지 마십시오.
[CA1062](ca1062.md) | public 메서드의 인수에 대한 유효성을 검사하세요.
[CA1063](ca1063.md) | IDisposable을 올바르게 구현 하십시오.
[CA1064](ca1064.md) | 예외는 public이어야 합니다.
[CA1065](ca1065.md) | 예기치 않은 위치에서 예외를 발생시키지 마십시오.
[CA1066](ca1066.md) | 형식은 {0} \<T> Equals를 재정의 하기 때문에 IEquatable을 구현 해야 합니다.
[CA1067](ca1067.md) | IEquatable를 구현할 때 개체 Equals (object)를 재정의 합니다.\<T>
[CA1303](ca1303.md) | 리터럴을 지역화된 매개 변수로 전달하지 마세요.
[CA1304](ca1304.md) | CultureInfo를 지정하세요.
[CA1305](ca1305.md) | IFormatProvider를 지정하세요.
[CA1307](ca1307.md) | 명확성을 위해 StringComparison 지정
[CA1308](ca1308.md) | 대문자로 문자열을 정규화하세요.
[CA1309](ca1309.md) | 서 수 문자열 비교 사용
[CA1401](ca1401.md) | P/Invoke는 노출되지 않아야 합니다.
[CA1501](ca1501.md) | 상속성을 너무 많이 사용하지 마세요.
[CA1502](ca1502.md) | 지나치게 복잡하게 만들지 마세요.
[CA1505](ca1505.md) | 유지 관리할 수 없는 코드를 사용하지 마세요.
[CA1506](ca1506.md) | 클래스를 지나치게 많이 결합하지 마세요.
[CA1700](ca1700.md) | 열거형 값의 이름을 'Reserved'로 지정하지 마세요.
[CA1707](ca1707.md) | 식별자에는 밑줄을 사용할 수 없습니다.
[CA1708](ca1708.md) | 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.
[CA1710](ca1710.md) | 식별자에는 올바른 접미사를 사용해야 합니다.
[CA1711](ca1711.md) | 식별자에는 올바른 접미사를 사용해야 합니다.
[CA1712](ca1712.md) | 열거형 값에 형식 이름을 접두사로 사용하지 마세요.
[CA1713](ca1713.md) | 이벤트에 Before 또는 After 접두사를 사용하지 마세요.
[CA1714](ca1714.md) | 플래그 열거형에는 복수형 이름을 사용해야 합니다.
[CA1715](ca1715.md) | 식별자에는 올바른 접두사를 사용해야 합니다.
[CA1716](ca1716.md) | 식별자는 키워드와 달라야 합니다.
[CA1717](ca1717.md) | FlagsAttribute 열거형만 복수형 이름을 가질 수 있습니다.
[CA1720](ca1720.md) | 식별자에 형식 이름이 포함 되어 있습니다.
[CA1721](ca1721.md) | 속성 이름은 Get 메서드와 달라야 합니다.
[CA1724](ca1724.md) | 형식 이름은 네임 스페이스와 일치 하면 안 됩니다.
[CA1725](ca1725.md) | 매개 변수 이름은 기본 선언과 일치해야 합니다.
[CA1801](ca1801.md) | 사용되지 않은 매개 변수를 검토하세요.
[CA1802](ca1802.md) | 적절 한 경우 리터럴 사용
[CA1805](ca1805.md) | 불필요 하 게 초기화 안 함
[CA1806](ca1806.md) | 메서드 결과를 무시하지 마세요.
[CA1810](ca1810.md) | 참조 형식 정적 필드를 인라인으로 초기화하세요.
[CA1812](ca1812.md) | 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.
[CA1813](ca1813.md) | 봉인되지 않은 특성을 사용하지 마세요.
[CA1814](ca1814.md) | 다차원 배열보다 가변 배열을 사용하세요.
[CA1815](ca1815.md) | 값 형식에서 Equals 또는 같음 연산자를 재정의하세요.
[CA1816](ca1816.md) | Dispose 메서드는 Gc.suppressfinalize을 호출 해야 합니다.
[CA1819](ca1819.md) | 속성은 배열을 반환해서는 안 됩니다.
[CA1820](ca1820.md) | 문자열 길이를 사용하여 빈 문자열을 테스트하세요.
[CA1821](ca1821.md) | 빈 종료자 제거
[CA1822](ca1822.md) | 멤버를 static으로 표시하세요.
[CA1823](ca1823.md) | 사용되지 않는 전용 필드를 사용하지 마세요.
[CA1824](ca1824.md) | NeutralResourcesLanguageAttribute로 어셈블리를 표시하세요.
[CA1825](ca1825.md) | 길이가 0 인 배열 할당을 방지 합니다.
[CA2000](ca2000.md) | 범위를 벗어나기 전에 개체를 삭제하세요.
[CA2002](ca2002.md) | 약한 ID를 가진 개체를 잠그지 마십시오.
[CA2100](ca2100.md) | 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.
[CA2101](ca2101.md) | P/Invoke 문자열 인수에 대해 마샬링을 지정하십시오.
[CA2109](ca2109.md) | 표시되는 이벤트 처리기를 검토하세요.
[CA2119](ca2119.md) | private 인터페이스를 만족하는 메서드를 봉인하세요.
[CA2153](ca2153.md) | 손상 된 상태 예외를 Catch 하지 않음
[CA2200](ca2200.md) | 스택 정보를 유지 하도록 다시 throw 합니다.
[CA2201](ca2201.md) | 예약된 예외 형식을 발생시키지 마세요.
[CA2207](ca2207.md) | 값 형식 정적 필드 인라인을 초기화하십시오.
[CA2208](ca2208.md) | 인수 예외를 올바르게 인스턴스화하세요.
[CA2211](ca2211.md) | 비상수 필드는 노출되면 안 됩니다.
[CA2213](ca2213.md) | 삭제 가능한 필드는 삭제해야 합니다.
[CA2214](ca2214.md) | 재정의 가능한 메서드를 생성자에서 호출하지 마십시오.
[CA2215](ca2215.md) | Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.
[CA2216](ca2216.md) | 삭제 가능한 형식은 종료자를 선언해야 합니다.
[CA2217](ca2217.md) | 열거형을 FlagsAttribute로 표시하지 마세요.
[CA2219](ca2219.md) | Finally 절에서 예외를 발생 시 키 지 마십시오.
[CA2225](ca2225.md) | 연산자 오버로드에는 명명된 대체 항목이 있습니다.
[CA2226](ca2226.md) | 연산자에는 대칭 오버로드가 있어야 합니다.
[CA2227](ca2227.md) | 컬렉션 속성은 읽기 전용이어야 합니다.
[CA2229](ca2229.md) | serialization 생성자를 구현하십시오.
[CA2231](ca2231.md) | 오버 로드 연산자 equals 재정의 값 형식 같음
[CA2234](ca2234.md) | 문자열 대신 시스템 uri 개체를 전달 합니다.
[CA2235](ca2235.md) | 모두 serialize할 수 없는 필드로 표시하십시오.
[CA2237](ca2237.md) | ISerializable 형식을 serializable로 표시하세요.
[CA2241](ca2241.md) | 서식 지정 메서드에 올바른 인수를 제공하십시오.
[CA2242](ca2242.md) | NaN에 대해 정확하게 테스트하십시오.
[CA2243](ca2243.md) | 특성 문자열 리터럴이 올바르게 구문 분석되어야 합니다.
[CA2300](ca2300.md) | 안전하지 않은 역직렬 변환기 BinaryFormatter를 사용하지 마세요.
[CA2301](ca2301.md) | 먼저 BinaryFormatter.Binder를 설정하지 않고 BinaryFormatter.Deserialize를 호출하지 마세요.
[CA2302](ca2302.md) | BinaryFormatter.Deserialize를 호출하기 전에 BinaryFormatter.Binder가 설정되었는지 확인합니다.
[CA2305](ca2305.md) | 안전하지 않은 역직렬 변환기 LosFormatter를 사용하지 마세요.
[CA2310](ca2310.md) | 안전하지 않은 역직렬 변환기 NetDataContractSerializer를 사용하지 마세요.
[CA2311](ca2311.md) | 먼저 NetDataContractSerializer.Binder를 설정하지 않고 역직렬화하지 마세요.
[CA2312](ca2312.md) | 역직렬화하기 전에 NetDataContractSerializer.Binder를 설정해야 합니다.
[CA2315](ca2315.md) | 안전하지 않은 역직렬 변환기 ObjectStateFormatter를 사용하지 마세요.
[CA2321](ca2321.md) | SimpleTypeResolver를 사용하여 JavaScriptSerializer를 통해 역직렬화하지 마세요.
[CA2322](ca2322.md) | JavaScriptSerializer가 역직렬화하기 전에 SimpleTypeResolver로 초기화되지 않는지 확인하세요.
[CA3001](ca3001.md) | 코드에서 SQL 주입 취약점에 대해 검토합니다.
[CA3002](ca3002.md) | 코드에서 XSS 취약점에 대해 검토합니다.
[CA3003](ca3003.md) | 코드에서 파일 경로 삽입 취약성에 대해 검토합니다.
[CA3004](ca3004.md) | 코드에서 정보 공개 취약성에 대해 검토합니다.
[CA3005](ca3005.md) | 코드에서 LDAP 주입 취약점에 대해 검토합니다.
[CA3006](ca3006.md) | 코드에서 프로세스 명령 주입 취약점에 대해 검토합니다.
[CA3007](ca3007.md) | 코드에서 오픈 리디렉션 취약점에 대해 검토합니다.
[CA3008](ca3008.md) | 코드에서 XPath 삽입 취약성에 대해 검토합니다.
[CA3009](ca3009.md) | 코드에서 XML 삽입 취약성에 대해 검토합니다.
[CA3010](ca3010.md) | 코드에서 XAML 삽입 취약성에 대해 검토합니다.
[CA3011](ca3011.md) | 코드에서 DLL 삽입 취약성에 대해 검토합니다.
[CA3012](ca3012.md) | 코드에서 regex 삽입 취약성에 대해 검토합니다.
[CA3061](ca3061.md) | URL로 스키마를 추가 하지 않습니다.
[CA3075](ca3075.md) | XML의 안전하지 않은 DTD 처리
[CA3076](ca3076.md) | 안전 하지 않은 XSLT 스크립트 처리
[CA3077](ca3077.md) | API Design, XmlDocument 및 XmlTextReader의 안전 하지 않은 처리
[CA3147](ca3147.md) | 위조 방지 토큰을 사용 하 여 동사 처리기 표시
[CA5350](ca5350.md) | 취약한 암호화 알고리즘을 사용하지 마세요.
[CA5351](ca5351.md) | 끊어진 암호화 알고리즘 사용 안 함
[CA5358](ca5358.md) | 안전하지 않은 암호화 모드를 사용하지 마세요.
CA5359 | 인증서 유효성 검사를 사용 하지 않도록 설정 안 함
CA5360 | Deserialization에서 위험한 메서드를 호출 하지 마십시오.
[CA5361](ca5361.md) | 강력한 암호화의 SChannel 사용을 사용 하지 않도록 설정 안 함
CA5362 | Serializable 클래스에서 자체를 참조 하지 마십시오.
[CA5363](ca5363.md) | 요청 유효성 검사를 사용 하지 않도록 설정 안 함
[CA5364](ca5364.md) | 사용 되지 않는 보안 프로토콜 사용 안 함
CA5365 | HTTP 헤더 검사를 사용 하지 않도록 설정 안 함
CA5366 | 데이터 집합에 XmlReader 사용 Xml 읽기
CA5367 | 포인터 필드를 사용 하 여 형식 직렬화 안 함
CA5368 | 페이지에서 파생 된 클래스에 대해 ViewStateUserKey 설정
[CA5369](ca5369.md) | Deserialization을 위해 XmlReader 사용
[CA5370](ca5370.md) | 판독기의 유효성을 검사 하려면 XmlReader를 사용 합니다.
[CA5371](ca5371.md) | 스키마 읽기에 XmlReader 사용
[CA5372](ca5372.md) | XPathDocument에 XmlReader 사용
[CA5373](ca5373.md) | 사용되지 않는 키 파생 함수를 사용하지 마세요.
CA5374 | XslTransform 사용 안 함
CA5375 | 계정 공유 액세스 서명 사용 안 함
CA5376 | SharedAccessProtocol HttpsOnly 사용
CA5377 | 컨테이너 수준 액세스 정책 사용
[CA5378](ca5378.md) | ServicePointManagerSecurityProtocols를 비활성화하지 마세요.
CA5379 | 약한 키 파생 함수 알고리즘 사용 안 함
CA9999 | 분석기 버전이 일치 하지 않습니다.

## <a name="see-also"></a>참고 항목

- [FxCopAnalyzers 규칙](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
