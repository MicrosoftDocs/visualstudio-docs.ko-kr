---
title: 관리되는 코드에 대한 CheckId별 코드 분석 경고
ms.date: 04/18/2019
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1417
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1805
- CA1806
- CA1809
- CA1810
- CA1811
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1835
- CA1836
- CA1838
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA5122
- CA5374
- IL3000
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 040df1edf85f2879cd2666e79768e76969464522
ms.sourcegitcommit: 2946d802aec1418e87bfa779d81834eeb7be5c9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88214599"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>관리 코드 CheckId 별 코드 분석 경고

다음 표에서는 관리 코드에 대한 코드 분석 경고를 경고의 CheckId 식별자별로 보여 줍니다.

| CheckId | Warning | Description |
|---------| - | - |
| CA1000 | [CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.](../code-quality/ca1000.md) | 제네릭 형식의 정적 멤버를 호출할 때는 형식에 형식 인수를 지정해야 합니다. 유추를 지원하지 않는 제네릭 인스턴스 멤버를 호출할 때는 멤버에 형식 인수를 지정해야 합니다. 이 두 가지 경우에 형식 인수를 지정하기 위한 구문은 서로 다르며 혼동되기 쉽습니다. |
| CA1001 | [CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1001.md) | 클래스가 System.IDisposable 형식인 인스턴스 필드를 선언하고 구현하지만 IDisposable은 구현하지 않습니다. IDisposable 필드를 선언하는 클래스는 관리되지 않는 리소스를 간접적으로 소유하며 IDisposable 인터페이스를 구현해야 합니다. |
| CA1002 | [CA1002: 제네릭 목록을 노출하지 마세요.](../code-quality/ca1002.md) | < (Of \<(T> ) >)는 상속이 아닌 성능을 위해 디자인 된 제네릭 컬렉션입니다. 따라서 List에는 가상 멤버가 포함되지 않습니다. 상속을 위해 디자인된 제네릭 컬렉션이 대신 노출되어야 합니다. |
| CA1003 | [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.](../code-quality/ca1003.md) |void를 반환 하며 해당 시그니처에 두 개의 매개 변수 (개체가 첫 번째 및 두 번째는 EventArgs에 할당 될 수 있는 형식)를 포함 하는 대리자를 포함 하는 형식을 포함 하는 어셈블리에는 Microsoft.NET Framework 2.0 대상으로 합니다. |
| CA1004 | [CA1004: 제네릭 메서드는 형식 매개 변수를 제공해야 합니다.](../code-quality/ca1004.md) | 제네릭 메서드의 형식 인수가 형식 인수를 명시적으로 지정하는 대신 메서드로 전달된 인수의 형식에 따라 결정되는 방식을 유추라고 합니다. 유추를 사용하려면 제네릭 메서드의 매개 변수 시그니처에 메서드에 대한 형식 매개 변수와 같은 형식의 매개 변수가 포함되어야 합니다. 이 경우 형식 인수는 지정할 필요가 없습니다. 모든 형식 매개 변수에 대해 유추를 사용하는 경우 제네릭과 제네릭이 아닌 인스턴스 메서드를 호출하는 구문은 동일합니다. 따라서 제네릭 메서드를 사용하기가 간편해집니다. |
| CA1005 | [CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.](../code-quality/ca1005.md) | 제네릭 형식에 포함된 형식 매개 변수가 많을수록 각 형식 매개 변수가 무엇을 나타내는지를 파악하거나 기억하기가 더 어렵습니다. 일반적으로 목록에서와 같이 하나의 형식 매개 변수를 사용 하 \<T> 고 사전에서와 같이 두 개의 형식 매개 변수를 사용 하는 것이 명확 \<TKey, TValue> 합니다. 그러나 형식 매개 변수가 세 개 이상이면 대부분의 사용자가 사용하기에 너무 어렵습니다. |
| CA1006 | [CA1006: 멤버 시그니처에 제네릭 형식을 중첩하지 마세요.](../code-quality/ca1006.md) | 중첩된 형식 인수는 제네릭 형식의 인수입니다. 시그니처에 중첩된 형식 인수가 포함되어 있는 멤버를 호출하려면 제네릭 형식 하나를 인스턴스화하고 이 형식을 두 번째 제네릭 형식의 생성자에 전달해야 합니다. 이 경우 복잡한 프로시저와 구문이 필요하므로 이 방법을 피해야 합니다. |
| CA1007 |[CA1007: 적합한 제네릭을 사용하세요.](../code-quality/ca1007.md) | 외부에서 볼 수 있는 메서드에 System.Object 형식의 참조 매개 변수가 포함되어 있습니다. 제네릭 메서드를 사용하면 제약 조건에 따라 형식을 참조 매개 변수 형식으로 먼저 캐스팅하지 않고도 모든 형식을 메서드에 전달할 수 있습니다. |
| CA1008 | [CA1008: 열거형에는 0 값이 있어야 합니다.](../code-quality/ca1008.md) | 초기화되지 않은 열거형의 기본값은 다른 값 형식과 마찬가지로 0입니다. 플래그 특성을 사용하지 않는 열거형에서는 기본값이 열거형의 유효한 값이 되도록 0 값을 사용하여 멤버를 정의해야 합니다. FlagsAttribute 특성이 적용된 열거형에서 0 값을 가진 멤버를 정의하는 경우에는 열거형에 값이 설정되지 않았음을 나타낼 수 있도록 해당 멤버 이름이 "None"이어야 합니다. |
| CA1009 | [CA1009: 이벤트 처리기를 제대로 선언하십시오.](../code-quality/ca1009.md) | 이벤트 처리기 메서드는 두 개의 매개 변수를 사용합니다. 첫 번째 매개 변수는 System.Object 형식이고 이름은 "sender"입니다. 이 매개 변수는 이벤트를 발생시킨 개체입니다. 두 번째 매개 변수는 System.EventArgs 형식이고 이름은 "e"입니다. 이 매개 변수는 이벤트와 관련된 데이터입니다. 이벤트 처리기 메서드는 값을 반환하지 않아야 하며, C# 프로그래밍 언어에서 이는 반환 형식 void로 표시됩니다. |
| CA1010 | [CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.](../code-quality/ca1010.md) | 컬렉션의 유용성을 높이려면 제네릭 컬렉션 인터페이스 중 하나를 구현합니다. 그러면 컬렉션을 사용하여 제네릭 컬렉션 형식을 채울 수 있습니다. |
| CA1011 |[CA1011: 기본 형식을 매개 변수로 전달해 보세요.](../code-quality/ca1011.md) | 기본 형식이 메서드 선언의 매개 변수로 지정된 경우 기본 형식에서 파생된 모든 형식을 해당 인수로 메서드에 전달할 수 있습니다. 파생된 매개 변수 형식에서 제공하는 추가 기능이 필요하지 않은 경우 기본 형식을 사용하면 메서드를 보다 광범위하게 사용할 수 있습니다. |
| CA1012 | [CA1012: 추상 형식에는 생성자를 사용하면 안 됩니다.](../code-quality/ca1012.md) | 추상 형식에 대한 생성자는 파생된 형식에서만 호출할 수 있습니다. public 생성자에서 형식의 인스턴스를 만들고 사용자는 추상 형식의 인스턴스를 만들 수 없기 때문에 public 생성자가 있는 추상 형식은 잘못 디자인된 것입니다. |
| CA1013 | [CA1013: 더하기 및 빼기를 오버로드할 때 같음 연산자를 오버로드하세요.](../code-quality/ca1013.md) | public 또는 protected 형식이 같음 연산자를 구현하지 않고 더하기 또는 빼기 연산자를 구현합니다. |
| CA1014 | [CA1014: CLSCompliantAttribute로 어셈블리를 표시하세요.](../code-quality/ca1014.md) | CLS(공용 언어 사양)는 어셈블리가 여러 프로그래밍 언어에 사용될 경우 준수해야 하는 명명 제한, 데이터 형식 및 규칙을 정의합니다. 모든 어셈블리에는 <xref:System.CLSCompliantAttribute>를 사용하여 CLS 규격을 명시적으로 나타내는 것이 좋습니다. 어셈블리에 이 특성이 없으면 해당 어셈블리는 규격을 따르지 않습니다. |
| CA1016 | [CA1016: AssemblyVersionAttribute로 어셈블리 표시](../code-quality/ca1016.md) | .NET에서는 버전 번호를 사용 하 여 어셈블리를 고유 하 게 식별 하 고 강력한 이름의 어셈블리에 있는 형식에 바인딩합니다. 버전 번호는 버전 및 게시자 정책과 함께 사용됩니다. 기본적으로 애플리케이션은 해당 애플리케이션이 빌드될 때 사용된 어셈블리 버전으로만 실행됩니다. |
| CA1017 | [CA1017: ComVisibleAttribute로 어셈블리를 표시하세요.](../code-quality/ca1017.md) |ComVisibleAttribute는 COM 클라이언트에서 관리 코드에 액세스하는 방식을 결정합니다. 어셈블리에서 COM에 노출할지 여부를 명시적으로 나타내는 것이 좋은 디자인입니다. 전체 어셈블리에 대해 COM 노출 여부를 설정한 다음 개별 형식 및 형식 멤버에 대해 이를 재정의할 수 있습니다. 이 특성이 없으면 COM 클라이언트에서 어셈블리의 내용을 볼 수 있습니다. |
| CA1018 | [CA1018: AttributeUsageAttribute로 특성을 표시하세요.](../code-quality/ca1018.md) | 사용자 지정 특성을 정의할 때는 해당 특성을 AttributeUsageAttribute로 표시하여 사용자 지정 특성을 적용할 수 있는 소스 코드의 위치를 나타냅니다. 특성의 의미 및 용도에 따라 코드에서의 유효한 위치가 결정됩니다. |
| CA1019 | [CA1019: 특성 인수의 접근자를 정의하세요.](../code-quality/ca1019.md) | 특성에서는 대상에 특성을 적용할 때 지정해야 하는 필수 인수를 정의할 수 있습니다. 이러한 인수는 특성 생성자에 위치 매개 변수로 제공되기 때문에 이러한 인수를 위치 인수라고도 합니다. 모든 필수 인수에 대해 특성은 실행 시간에 인수의 값을 검색할 수 있도록 해당하는 읽기 전용 속성도 제공해야 합니다. 특성에서는 명명된 인수라고 하는 선택적 인수도 정의할 수 있습니다. 이들 인수는 이름으로 특성 생성자에 제공되며 해당하는 읽기/쓰기 특성이 있어야 합니다. |
| CA1020 | [CA1020: 형식이 부족한 네임스페이스를 사용하지 마세요.](../code-quality/ca1020.md) | 각 네임스페이스에 논리적 구성이 있는지, 형식이 부족한 네임스페이스에 형식을 배치하는 타당한 근거가 있는지 확인합니다. |
| CA1021 | [CA1021: out 매개 변수를 사용하지 마세요.](../code-quality/ca1021.md) | out 또는 ref를 사용하여 참조로 형식을 전달하려면 포인터 사용 방법을 알고 있어야 하고, 값 형식과 참조 형식이 어떻게 다른지 알고 있어야 하며, 반환 값이 여러 개인 메서드를 처리할 수 있어야 합니다. 또한 out 매개 변수와 ref 매개 변수의 차이점은 잘 알려져 있지 않습니다. |
| CA1023 | [CA1023: 다차원 인덱서를 사용하지 마세요.](../code-quality/ca1023.md) | 인덱서, 즉 인덱싱된 속성은 단일 인덱스를 사용해야 합니다. 다차원 인덱서를 사용하면 라이브러리의 유용성이 현저히 줄어들 수 있습니다. |
| CA1024 | [CA1024: 적합한 속성을 사용하세요.](../code-quality/ca1024.md) | public 또는 protected 메서드가 "Get"으로 시작하는 이름을 사용하고, 매개 변수를 사용하지 않으며, 배열이 아닌 값을 반환합니다. 이 메서드는 속성이 될 수 있는 좋은 예일 수 있습니다. |
| CA1025 | [CA1025: 반복 인수를 매개 변수 배열로 바꾸세요.](../code-quality/ca1025.md) | 인수의 정확한 개수를 알 수 없는데 가변 인수가 같은 형식이거나 같은 형식으로서 전달될 수 있는 경우에는 반복되는 인수 대신 매개 변수 배열을 사용합니다. |
| CA1026 | [CA1026: 기본 매개 변수를 사용하면 안 됩니다.](../code-quality/ca1026.md) | CLS에서는 기본 매개 변수를 사용하는 메서드를 허용하지만 컴파일러가 이러한 매개 변수에 할당된 값을 무시할 수 있도록 합니다. 여러 프로그래밍 언어에서 원하는 동작을 유지하려면 기본 매개 변수를 사용하는 메서드를 기본 매개 변수를 제공하는 메서드 오버로드로 바꿔야 합니다. |
| CA1027 |[CA1027: 열거형을 FlagsAttribute로 표시하세요.](../code-quality/ca1027.md) | 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 명명된 상수를 의미 있게 조합할 수 있는 경우 열거형에 FlagsAttribute를 적용합니다. |
| CA1028 | [CA1028: 열거형 스토리지는 Int32여야 합니다.](../code-quality/ca1028.md) | 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 기본적으로 System.Int32 데이터 형식은 상수 값을 저장하는 데 사용됩니다. 이 내부 형식을 변경할 수 있지만 대부분의 시나리오에서는 변경이 필요하지 않거나 권장되지 않습니다. |
| CA1030 | [CA1030: 적절한 경우 이벤트를 사용하세요.](../code-quality/ca1030.md) |이 규칙에서는 보통 이벤트에 사용되는 이름을 갖는 메서드를 찾아냅니다. 명확하게 정의된 상태 변경에 대한 응답으로 메서드를 호출할 경우 이 메서드는 이벤트 처리기에서 호출해야 합니다. 메서드를 호출하는 개체는 메서드를 직접 호출하는 대신 이벤트를 발생시켜야 합니다. |
| CA1031 | [CA1031: 일반적인 예외 형식을 catch하지 마세요.](../code-quality/ca1031.md) | 일반 예외는 catch하면 안 됩니다. 보다 구체적인 예외를 catch하거나, 일반적인 예외를 catch 블록의 마지막 문으로 다시 throw해야 합니다. |
| CA1032 |[CA1032: 표준 예외 생성자를 구현하세요.](../code-quality/ca1032.md) | 이들 생성자 집합을 전부 제공하지 못하면 예외를 제대로 처리하기 어려울 수 있습니다. |
| CA1033 | [CA1033: 인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.](../code-quality/ca1033.md) | 외부에서 볼 수 있는 unsealed 형식이 public 인터페이스의 명시적 메서드 구현을 제공하면서 외부에서 볼 수 있는 같은 이름의 대체 메서드를 제공하지 않습니다. |
| CA1034 | [CA1034: 중첩 형식은 노출되면 안 됩니다.](../code-quality/ca1034.md) | 중첩 형식은 다른 형식의 범위 내에 선언된 형식입니다. 중첩 형식은 포함하는 형식의 private 구현 정보를 캡슐화하는 데 유용합니다. 이 용도로 사용할 경우 중첩 형식은 외부에 노출되면 안 됩니다. |
| CA1035 | [CA1035: ICollection 구현에 강력한 형식의 멤버가 있습니다.](../code-quality/ca1035.md) | 이 규칙에서는 사용자가 인터페이스에서 제공하는 기능을 사용할 때 인수를 Object 형식으로 캐스팅할 필요가 없도록 ICollection 구현에서 강력한 형식의 멤버를 제공할 것을 요구합니다. 이 규칙에서는 ICollection을 구현하는 형식이 이를 수행하여 Object보다 강력한 형식의 인스턴스 컬렉션을 관리한다고 가정합니다. |
| CA1036 | [CA1036: 비교 가능한 형식에 메서드를 재정의하세요.](../code-quality/ca1036.md) |public 또는 protected 형식이 System.IComparable 인터페이스를 구현합니다. 이 형식은 Object.Equals를 재정의하지 않으며 같음, 같지 않음, 보다 작음 또는 보다 큼에 대한 언어별 연산자를 오버로드하지 않습니다. |
| CA1038 | [CA1038: 열거자는 강력한 형식이어야 합니다.](../code-quality/ca1038.md) | 이 규칙에서는 사용자가 인터페이스에서 제공하는 기능을 사용할 때 반환 값을 강력한 형식으로 캐스팅할 필요가 없도록 IEnumerator 구현에서 Current 속성의 강력한 형식 버전도 제공할 것을 요구합니다. |
| CA1039 | [CA1039: 목록은 강력한 형식이어야 합니다.](../code-quality/ca1039.md) | 이 규칙에서는 사용자가 인터페이스에서 제공하는 기능을 사용할 때 인수를 System.Object 형식으로 캐스팅할 필요가 없도록 IList 구현에서 강력한 형식의 멤버를 제공할 것을 요구합니다. |
| CA1040 |[CA1040: 빈 인터페이스를 사용하지 마세요.](../code-quality/ca1040.md) | 인터페이스에서는 동작이나 사용 계약을 제공하는 멤버를 정의합니다. 인터페이스에 의해 설명되는 기능은 상속 계층 구조에서 형식이 나타나는 위치에 관계없이 모든 형식에서 사용할 수 있습니다. 형식에서는 인터페이스의 멤버에 대한 구현을 제공하여 인터페이스를 구현합니다. 빈 인터페이스는 멤버를 정의하지 않으므로 구현 가능한 계약을 정의하지 않습니다. |
| CA1041 | [CA1041: ObsoleteAttribute 메시지를 제공하세요.](../code-quality/ca1041.md) | 형식 또는 멤버가 ObsoleteAttribute.Message 속성이 지정되지 않은 System.ObsoleteAttribute 특성으로 표시되어 있습니다. ObsoleteAttribute로 표시된 형식 또는 멤버를 컴파일하면 해당 특성의 Message 속성이 표시되어 사용되지 않는 형식 또는 멤버에 대한 정보가 사용자에게 제공됩니다. |
| CA1043 | [CA1043: 인덱서에 정수 또는 문자열 인수를 사용하세요.](../code-quality/ca1043.md) | 인덱서, 즉 인덱싱된 속성은 인덱스에 정수 계열 형식이나 문자열 형식을 사용해야 합니다. 이러한 형식은 대개 데이터 구조를 인덱싱하는 데 사용되며 라이브러리의 유용성을 증가시킵니다. Object 형식은 디자인 타임에 특정 정수 계열 형식이나 문자열 형식을 지정할 수 없는 경우에만 제한적으로 사용해야 합니다. |
| CA1044 | [CA1044: 속성은 쓰기 전용이면 안 됩니다.](../code-quality/ca1044.md) | 읽기 전용 속성을 사용하는 것은 가능하고 종종 필요하기도 하지만 쓰기 전용 속성의 사용은 금지되어 있습니다. 사용자에게 값을 설정하도록 허용한 다음 해당 값을 볼 수 없도록 하면 보안상 문제가 있기 때문입니다. 또한 읽기 권한이 없으면 공유 개체의 상태를 볼 수 없으므로 사용하는 데 제한을 받습니다. |
| CA1045 |[CA1045: 참조로 형식을 전달하지 마세요.](../code-quality/ca1045.md) | out 또는 ref를 사용하여 참조로 형식을 전달하려면 포인터 사용 방법을 알고 있어야 하고, 값 형식과 참조 형식이 어떻게 다른지 알고 있어야 하며, 반환 값이 여러 개인 메서드를 처리할 수 있어야 합니다. 일반 사용자를 위해 디자인 한 라이브러리 설계자는 사용자가 `out` 또는 매개 변수로 작업 하는 것을 원하지 않습니다 `ref` . |
| CA1046 | [CA1046: 참조 형식에 같음 연산자를 오버로드하지 마세요.](../code-quality/ca1046.md) | 참조 형식의 경우 같음 연산자의 기본 구현은 대부분 항상 올바릅니다. 기본적으로 두 참조는 같은 개체를 가리킬 경우에만 같습니다. |
| CA1047 |[CA1047: protected 멤버를 sealed 형식으로 선언하지 마세요.](../code-quality/ca1047.md) | 형식에서는 상속하는 형식에서 멤버에 액세스하거나 멤버를 재정의할 수 있도록 하기 위해 protected 멤버를 선언합니다. 정의에 따라 sealed 형식은 상속할 수 없으므로 sealed 형식에 대해 protected 메서드를 호출할 수 없습니다. |
| CA1048 | [CA1048: 가상 멤버를 sealed 형식으로 선언하지 마세요.](../code-quality/ca1048.md) | 상속 형식이 가상 메서드의 구현을 재정의할 수 있도록 하기 위해 형식은 메서드를 가상으로 선언합니다. 정의에 따라 sealed 형식은 상속할 수 없습니다. 따라서 sealed 형식에 대한 가상 메서드는 의미가 없습니다. |
| CA1049 | [CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1049.md) | 관리되지 않는 리소스를 할당하는 형식은 IDisposable을 구현하여 호출자가 필요할 때 해당 리소스를 해제할 수 있도록 하고 리소스를 차지하고 있는 개체의 수명을 줄여야 합니다. |
| CA1050 | [CA1050: 네임스페이스에 형식을 선언하세요.](../code-quality/ca1050.md) | 이름 충돌을 방지하고 관련된 형식을 개체 계층 구조로 구성하기 위해 형식은 네임스페이스 안에 선언됩니다. |
| CA1051 | [CA1051: 표시되는 인스턴스 필드를 선언하지 마세요.](../code-quality/ca1051.md) | 필드의 주된 용도는 구현을 세부적으로 설명하는 것입니다. 필드는 private 또는 internal이어야 하고 속성을 통해 노출되어야 합니다. |
| CA1052 | [CA1052: 정적 소유자 형식은 sealed여야 합니다.](../code-quality/ca1052.md) | public 또는 protected 형식이 정적 멤버만 포함하며 sealed(C# 참조)(NotInheritable) 한정자로 선언되지 않았습니다. 상속을 고려하지 않은 형식은 sealed 한정자로 표시하여 기본 형식으로 사용되지 않도록 해야 합니다. |
| CA1053 |[CA1053: 정적 소유자 형식에는 생성자를 사용하면 안 됩니다.](../code-quality/ca1053.md) | public 또는 중첩된 public 형식에서 정적 멤버만 선언하며 public 또는 protected 기본 생성자를 사용합니다. 호출하는 정적 멤버에 형식의 인스턴스가 필요하지 않기 때문에 생성자가 필요 없습니다. 문자열 오버로드는 안전과 보안을 위해 문자열 인수를 사용하여 URI(Uniform Resource Identifier) 오버로드를 호출해야 합니다. |
| CA1054 | [CA1054: URI 매개 변수는 문자열이면 안 됩니다.](../code-quality/ca1054.md) | 메서드가 URI의 문자열 표현을 사용하면 URI 클래스의 인스턴스를 사용하는 해당 오버로드를 제공해야 합니다. 이렇게 하면 서비스가 안전한 방식으로 제공됩니다. |
| CA1055 | [CA1055: URI 반환 값은 문자열이면 안 됩니다.](../code-quality/ca1055.md) | 이 규칙에서는 메서드가 URI를 반환한다고 가정합니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. System.Uri 클래스는 이러한 서비스를 안전한 방식으로 제공합니다. |
| CA1056 | [CA1056: URI 속성은 문자열이면 안 됩니다.](../code-quality/ca1056.md) | 이 규칙에서는 속성이 URI(Uniform Resource Identifier)를 나타낸다고 가정합니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. System.Uri 클래스는 이러한 서비스를 안전한 방식으로 제공합니다. |
| CA1057 | [CA1057: 문자열 URI 오버로드는 System.Uri 오버로드를 호출합니다.](../code-quality/ca1057.md) | 형식에서 문자열 매개 변수가 System.Uri 매개 변수로 바뀐 점만 다른 메서드 오버로드를 선언합니다. 문자열 매개 변수를 사용하는 오버로드는 URI 매개 변수를 사용하는 오버로드를 호출하지 않습니다. |
| CA1058 | [CA1058: 형식은 특정 기본 형식을 확장하면 안 됩니다.](../code-quality/ca1058.md) | 외부에서 볼 수 있는 형식이 특정 기본 형식을 확장합니다. 다음 방법 중 하나를 사용합니다. |
| CA1059 |[CA1059: 멤버는 구체적인 특정 형식을 노출하면 안 됩니다.](../code-quality/ca1059.md) | 구체적인 형식은 완전히 구현되었기 때문에 인스턴스화할 수 있는 형식을 말합니다. 멤버를 광범위하게 사용할 수 있도록 하려면 구체적인 형식을 제안된 인터페이스로 바꾸십시오. |
| CA1060 | [CA1060: P/Invoke를 NativeMethods 클래스로 이동 합니다.](../code-quality/ca1060.md) | System.Runtime.InteropServices.DllImportAttribute 특성으로 표시된 메서드나 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]에서 Declare 키워드를 사용하여 정의된 메서드 같은 플랫폼 호출 메서드에서는 비관리 코드에 액세스합니다. 이러한 메서드는 NativeMethods, SafeNativeMethods 또는 UnsafeNativeMethods 클래스에 속해야 합니다. |
| CA1061 |[CA1061: 기본 클래스 메서드를 숨기지 마십시오.](../code-quality/ca1061.md) | 파생된 메서드의 매개 변수 시그니처가 기본 메서드의 매개 변수 시그니처에 있는 해당 형식보다 더 약하게 파생된 형식이라는 점만 다른 경우 기본 형식의 메서드는 파생된 형식에 있는 동일한 이름의 메서드에 의해 숨겨집니다. |
| CA1062 | [CA1062: public 메서드의 인수에 대한 유효성을 검사하세요.](../code-quality/ca1062.md) | 외부에서 볼 수 있는 메서드에 전달되는 모든 참조 인수는 null인지 여부를 검사해야 합니다. |
| CA1063 | [CA1063: IDisposable을 올바르게 구현하십시오.](../code-quality/ca1063.md) | 모든 IDisposable 형식은 Dispose 패턴을 올바르게 구현해야 합니다. |
| CA1064 | [CA1064: 예외는 public이어야 합니다.](../code-quality/ca1064.md) | 내부 예외는 내부 범위 내에만 표시됩니다. 예외가 내부 범위 밖에 놓이게 되면 예외를 catch하는 데 기본 예외만 사용할 수 있습니다. 내부 예외에서 상속 되 면 <xref:System.Exception>, <xref:System.SystemException>, 또는 <xref:System.ApplicationException>, 외부 코드에 예외를 사용 하 여 수행할 작업을 알고에 충분 한 정보가 없습니다. |
| CA1065 | [CA1065: 예기치 않은 위치에서 예외를 발생시키지 마십시오.](../code-quality/ca1065.md) | 예외를 throw하지 않아야 하는 메서드가 예외를 throw했습니다. |
| CA1066 | [CA1066: Equals를 재정의할 때 IEquatable을 구현하세요.](../code-quality/ca1066.md) | 값 형식은 <xref:System.Object.Equals%2A> 메서드를 재정의 하지만는 구현 하지 않습니다 <xref:System.IEquatable%601> . |
| CA1067 | [CA1067: IEquatable을 구현할 때 Equals를 재정의하세요.](../code-quality/ca1067.md) | 형식은를 구현 <xref:System.IEquatable%601> 하지만 메서드를 재정의 하지 않습니다 <xref:System.Object.Equals%2A> . |
| CA1068 | [CA1068: CancellationToken 매개 변수는 마지막에 위치해야 합니다.](../code-quality/ca1068.md) | 메서드에 마지막 매개 변수가 아닌 CancellationToken 매개 변수가 있습니다. |
| CA1069 | [CA1069: 열거형에 중복 값이 없어야 합니다.](../code-quality/ca1069.md) | 열거형에는 동일한 상수 값을 명시적으로 할당 하는 여러 멤버가 있습니다. |
| CA1070 | [CA1070: 이벤트 필드를 가상으로 선언하지 마세요.](../code-quality/ca1070.md) | [필드와 유사한 이벤트가](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) 가상으로 선언 되었습니다. |
| CA1200 | [CA1200: 접두사를 사용하여 cref 태그 사용 방지](../code-quality/ca1200.md) | XML 문서 태그의 [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) 특성은 "코드 참조"를 의미 합니다. 태그의 내부 텍스트를 형식, 메서드, 속성 등의 코드 요소로 지정합니다. `cref`컴파일러가 참조를 확인 하는 것을 방지 하므로 접두사와 함께 태그를 사용 하지 마십시오. 또한 Visual Studio IDE (통합 개발 환경)에서 리팩터링 중에 이러한 기호 참조를 찾아 업데이트할 수 없습니다. |
| CA1300 | [CA1300: MessageBoxOptions를 지정하세요.](../code-quality/ca1300.md) | 오른쪽에서 왼쪽으로 읽기 순서를 사용하는 문화권에 대해 메시지 상자를 올바로 표시하려면 MessageBoxOptions 열거형의 RightAlign 및 RtlReading 멤버를 Show 메서드로 전달해야 합니다. |
| CA1301 | [CA1301: 중복 액셀러레이터 키를 사용하지 마십시오.](../code-quality/ca1301.md) | 액셀러레이터 키라고도 하는 선택키를 사용하면 Alt 키를 사용하여 키보드로 컨트롤에 액세스할 수 있습니다. 여러 컨트롤에 중복 된 액세스 키가 있는 경우에는 액세스 키의 동작이 제대로 정의 되지 않습니다. |
| CA1302 | [CA1302: 로캘별 문자열을 하드코드하지 마세요.](../code-quality/ca1302.md) | System.Environment.SpecialFolder 열거형에는 특수 시스템 폴더를 참조하는 멤버가 포함되어 있습니다. 이러한 폴더의 위치는 운영 체제에 따라 값이 다를 수 있으며, 사용자가 위치 일부를 변경할 수 있고, 위치는 지역화됩니다. Environment.GetFolderPath 메서드는 Environment.SpecialFolder 열거형과 연관된 위치를 반환하며 이 위치는 지역화되므로 현재 실행되고 있는 컴퓨터에 적합합니다. |
| CA1303 | [CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.](../code-quality/ca1303.md) | 외부에서 볼 수 있는 메서드는 문자열 리터럴을 .NET 생성자 또는 메서드에 대 한 매개 변수로 전달 하 고 해당 문자열을 지역화할 수 있어야 합니다. |
| CA1304 | [CA1304: CultureInfo를 지정하세요.](../code-quality/ca1304.md) | 메서드 또는 생성자가 System.Globalization.CultureInfo 매개 변수를 받아들이는 오버로드가 있는 멤버를 호출하지만 CultureInfo 매개 변수를 사용하는 오버로드는 호출하지 않습니다. CultureInfo 또는 System.IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다. |
| CA1305 | [CA1305: IFormatProvider를 지정하세요.](../code-quality/ca1305.md) | 메서드 또는 생성자가 System.IFormatProvider 매개 변수를 받아들이는 오버로드가 있는 하나 이상의 멤버를 호출하지만 IFormatProvider 매개 변수를 사용하는 오버로드는 호출하지 않습니다. System.Globalization.CultureInfo 또는 IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다. |
| CA1306 | [CA1306: 데이터 형식에 맞는 로캘을 설정하세요.](../code-quality/ca1306.md) | 로캘은 숫자 값에 사용되는 서식, 통화 기호 및 정렬 순서 등과 같은 데이터의 문화권별 표현 요소를 결정합니다. DataTable 또는 DataSet를 만들 때는 로캘을 명시적으로 설정해야 합니다. |
| CA1307 | [CA1307: StringComparison 지정하세요.](../code-quality/ca1307.md) | 문자열 비교 작업에서 StringComparison 매개 변수를 설정하지 않는 메서드 오버로드를 사용합니다. |
| CA1308 |[CA1308: 대문자로 문자열을 정규화하세요.](../code-quality/ca1308.md) | 문자열은 대문자로 정규화되어야 합니다. 일부 문자는 소문자로 변환될 때 다시 대문자로 변환될 수 없습니다. |
| CA1309 | [CA1309: 서수 StringComparison을 사용하세요.](../code-quality/ca1309.md) | 비언어 문자열 비교 작업에서는 StringComparison 매개 변수를 Ordinal 또는 OrdinalIgnoreCase로 설정하지 않습니다. 매개 변수가 명시적으로 StringComparison.Ordinal 또는 StringComparison.OrdinalIgnoreCase로 설정되기 때문에 코드 실행 속도, 정확도 및 신뢰도가 향상됩니다. |
| CA1400 | [CA1400: P/Invoke 진입점이 있어야 합니다.](../code-quality/ca1400.md) |public 또는 protected 메서드는 System.Runtime.InteropServices.DllImportAttribute 특성으로 표시됩니다. 관리되지 않는 라이브러리를 찾을 수 없거나 해당 메서드와 라이브러리의 함수가 일치하지 않습니다. |
| CA1401 | [CA1401: P/Invoke는 노출 되지 않아야 합니다.](../code-quality/ca1401.md) | public 형식의 public 또는 protected 메서드는 System.Runtime.InteropServices.DllImportAttribute 특성을 가지며 또한 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]에서 Declare 키워드로 구현됩니다. 이러한 메서드는 노출되지 않아야 합니다. |
| CA1402 |[CA1402: COM 노출 인터페이스에서 오버로드를 사용하지 마세요.](../code-quality/ca1402.md) | 오버로드된 메서드가 COM 클라이언트에 노출되면 첫 번째 메서드 오버로드만 이름이 유지됩니다. 이후의 오버로드는 이름에 밑줄 문자(_)와 오버로드 선언 순서에 해당하는 정수가 추가되어 고유한 이름이 지정됩니다. |
| CA1403 | [CA1403: 자동 레이아웃 형식은 COM 노출이면 안 됩니다.](../code-quality/ca1403.md) | COM 노출 값 형식은 Layoutkind.explicit로 설정 된 T e m. StructLayoutAttribute 특성을 사용 하 여 표시 됩니다. 이러한 형식의 레이아웃은 .NET 버전 간에 변경 될 수 있으므로 특정 레이아웃이 요구 되는 COM 클라이언트는 중단 됩니다. |
| CA1404 | [CA1404: P/Invoke 직후에 GetLastError를 호출 합니다.](../code-quality/ca1404.md) | Marshal.GetLastWin32Error 메서드 또는 해당 호출 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError 함수를 하 고 즉시 이전 호출은 운영 체제 아닌 메서드를 호출 합니다. |
| CA1405 | [CA1405: COM 노출 형식의 기본 형식은 COM 노출이어야 합니다.](../code-quality/ca1405.md) | COM 노출 형식이 COM에 노출되지 않는 형식에서 파생됩니다. |
| CA1406 |[CA1406: Visual Basic 6 클라이언트에서는 Int64 인수를 사용하지 마세요.](../code-quality/ca1406.md) | Visual Basic 6 COM 클라이언트는 64 비트 정수를 액세스할 수 없습니다. |
| CA1407 |[CA1407: COM 노출 형식에 정적 멤버를 사용하지 마세요.](../code-quality/ca1407.md) | COM에서는 static 메서드를 지원하지 않습니다. |
| CA1408 | [CA1408: AutoDual ClassInterfaceType을 사용하지 마세요.](../code-quality/ca1408.md) | 이중 인터페이스를 사용하는 형식에서는 클라이언트가 특정 인터페이스 레이아웃에 바인딩할 수 있습니다. 이후 버전에서 해당 형식이나 기본 형식의 레이아웃이 변경되면 인터페이스에 바인딩된 COM 클라이언트의 바인딩이 해제될 수 있습니다. 기본적으로 ClassInterfaceAttribute 특성이 지정되어 있지 않으면 디스패치 전용 인터페이스가 사용됩니다. |
| CA1409 | [CA1409: Com 노출 형식을 만들 수 있어야 합니다.](../code-quality/ca1409.md) |COM에 표시되는 것으로 특별히 표시된 참조 형식에 매개 변수가 있는 public 생성자가 있지만 매개 변수가 없는 public 기본 생성자가 없습니다. COM 클라이언트에서는 public 기본 생성자가 없는 형식을 만들 수 없습니다. |
| CA1410 | [CA1410: COM 등록 메서드는 일치해야 합니다.](../code-quality/ca1410.md) | 형식이 System.Runtime.InteropServices.ComRegisterFunctionAttribute 특성으로 표시된 메서드를 선언하지만 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 특성으로 표시된 메서드는 선언하지 않거나 그 반대의 경우입니다. |
| CA1411 | [CA1411: COM 등록 메서드는 노출되면 안 됩니다.](../code-quality/ca1411.md) | System.Runtime.InteropServices.ComRegisterFunctionAttribute 특성 또는 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 특성으로 표시된 메서드가 외부에 노출됩니다. |
| CA1412 | [CA1412: ComSource 인터페이스를 IDispatch로 표시하세요.](../code-quality/ca1412.md) | 형식이 System.Runtime.InteropServices.ComSourceInterfacesAttribute 특성으로 표시되어 있으며 지정된 인터페이스 중 하나 이상이 ComInterfaceType.InterfaceIsIDispatch로 설정된 System.Runtime.InteropServices.InterfaceTypeAttribute 특성으로 표시되어 있지 않습니다. |
| CA1413 | [CA1413: COM 노출 값 형식에 public이 아닌 필드를 사용하지 마세요.](../code-quality/ca1413.md) | public이 아니며 값 형식이 COM에 노출되는 인스턴스 필드는 COM 클라이언트에서 볼 수 있습니다. 필드의 내용을 검토하여 노출되지 않아야 하거나 디자인 또는 보안에 의도하지 않은 영향을 줄 수 있는 정보가 있는지 확인합니다. |
| CA1414 | [CA1414: 부울 P/Invoke 인수를 MarshalAs로 표시 합니다.](../code-quality/ca1414.md) | 부울 데이터 형식은 비관리 코드에서 여러 가지로 표현됩니다. |
| CA1415 | [CA1415: P/Invoke를 올바르게 선언 하십시오.](../code-quality/ca1415.md) | 이 규칙에서는 OVERLAPPED 구조체 매개 변수에 대한 포인터가 있는 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 함수를 대상으로 하는 운영 체제 호출 메서드 선언을 찾는데 관리되는 해당 매개 변수가 System.Threading.NativeOverlapped 구조체에 대한 포인터가 아닙니다. |
| CA1417 | [CA1417: `OutAttribute` P/invoke에 문자열 매개 변수를 사용 하지 마십시오.](../code-quality/ca1417.md) | 로 값으로 전달 되는 문자열 매개 변수는 `OutAttribute` 문자열이 인턴 문자열이 면 런타임을 불안정 하 게 만들 수 있습니다. |
| CA1500 | [CA1500: 변수 이름은 필드 이름과 달라야 합니다.](../code-quality/ca1500.md) | 인스턴스 메서드에서 선언 형식의 인스턴스 필드와 이름이 같은 매개 변수나 지역 변수를 선언합니다. 이로 인해 오류가 발생합니다. |
| CA1501 | [CA1501: 상속성을 너무 많이 사용하지 마세요.](../code-quality/ca1501.md) | 형식이 상속 계층 구조에서 네 단계보다 아래에 있습니다. 여러 번 중첩된 형식 계층 구조는 추적하고, 이해하고, 유지 관리하기가 어렵습니다. |
| CA1502 | [CA1502: 지나치게 복잡하게 만들지 마세요.](../code-quality/ca1502.md) | 이 규칙은 메서드를 통과하는 선형 독립 경로의 수를 측정하며 조건부 분기의 수와 복잡성에 의해 결정됩니다. |
| CA1504 | [CA1504: 잘못된 필드 이름을 검토하세요.](../code-quality/ca1504.md) | 인스턴스 필드의 이름이 "s_"로 시작 하거나 정적 (Visual Basic에서는 Shared) 필드의 이름이 "m_"로 시작 합니다. |
| CA1505 | [CA1505: 유지 관리할 수 없는 코드를 사용하지 마세요.](../code-quality/ca1505.md) | 형식 또는 메서드에 낮은 유지 관리 인덱스 값이 있습니다. 낮은 유지 관리 인덱스는 형식 또는 메서드가 유지 관리하기 어렵고 다시 디자인될 수 있음을 나타냅니다. |
| CA1506 | [CA1506: 클래스를 지나치게 많이 결합하지 마세요.](../code-quality/ca1506.md) | 이 규칙은 형식 또는 메서드에 들어 있는 고유한 형식 참조의 개수를 계산하여 클래스 결합을 측정합니다. |
| CA1507 | [CA1507: 문자열 대신 nameof 사용](../code-quality/ca1507.md) | 문자열 리터럴은 식을 사용할 수 있는 인수로 사용 됩니다 `nameof` . |
| CA1508 | [CA1508: 데드 조건부 코드 방지](../code-quality/ca1508.md) | 메서드에는 항상 `true` 또는 런타임 시로 계산 되는 조건부 코드가 있습니다 `false` . 이렇게 하면 조건의 분기에서 데드 코드가 발생 `false` 합니다. |
| CA1509 | [CA1509: 코드 메트릭 구성 파일의 잘못된 항목](../code-quality/ca1509.md) | [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) 및 [CA1506](ca1506.md)와 같은 코드 메트릭 규칙에서 `CodeMetricsConfig.txt` 잘못 된 항목을 포함 하는 이라는 구성 파일을 제공 했습니다. |
| CA1600 | [CA1600: 유휴 프로세스 우선 순위를 사용하지 마세요.](../code-quality/ca1600.md) | 프로세스 우선 순위를 유휴 상태로 설정하지 마십시오. System.Diagnostics.ProcessPriorityClass.Idle인 프로세스는 어떠한 이유로든 유휴 상태가 될 경우 CPU를 차지하므로 블록이 대기 모드가 됩니다. |
| CA1601 | [CA1601: 전원 상태 변경을 방해하는 타이머를 사용하지 마세요.](../code-quality/ca1601.md) | 정기적인 작업의 실행 빈도가 높아지면 CPU 사용률도 높아져 디스플레이 및 하드 디스크를 끄는 절전 유휴 타이머에 방해가 됩니다. |
| CA1700 | [CA1700: 열거형 값의 이름을 'Reserved'로 지정하지 마세요.](../code-quality/ca1700.md) | 이 규칙에서는 "reserved"라는 단어가 포함된 이름을 갖는 열거형 멤버가 현재 사용되지는 않지만 이후 버전에서 이름이 바뀌거나 제거될 자리 표시자라고 가정합니다. 멤버의 이름을 바꾸거나 멤버를 제거하는 것은 주요 변경에 해당합니다. |
| CA1701 | [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701.md) | 리소스 문자열의 각 단어는 대/소문자에 따라 토큰으로 구분됩니다. Microsoft 맞춤법 검사 라이브러리에서는 연속된 각 두 토큰의 조합을 검사합니다. 규칙 위반이 인식되면 단어에서 규칙 위반을 작성합니다. |
| CA1702 | [CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1702.md) | 식별자 이름에 여러 개의 단어가 포함되어 있으며 이 중 적어도 하나의 단어가 대/소문자를 정확하게 사용하지 않은 복합 단어인 것 같습니다. |
| CA1703 | [CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1703.md) | 리소스 문자열에 Microsoft 맞춤법 검사 라이브러리에서 인식하지 못하는 단어가 하나 이상 있습니다. |
| CA1704 | [CA1704: 식별자에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1704.md) | 외부에서 볼 수 있는 식별자의 이름에 Microsoft 맞춤법 검사 라이브러리에서 인식하지 못하는 단어가 하나 이상 있습니다. |
| CA1707 | [CA1707: 식별자에는 밑줄을 사용할 수 없습니다.](../code-quality/ca1707.md) | 규칙에 따라 식별자 이름에는 밑줄 문자(_)가 포함될 수 없습니다. 이 규칙에서는 네임스페이스, 형식, 멤버 및 매개 변수를 검사합니다. |
| CA1708 | [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708.md) | 공용 언어 런타임을 대상으로 하는 언어는 대/소문자를 구분하지 않으므로 네임스페이스, 형식, 멤버 및 매개 변수의 식별자가 대/소문자만 달라서는 안 됩니다. |
| CA1709 | [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709.md) | 규칙에 따라 매개 변수 이름에는 카멜식 대/소문자 구분을 사용하고 네임스페이스, 형식 및 멤버 이름에는 파스칼식 대/소문자 구분을 사용합니다. |
| CA1710 | [CA1710: 식별자에는 올바른 접미사를 사용해야 합니다.](../code-quality/ca1710.md) |규칙에 따라 특정 기본 형식을 확장하거나 특정 인터페이스를 구현하는 형식 또는 이러한 형식에서 파생되는 형식은 이름에 기본 형식이나 인터페이스와 연관된 접미사를 갖습니다. |
| CA1711 | [CA1711: 식별자에는 올바른 접미사를 사용해야 합니다.](../code-quality/ca1711.md) | 규칙에 따라 특정 기본 형식을 확장하거나 특정 인터페이스를 구현하는 형식의 이름 또는 이러한 형식에서 파생되는 형식의 이름만이 예약된 특정 접미사로 끝나야 합니다. 다른 형식 이름에는 이러한 예약된 접미사를 사용하면 안 됩니다. |
| CA1712 | [CA1712: 열거형 값에 형식 이름을 접두사로 사용하지 마세요.](../code-quality/ca1712.md) | 개발 도구에서 형식 정보를 제공하므로 열거형 멤버의 이름에는 형식 이름을 접두사로 사용하지 않습니다. |
| CA1713 | [CA1713: 이벤트에 Before 또는 After 접두사를 사용하지 마세요.](../code-quality/ca1713.md) | 이벤트 이름이 "Before" 또는 "After"로 시작합니다. 특정 시퀀스에서 발생하는 관련 이벤트의 이름을 지정하려면 현재 또는 과거 시제를 사용하여 동작 시퀀스 내의 상대적인 위치를 나타냅니다. |
| CA1714 | [CA1714: 플래그 열거형에는 복수형 이름을 사용해야 합니다.](../code-quality/ca1714.md) | public 열거형에 System.FlagsAttribute 특성이 있고 이름이 "s"로 끝나지 않았습니다. FlagsAttribute 특성은 둘 이상의 값을 지정할 수 있음을 나타내므로 이 특성으로 표시된 형식은 복수형 이름을 갖습니다. |
| CA1715 | [CA1715: 식별자에는 올바른 접두사를 사용해야 합니다.](../code-quality/ca1715.md) | 외부에 노출되는 인터페이스의 이름이 대문자 "I"로 시작하지 않습니다. 외부에 노출되는 형식 또는 메서드의 제네릭 형식 매개 변수 이름이 대문자 "T"로 시작하지 않습니다. |
| CA1716 | [CA1716: 식별자는 키워드와 달라야 합니다.](../code-quality/ca1716.md) | 네임스페이스 이름 또는 형식 이름이 프로그래밍 언어의 예약된 키워드와 일치합니다. 네임스페이스 및 형식에 대한 식별자는 공용 언어 런타임을 대상으로 하는 언어에서 정의된 키워드와 일치하면 안 됩니다. |
| CA1717 | [CA1717: FlagsAttribute 열거형만 복수형 이름을 가질 수 있습니다.](../code-quality/ca1717.md) | 명명 규칙은 열거형 이름이 복수형인 경우 여러 열거 값을 동시에 지정할 수 있음을 나타내도록 되어 있습니다. |
| CA1719 | [CA1719: 매개 변수 이름은 멤버 이름과 달라야 합니다.](../code-quality/ca1719.md) | 매개 변수 이름은 매개 변수의 의미를 나타내고 멤버 이름은 멤버의 의미를 나타내야 합니다. 매개 변수와 멤버의 의미가 같게 디자인되는 경우는 드뭅니다. 매개 변수의 이름을 멤버 이름과 동일하게 지정하는 것은 비직관적이고 라이브러리 사용을 어렵게 만듭니다. |
| CA1720 |[CA1720: 식별자에 형식 이름을 포함하면 안 됩니다.](../code-quality/ca1720.md) | 외부에 노출되는 멤버의 매개 변수 이름에 데이터 형식 이름이 포함되어 있거나 외부에 노출되는 멤버의 이름에 언어에 따라 다른 데이터 형식 이름이 포함되어 있습니다. |
| CA1721 | [CA1721: 속성 이름은 Get 메서드와 달라야 합니다.](../code-quality/ca1721.md) |public 또는 protected 멤버의 이름이 "Get"으로 시작하며 이름의 나머지 부분이 public 또는 protected 속성의 이름과 같습니다. "Get" 메서드와 속성은 서로가 분명히 구분되는 이름을 사용해야 합니다. |
| CA1722 | [CA1722: 식별자에는 올바른 접두사를 사용해야 합니다.](../code-quality/ca1722.md) | 규칙에 따라 특정 프로그래밍 요소에만 특정 접두사로 시작하는 이름을 사용할 수 있습니다. |
| CA1724 | [CA1724: 형식 이름은 네임스페이스와 달라야 합니다.](../code-quality/ca1724.md) | 형식 이름은 .NET 네임 스페이스의 이름과 일치 하면 안 됩니다. 이 규칙을 위반하면 라이브러리의 유용성이 저하될 수 있습니다. |
| CA1725 | [CA1725: 매개 변수 이름은 기본 선언과 일치해야 합니다.](../code-quality/ca1725.md) | 재정의 계층 구조에서 매개 변수 이름을 일관되게 지정하면 메서드 재정의를 더 편리하게 사용할 수 있습니다. 파생된 메서드의 매개 변수 이름이 기본 선언의 이름과 다르면 메서드가 기본 메서드의 재정의인지 메서드의 새 오버로드인지를 혼동할 수 있습니다. |
| CA1726 | [CA1726: 기본 설정 용어를 사용하세요.](../code-quality/ca1726.md) | 외부에서 볼 수 있는 식별자의 이름에 특정 용어가 포함되어 있는데, 이 용어에는 기본 설정된 대체 용어가 있습니다. 또는 이름에 "Flag"나 "Flags"라는 용어가 포함되어 있습니다. |
| CA1800 | [CA1800: 불필요하게 캐스트하지 마세요.](../code-quality/ca1800.md) | 중복 캐스팅을 수행하면 성능이 저하됩니다. 특히 간단한 반복 문에서 캐스팅이 수행될 때 더욱 그러합니다. |
| CA1801 | [CA1801: 사용되지 않은 매개 변수를 검토하세요.](../code-quality/ca1801.md) | 메서드 시그니처에 메서드 본문에서 사용되지 않는 매개 변수가 있습니다. |
| CA1802 |[CA1802: 가능하면 리터럴을 사용하세요.](../code-quality/ca1802.md) |필드가 static 및 read-only([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]의 경우 Shared 및 ReadOnly)로 선언되었으며 컴파일할 때 계산할 수 있는 값으로 초기화되어 있습니다. 컴파일 시간에 대상된 필드에 할당 되는 값을 계산할 이기 때문에 const 선언을 변경 (에서 Const [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 필드 값을 런타임 대신 컴파일 시간에 계산 되도록 합니다. |
| CA1804 | [CA1804: 사용되지 않는 로컬 항목을 제거하세요.](../code-quality/ca1804.md) | 사용되지 않는 지역 변수와 불필요한 할당으로 어셈블리의 크기가 증가하고 성능이 저하될 수 있습니다. |
| CA1805 | [CA1805: 불필요하게 초기화하지 마세요.](../code-quality/ca1805.md) | .NET 런타임은 생성자를 실행 하기 전에 참조 형식의 모든 필드를 기본값으로 초기화 합니다. 대부분의 경우 필드를 기본값으로 명시적으로 초기화 하면 유지 관리 비용이 증가 하 고 성능이 저하 될 수 있습니다 (예: 어셈블리 크기 증가). |
| CA1806 | [CA1806: 메서드 결과를 무시하지 마세요.](../code-quality/ca1806.md) | 새 개체가 만들어지지만 사용되지 않거나, 새 문자열을 만들고 반환하는 메서드가 호출되고 새 문자열이 사용되지 않거나, COM 또는 P/Invoke 메서드가 사용되지 않는 오류 코드나 HRESULT를 반환합니다. |
| CA1809 |[CA1809: 불필요한 로컬 항목을 사용하지 마세요.](../code-quality/ca1809.md) | 값을 메모리가 아닌 프로세서 레지스터에 저장하는 방법은 성능 최적화에 많이 사용되는 방법이며 "값의 레지스터 등록"이라고도 합니다. 모든 지역 변수에 레지스터는 가능성을 늘리려면 64 로컬 변수 수를 제한 합니다. |
| CA1810 | [CA1810: 참조 형식 정적 필드를 인라인으로 초기화하세요.](../code-quality/ca1810.md) | 형식이 명시적인 정적 생성자를 선언하면 JIT(Just-in-Time) 컴파일러는 형식의 각 정적 메서드와 인스턴스 생성자에 검사를 추가하여 정적 생성자를 이전에 호출했는지 확인합니다. 정적 생성자 검사로 인해 성능이 저하될 수 있습니다. |
| CA1811 | [CA1811: 호출되지 않는 전용 코드를 사용하지 마세요.](../code-quality/ca1811.md) | 어셈블리에 private 또는 internal(어셈블리 수준) 멤버의 호출자가 없고, 공용 언어 런타임에서도 이 멤버를 호출하지 않으며, 대리자에서도 이 멤버를 호출하지 않습니다. |
| CA1812 | [CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.](../code-quality/ca1812.md) | 어셈블리 수준 형식의 인스턴스가 어셈블리에서 코드에 의해 만들어지지 않습니다. |
| CA1813 | [CA1813: 봉인되지 않은 특성을 사용하지 마세요.](../code-quality/ca1813.md) | .NET에서는 사용자 지정 특성을 검색 하는 메서드를 제공 합니다. 기본적으로 이러한 메서드는 특성 상속 계층을 검색합니다. 특성을 봉인하면 상속 계층을 검색하지 않으므로 성능이 향상될 수 있습니다. |
| CA1814 | [CA1814: 다차원 배열보다 가변 배열을 사용하세요.](../code-quality/ca1814.md) | 가변 배열의 요소에는 배열이 사용됩니다. 요소를 구성하는 배열의 크기는 서로 다를 수 있습니다. 이 경우 일부 데이터 집합에 대한 공간을 절약할 수 있습니다. |
| CA1815 | [CA1815: 값 형식에서 Equals 또는 같음 연산자를 재정의하세요.](../code-quality/ca1815.md) | 값 형식의 경우 Equals의 상속된 구현에서 Reflection 라이브러리를 사용하며 모든 필드의 내용을 비교합니다. Reflection에는 많은 계산이 요구되며 모든 필드의 일치 여부를 비교하는 것이 불필요할 수 있습니다. 사용자가 인스턴스를 비교 또는 정렬하거나 인스턴스를 해시 테이블 키로 사용할 것으로 예측되는 경우에는 값 형식에서 Equals를 구현해야 합니다. |
| CA1816 | [CA1816: GC.SuppressFinalize를 올바르게 호출하세요.](../code-quality/ca1816.md) | Dispose 구현인 메서드가 GC를 호출 하지 않습니다. SuppressFinalize; 또는 Dispose 구현 되지 않는 메서드가 GC를 호출 합니다. SuppressFinalize; 또는 GC를 호출 합니다. SuppressFinalize 및 전달이 (Visual Basic의 Me) 이외의 것입니다. |
| CA1819 | [CA1819: 속성은 배열을 반환해서는 안 됩니다.](../code-quality/ca1819.md) | 속성에서 반환된 배열은 속성이 읽기 전용이더라도 쓰기 금지되지 않습니다. 배열을 무단으로 변경하지 못하도록 하려면 속성에서 배열의 복사본을 반환해야 합니다. 일반적으로 사용자는 이러한 속성을 호출할 경우 성능에 부정적인 영향을 준다는 것을 인식하지 못합니다. |
| CA1820 | [CA1820: 문자열 길이를 사용하여 빈 문자열을 테스트하세요.](../code-quality/ca1820.md) | String.Length 속성이나 String.IsNullOrEmpty 메서드를 사용하여 문자열을 비교하는 것이 Equals를 사용하는 것보다 훨씬 더 빠릅니다. |
| CA1821 | [CA1821: 빈 종료자를 제거하십시오.](../code-quality/ca1821.md) | 개체 수명을 추적할 때에는 추가로 성능 오버헤드가 발생하므로 가능한 경우 종료자를 사용하지 마십시오. 빈 종료자는 아무런 장점 없이 오버헤드만 가중시킵니다. |
| CA1822 |[CA1822: 멤버를 static으로 표시하세요.](../code-quality/ca1822.md) | 인스턴스 데이터에 액세스하지 않거나 인스턴스 메서드를 호출하지 않는 멤버는 static([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]의 경우 Shared)으로 표시할 수 있습니다. 메서드를 static으로 표시하면 컴파일러는 이러한 멤버에 대한 비가상 호출 사이트를 내보냅니다. 이 경우 성능이 중요한 코드에서 성능이 크게 향상될 수 있습니다. |
| CA1823 | [CA1823: 사용되지 않는 전용 필드를 사용하지 마세요.](../code-quality/ca1823.md) | 어셈블리에서 액세스되지 않는 것으로 보이는 전용 필드가 발견되었습니다. |
| CA1824 |[CA1824: NeutralResourcesLanguageAttribute로 어셈블리를 표시하세요.](../code-quality/ca1824.md) | NeutralResourcesLanguage 특성은 어셈블리에 대 한 중립 문화권의 리소스를 표시 하는 데 사용 된 언어를 리소스 관리자에 게 알립니다. 이렇게 하면 로드한 첫 리소스에 대한 찾기 성능을 향상시킬 수 있으며 작업이 간단해집니다. |
| CA1825 |[CA1825: 길이가 0인 배열 할당 방지](../code-quality/ca1825.md) | 길이가 0 인 배열을 초기화 하면 불필요 한 메모리 할당이 발생 합니다. 대신를 호출 하 여 정적으로 할당 된 빈 배열 인스턴스를 사용 합니다 <xref:System.Array.Empty%2A?displayProperty=nameWithType> . 메모리 할당은이 메서드의 모든 호출에서 공유 됩니다. |
| CA1826 |[CA1826: Linq Enumerable 메서드 대신 속성을 사용하세요.](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> LINQ 메서드는 보다 효율적인 동등한 속성을 지 원하는 형식에서 사용 되었습니다. |
| CA1827 |[CA1827: Any를 사용할 수 있는 경우 Count/LongCount를 사용하지 마세요.](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> 또는 메서드가 <xref:System.Linq.Enumerable.LongCount%2A> 더 효율적으로 사용 되었습니다 <xref:System.Linq.Enumerable.Any%2A> . |
| CA1828 |[CA1828: AnyAsync를 사용할 수 있는 경우 CountAsync/LongCountAsync를 사용하지 마세요.](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> 또는 메서드가 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> 더 효율적으로 사용 되었습니다 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> . |
| CA1829 |[CA1829: Enumerable.Count 메서드 대신 Length/Count 속성을 사용하세요.](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> LINQ 메서드가 동등한, 보다 효율적인 또는 속성을 지 원하는 형식에서 사용 `Length` 되었습니다 `Count` . |
| CA1830 |[CA1830: StringBuilder에서 강력한 형식의 추가 및 삽입 메서드 오버로드를 사용하세요.](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> 및 <xref:System.Text.StringBuilder.Insert%2A> 는 이외의 여러 형식에 대 한 오버 로드를 제공 <xref:System.String> 합니다.  가능 하면 ToString () 및 문자열 기반 오버 로드를 사용 하는 것 보다 강력한 형식의 오버 로드를 사용 하는 것이 좋습니다. |
| CA1831 |[CA1831: 적절한 경우 문자열에 대해 범위 기반 인덱서 대신 AsSpan을 사용하세요.](../code-quality/ca1831.md) | 문자열에 범위 인덱서를 사용 하 고 해당 값을 ReadOnlySpan char 형식에 암시적으로 할당 하는 경우 &lt; &gt; 이 메서드는 <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> 문자열의 요청 된 부분 복사본을 생성 하는 대신 사용 됩니다. |
| CA1832 |[CA1832: 배열의 ReadOnlySpan 또는 ReadOnlyMemory 부분을 가져오려면 범위 기반 인덱서 대신 AsSpan 또는 AsMemory를 사용하세요.](../code-quality/ca1832.md) | 배열에 범위-인덱서를 사용 하 고 또는 형식에 값을 암시적으로 할당 하는 경우 <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> 이 메서드는 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 배열에서 요청 된 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> 부분의 복사본을 생성 하는 대신 사용 됩니다. |
| CA1833 |[CA1833: 배열의 Span 또는 Memory 부분을 가져오려면 범위 기반 인덱서 대신 AsSpan 또는 AsMemory를 사용하세요.](../code-quality/ca1833.md) | 배열에 범위-인덱서를 사용 하 고 또는 형식에 값을 암시적으로 할당 하는 경우 <xref:System.Span%601> <xref:System.Memory%601> 이 메서드는 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 배열에서 요청 된 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> 부분의 복사본을 생성 하는 대신 사용 됩니다. |
| CA1835 |[CA1835: ' ReadAsync ' 및 ' WriteAsync '에 대해 ' Memory' 기반 오버 로드를 선호 합니다.](../code-quality/ca1835.md) | ' Stream '에는 첫 번째 인수로 ' Memory Byte '를 사용 하는 ' ReadAsync ' 오버 로드 &lt; &gt; 와 ' ReadOnlyMemory &lt; Byte &gt; '를 첫 번째 인수로 사용 하는 ' WriteAsync ' 오버 로드가 있습니다. 더 효율적인 메모리 기반 오버 로드를 호출 하는 것이 좋습니다. |
| CA1836 |[CA1836: `IsEmpty` `Count` 사용 가능한 경우 선호](../code-quality/ca1836.md) | `IsEmpty`, 또는 보다 효율적인 속성을 사용 `Count` `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 하 여 개체에 항목이 포함 되어 있는지 여부를 확인 하는 것이 좋습니다. |
| CA1838 | [CA1838: `StringBuilder` P/invoke에 대 한 매개 변수를 사용 하지 않습니다.](../code-quality/ca1838.md) | ' StringBuilder '를 마샬링하면 항상 네이티브 버퍼 복사본이 만들어지므로 하나의 마샬링 작업에 대해 여러 할당이 발생 합니다. |
| CA1900 | [CA1900: 값 형식 필드는 이식 가능해야 합니다.](../code-quality/ca1900.md) | 이 규칙에서는 명시적 레이아웃으로 선언된 구조체가 64비트 운영 체제에서 비관리 코드로 마샬링될 때 올바르게 맞춰지는지 검사합니다. |
| CA1901 | [CA1901: P/Invoke 선언은 이식 가능 해야 합니다.](../code-quality/ca1901.md) | 이 규칙은 P/Invoke의 반환 값과 각 매개 변수의 크기를 계산하여 32비트 및 64비트 운영 체제에서 비관리 코드로 마샬링될 때 해당 매개 변수의 크기가 올바른지 확인합니다. |
| CA1903 | [CA1903: 대상 프레임워크의 API만 사용하세요.](../code-quality/ca1903.md) | 멤버 또는 형식이 프로젝트의 대상 프레임워크에 함께 포함되지 않은 서비스 팩에 도입된 멤버 또는 형식을 사용합니다. |
| CA2000 | [CA2000: 범위를 벗어나기 전에 개체를 삭제하세요.](../code-quality/ca2000.md) | 개체의 종료자가 실행되지 못하도록 하는 예외 이벤트가 발생할 수 있기 때문에 개체에 대한 모든 참조가 범위를 벗어나기 전에 개체를 명시적으로 삭제해야 합니다. |
| CA2001 | [CA2001: 문제가 있는 메서드는 호출하지 마세요.](../code-quality/ca2001.md) | 멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다. |
| CA2002 |[CA2002: 약한 ID를 가진 개체를 잠그지 마십시오.](../code-quality/ca2002.md) |애플리케이션 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다. 약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 애플리케이션 도메인의 스레드에 의해 차단될 수 있습니다. |
| CA2003 |[CA2003: 파이버를 스레드로 취급하지 마세요.](../code-quality/ca2003.md) | 관리되는 스레드가 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 스레드처럼 취급됩니다. |
| CA2004 | [CA2004: GC.KeepAlive에 대한 호출을 제거하세요.](../code-quality/ca2004.md) | SafeHandle을 사용하는 방식으로 변환하는 경우 GC.KeepAlive(개체)에 대한 모든 호출을 제거해야 합니다. 이 경우 클래스에 종료자가 없지만 SafeHandle을 사용하여 OS 핸들을 종료하는 것으로 간주하므로 클래스에서 GC.KeepAlive를 호출할 필요가 없습니다. |
| CA2006 | [CA2006: SafeHandle을 사용하여 네이티브 리소스를 캡슐화하세요.](../code-quality/ca2006.md) | 관리 코드에 IntPtr을 사용하는 것은 잠재적인 보안 및 안정성 문제를 나타냅니다. IntPtr을 사용할 때마다 SafeHandle 또는 유사한 기술을 대신 사용해야 하는지 여부를 결정하도록 검토해야 합니다. |
| CA2007 | [CA2007: 작업을 직접 대기하지 마세요.](ca2007.md) | 비동기 메서드는를 직접 [기다립니다](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> 합니다. 비동기 메서드가 <xref:System.Threading.Tasks.Task> 직접 기다립니다 작업을 만든 스레드와 동일한 스레드에서 연속 작업을 수행 합니다. 이 동작은 성능 측면에서 비용이 많이 들 수 있으며 UI 스레드에 교착 상태가 발생할 수 있습니다. 을 호출 <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> 하 여 연속 작업을 위한 신호를 보내는 것이 좋습니다. |
| CA2009 | [CA2009: ImmutableCollection 값의 ToImmutableCollection을 호출하지 마세요.](ca2009.md) | `ToImmutable` 네임 스페이스의 변경할 수 없는 컬렉션에 대해 메서드를 불필요 하 게 호출 했습니다 <xref:System.Collections.Immutable> . |
| CA2011 | [CA2011: Setter 내에서 속성을 할당하지 마세요.](ca2011.md) | 속성에 해당 하는 자체 [set 접근자](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)내에 값이 실수로 할당 되었습니다. |
| CA2012 | [CA2012: ValueTasks를 올바르게 사용하세요.](ca2012.md) | 멤버 호출에서 반환 되는 ValueTasks는 직접 대기 합니다.  는 특정 기능을 여러 번 사용 하거나 완료 되기 전에 한 결과에 직접 액세스 하려고 시도 하 여 예외 또는 손상이 발생할 수 있습니다.  이러한 것을 무시 하면 기능적 버그를 나타낼 수 있으며 성능이 저하 될 수 있습니다. |
| CA2013 | [CA2013: 값 형식과 함께 ReferenceEquals를 사용하지 마세요.](ca2013.md) | 를 사용 하 여 값을 비교할 때 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> objA와 Obja가 값 형식이 면 메서드로 전달 되기 전에 boxing 됩니다 <xref:System.Object.ReferenceEquals%2A> . 즉, objA와 Obja가 모두 값 형식의 동일한 인스턴스를 나타내는 경우에도 <xref:System.Object.ReferenceEquals%2A> 메서드에서 false를 반환 합니다. |
| CA2014 | [CA2014: 루프에서 stackalloc을 사용 하지 마십시오.](ca2014.md) | Stackalloc에 의해 할당 된 스택 공간은 현재 메서드 호출의 끝 에서만 해제 됩니다.  루프에서이를 사용 하면 바인딩되지 않은 스택 증가 및 최종 스택 오버플로 조건이 발생할 수 있습니다. |
| CA2015 | [CA2015: MemoryManager T에서 파생 된 형식에 대 한 종료자를 정의 하지 않습니다. &lt;&gt;](ca2015.md) | 에서 파생 된 형식에 종료자를 추가 하면에서 <xref:System.Buffers.MemoryManager%601> 아직 사용 중인 메모리를 해제할 수 있습니다 <xref:System.Span%601> . |
| CA2016 | [CA2016: 인수 하나를 사용하는 메서드에 CancellationToken 매개 변수를 전달하세요.](ca2016.md) | `CancellationToken`매개 변수를 사용 하 여 작업 취소 알림이 제대로 전파 되는지 확인 하거나 `CancellationToken.None` 의도적으로 토큰을 전파 하지 않도록 명시적으로 전달 하는 메서드에 매개 변수를 전달 합니다. |
| CA2100 | [CA2100: 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.](../code-quality/ca2100.md) | 메서드가 메서드에 대한 문자열 인수로부터 만들어진 문자열을 사용하여 System.Data.IDbCommand.CommandText 속성을 설정합니다. 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다. |
| CA2101 |[CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101.md) | 플랫폼 호출 멤버가 부분 신뢰 호출자를 허용하고, 문자열 매개 변수를 사용하고, 문자열을 명시적으로 마샬링하지 않습니다. 이렇게 하면 보안상 위험할 수 있습니다. |
| CA2102 | [CA2102: 일반 처리기에서 비 CLSCompliant 예외를 catch하세요.](../code-quality/ca2102.md) | RuntimeCompatibilityAttribute로 표시되지 않거나 RuntimeCompatibility(WrapNonExceptionThrows = false)로 표시된 어셈블리의 멤버에는 System.Exception을 처리하는 catch 블록이 포함되며 바로 뒤의 일반 catch 블록은 포함되지 않습니다. |
| CA2103 | [CA2103: 명령적 보안을 검토하세요.](../code-quality/ca2103.md) |메서드가 명령적 보안을 사용하고, 요청이 활성 상태인 동안 변경될 수 있는 반환 값 또는 상태 정보를 사용하여 권한을 구성하고 있습니다. 가능하면 선언적 보안을 사용합니다. |
| CA2104 |[CA2104: 변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.](../code-quality/ca2104.md) | 외부에서 볼 수 있는 형식에 변경 가능한 참조 형식인, 외부에서 볼 수 있는 읽기 전용 필드가 포함되었습니다. 변경 가능한 형식은 해당 인스턴스 데이터를 수정할 수 있는 형식을 말합니다. |
| CA2105 | [CA2105: 배열 필드는 읽기 전용이면 안 됩니다.](../code-quality/ca2105.md) |배열이 들어 있는 필드에 read-only([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]의 경우 ReadOnly) 한정자를 적용하면 필드를 변경하여 다른 배열을 참조할 수 없습니다. 그러나 읽기 전용 필드에 저장된 배열의 요소는 변경할 수 있습니다. |
| CA2106 | [CA2106: 어설션을 안전하게 보호하세요.](../code-quality/ca2106.md) | 메서드에서 권한을 어설션하는데 호출자에 대해 보안 검사가 수행되지 않습니다. 보안 검사를 수행하지 않고 보안 권한을 어설션하면 코드에 보안상 취약한 부분이 남아 있을 수 있습니다. |
| CA2107 | [CA2107: deny 및 permit only 사용을 검토하세요.](../code-quality/ca2107.md) |PermitOnly 메서드 및 CodeAccessPermission. 보안 거부 동작은 .NET 보안에 대 한 고급 지식이 있는 사용자만 사용 해야 합니다. 이러한 보안 동작을 사용하는 코드는 보안 검토를 거쳐야 합니다. |
| CA2108 | [CA2108: 값 형식에서 선언적 보안을 검토하십시오.](../code-quality/ca2108.md) | public 또는 protected 값 형식이 데이터 액세스 또는 링크 요청에 의해 보안됩니다. |
| CA2109 | [CA2109: 표시되는 이벤트 처리기를 검토하세요.](../code-quality/ca2109.md) | public 또는 protected 이벤트 처리 메서드를 발견했습니다. 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다. |
| CA2111 |[CA2111: 포인터는 노출되면 안 됩니다.](../code-quality/ca2111.md) | 포인터가 전용, 내부 또는 읽기 전용이 아닙니다. 악의적인 코드에서 해당 포인터 값을 변경하여 메모리 내 임의의 위치에 액세스할 수 있게 되거나 애플리케이션 또는 시스템 오류를 발생시킬 수 있습니다. |
| CA2112 | [CA2112: 보안 형식은 필드를 노출하면 안 됩니다.](../code-quality/ca2112.md) | public 또는 protected 형식이 public 필드를 포함하고 링크 요청에 의해 보안됩니다. 코드에 링크 요청으로 보안된 형식의 인스턴스에 대한 액세스 권한이 있으면 코드에서 링크 요청을 만족하지 않아도 해당 형식의 필드에 액세스할 수 있습니다. |
| CA2114 | [CA2114: 메서드 보안은 형식의 상위 집합이어야 합니다.](../code-quality/ca2114.md) | 메서드에는 같은 동작에 대해 메서드 수준과 형식 수준의 선언적 보안이 모두 있으면 안 됩니다. |
| CA2115 | [CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.](../code-quality/ca2115.md) | 이 규칙에서는 관리되지 않는 리소스가 비관리 코드에서 여전히 사용되고 있는데 종료되려고 할 경우 발생할 수 있는 오류를 감지합니다. |
| CA2116 | [CA2116: APTCA 메서드는 APTCA 메서드만 호출해야 합니다.](../code-quality/ca2116.md) |완전히 신뢰할 수 있는 어셈블리에 APTCA(AllowPartiallyTrustedCallersAttribute) 특성이 있고 이 어셈블리가 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 다른 어셈블리의 코드를 실행하면 보안상 위험할 수 있습니다. |
| CA2117 | [CA2117: APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.](../code-quality/ca2117.md) | 완전히 신뢰할 수 있는 어셈블리에 APTCA가 있고 이 어셈블리의 형식이 부분적으로 신뢰할 수 있는 호출자를 허용하지 않는 형식에서 상속되면 보안상 위험할 수 있습니다. |
| CA2118 | [CA2118: SuppressUnmanagedCodeSecurityAttribute 사용을 검토하세요.](../code-quality/ca2118.md) |SuppressUnmanagedCodeSecurityAttribute는 COM interop 또는 운영 체제 호출을 사용하는 비관리 코드를 실행하는 멤버에 대해 기본 보안 시스템 동작을 변경합니다. 이 특성은 기본적으로 성능 향상을 위해 사용되지만 성능이 향상되는 대신 중대한 보안 위험이 발생합니다. |
| CA2119 | [CA2119: private 인터페이스를 만족하는 메서드를 봉인하세요.](../code-quality/ca2119.md) | 상속할 수 있는 public 형식에서는 internal([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]의 경우 Friend) 인터페이스의 재정의 가능한 메서드 구현을 제공합니다. 이 규칙 위반 문제를 해결하려면 어셈블리 외부에서 메서드가 재정의되지 않도록 합니다. |
| CA2120 | [CA2120: serialization 생성자를 안전하게 하세요.](../code-quality/ca2120.md) | 이 형식에는 System.Runtime.Serialization.SerializationInfo 개체와 System.Runtime.Serialization.StreamingContext 개체(serialization 생성자 서명)를 사용하는 생성자가 있습니다. 이 생성자는 보안 검사를 통해 보안되지 않지만 형식에 있는 하나 이상의 정규 생성자가 보안됩니다. |
| CA2121 | [CA2121: 정적 생성자는 private이어야 합니다.](../code-quality/ca2121.md) | 시스템에서는 형식의 첫 번째 인스턴스가 만들어지거나 static 멤버가 참조되기 전에 static 생성자를 호출합니다. static 생성자가 private이 아니면 시스템 이외의 코드에서 이를 호출할 수 있습니다. 이렇게 되면 생성자에서 수행하는 작업에 따라 예기치 않은 동작이 발생할 수 있습니다. |
| CA2122 | [CA2122: 링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.](../code-quality/ca2122.md) | public 또는 protected 멤버에 링크 요청이 있으며 해당 멤버가 보안 검사를 수행하지 않는 멤버에 의해 호출됩니다. 링크 요청은 직접 실행 호출자의 권한만 검사합니다. |
| CA2123 | [CA2123: 재정의 링크 요청은 기본 링크 요청과 같아야 합니다.](../code-quality/ca2123.md) | 이 규칙에서는 메서드를 다른 형식의 인터페이스이거나 가상 메서드인 기본 메서드에 일치시킨 다음 각각에 대해 링크 요청을 비교합니다. 이 규칙이 위반되면 악의적인 호출자가 보안되지 않은 메서드를 호출함으로써 링크 요청을 우회할 수 있습니다. |
| CA2124 | [CA2124: 취약한 finally 절을 외부 try에 래핑하십시오.](../code-quality/ca2124.md) | public 또는 protected 메서드에 try/finally 블록이 들어 있습니다. finally 블록이 보안 상태를 다시 설정하는 것으로 나타나며 finally 블록에 포함되어 있지 않습니다. |
| CA2126 | [CA2126: 형식 링크 요청에는 상속 요청이 필요합니다.](../code-quality/ca2126.md) | public unsealed 형식이 링크 요청으로 보호되며 재정의 가능한 메서드를 포함합니다. 형식이나 메서드는 모두 상속 요청으로 보호됩니다. |
| CA2130 | [CA2130: 보안에 중요한 상수는 투명해야 합니다.](../code-quality/ca2130.md) | 런타임에 조회가 필요하지 않도록 컴파일러에서 상수 값을 인라인하기 때문에 상수 값에 투명성이 적용되지 않습니다. 상수 필드는 보안 투명해야 하므로 코드 검토자는 투명 코드가 상수에 액세스할 수 없다고 가정하지 않습니다. |
| CA2131 | [CA2131: 보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.](../code-quality/ca2131.md) | 형식이 형식 동등에 참여하는데, 해당 형식 자체 또는 해당 형식의 멤버나 필드가 SecurityCriticalAttribute 특성을 사용하여 표시되어 있습니다. 이 규칙은 중요한 형식 또는 중요한 메서드나 필드를 포함하는 형식이 형식 동등에 참여하는 경우에 적용됩니다. CLR에서 이러한 형식이 검색되면 런타임에 해당 형식이 로드되지 않고 TypeLoadException이 throw됩니다. 일반적으로 이 규칙은 사용자가 tlbimp와 컴파일러를 이용하여 형식 동등을 수행하는 대신 수동으로 형식 동등을 구현하는 경우에만 적용됩니다. |
| CA2132 | [CA2132: 기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.](../code-quality/ca2132.md) |SecurityCriticalAttribute가 있는 형식 및 멤버는 Silverlight 애플리케이션 코드에서 사용할 수 없습니다. 보안에 중요한 형식 및 멤버는 .NET Framework for Silverlight 클래스 라이브러리의 신뢰할 수 있는 코드에서만 사용할 수 있습니다. 파생 클래스의 public 또는 protected 구성 요소는 투명성이 기본 클래스보다 높거나 같아야 하기 때문에 애플리케이션의 클래스는 SecurityCritical로 표시된 클래스에서 파생될 수 없습니다. |
| CA2133 | [CA2133: 대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.](../code-quality/ca2133.md) | 이 경고는 SecurityCriticalAttribute를 사용하여 표시된 대리자를 SecuritySafeCriticalAttribute를 사용하여 표시되거나 투명한 메서드에 바인딩하는 메서드에서 발생합니다. 또한 투명하거나 안전에 중요한 대리자를 중요한 메서드에 바인딩하는 메서드에서도 이 경고가 발생합니다. |
| CA2134 | [CA2134: 메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.](../code-quality/ca2134.md) |이 규칙은 SecurityCriticalAttribute를 사용하여 표시된 메서드가 SecuritySafeCriticalAttribute를 사용하여 표시되거나 투명한 메서드를 재정의할 때 적용됩니다. 또한 SecuritySafeCriticalAttribute를 사용하여 표시되거나 투명한 메서드가 SecurityCriticalAttribute를 사용하여 표시된 메서드를 재정의할 때도 이 규칙이 적용됩니다. 이 규칙은 가상 메서드를 재정의하거나 인터페이스를 구현할 때 적용됩니다. |
| CA2135 | [CA2135: 수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.](../code-quality/ca2135.md) | LinkDemands는 수준 2 보안 규칙 집합에서 사용되지 않습니다. JIT 컴파일 시 보안을 적용하는 데 LinkDemands를 사용하는 대신, 해당 메서드, 형식 및 필드를 SecurityCriticalAttribute 특성으로 표시하십시오. |
| CA2127 | [CA2136: 멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.](../code-quality/ca2136.md) | 100% 투명 어셈블리에서는 중요 코드가 나타날 수 없습니다. 이 규칙은 100% 투명 어셈블리의 형식, 필드 및 메서드 수준에서 SecurityCritical 주석 분석 합니다. |
| CA2136 | [CA2136: 멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.](../code-quality/ca2136.md) | 투명성 특성은 큰 범위의 코드 요소에서 작은 범위의 요소에 적용됩니다. 범위가 큰 코드 요소의 투명성 특성은 첫 번째 요소에 포함된 코드 요소의 투명성 특성보다 우선합니다. 예를 들어 SecurityCriticalAttribute를 사용하여 표시된 클래스에는 SecuritySafeCriticalAttribute 특성을 사용하여 표시된 메서드가 포함될 수 없습니다. |
| CA2137 | [CA2137: 투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.](../code-quality/ca2137.md) | 메서드가 확인할 수 없는 코드를 포함하거나 형식을 참조로 반환합니다. 이 규칙은 보안 투명 코드에서 확인할 수 없는 MSIL(Microsoft Intermediate Language)을 실행하려고 할 때 적용됩니다. 그러나 이 규칙은 완전한 IL 검증 도구를 포함하지 않으며 대신 추론을 사용하여 MSIL 확인 시 대부분의 위반을 catch합니다. |
| CA2138 | [CA2138: 투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.](../code-quality/ca2138.md) | 보안 투명 메서드가 SuppressUnmanagedCodeSecurityAttribute 특성을 사용하여 표시된 메서드를 호출합니다. |
| CA2139 | [CA2139: 투명 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다.](../code-quality/ca2139.md) | 이 규칙은 HandleProcessCorruptedStateExceptionsAttribute 특성을 사용하여 프로세스 손상 예외를 처리하려고 시도하는 모든 투명한 메서드에 적용됩니다. 프로세스 손상 예외는 AccessViolationException과 같은 예외의 CLR 버전 4.0 예외 분류입니다. HandleProcessCorruptedStateExceptionsAttribute 특성은 보안에 중요한 메서드에서만 사용할 수 있으며 투명 메서드에 적용되는 경우 무시됩니다. |
| CA2129 | [CA2140: 투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.](../code-quality/ca2140.md) | SecurityTransparentAttribute로 표시된 메서드가 SecurityCritical로 표시된 public이 아닌 멤버를 호출합니다. 이 규칙은 투명/중요 혼합 어셈블리의 모든 메서드와 형식을 분석하고 투명 코드에서 SecurityTreatAsSafe로 표시되지 않은 public이 아닌 중요 코드를 대상으로 하는 모든 호출을 플래그합니다. |
| CA2140 | [CA2140: 투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.](../code-quality/ca2140.md) | SecurityCriticalAttribute 특성을 사용하여 표시된 코드 요소는 보안에 중요합니다. 투명 메서드는 보안에 중요한 요소를 사용할 수 없습니다. 투명 형식이 보안에 중요한 형식을 사용하려고 시도하는 경우 TypeAccessException, MethodAccessException 또는 FieldAccessException이 발생합니다. |
| CA2141 |[CA2141: 투명한 메서드는 LinkDemands를 충족해서는 안 됩니다](../code-quality/ca2141.md) | 보안 투명 메서드가 APTCA를 사용하여 표시되지 않은 어셈블리의 메서드를 호출하거나, 보안 투명 메서드가 형식 또는 메서드에 대한 LinkDemand를 충족합니다. |
| CA2142 | [CA2142: 투명 코드는 LinkDemands로 보호될 수 없습니다.](../code-quality/ca2142.md) | 이 규칙은 액세스하는 데 LinkDemands가 필요한 투명한 메서드에 적용됩니다. 보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다. |
| CA2143 | [CA2143: 투명 메서드는 보안 요청을 사용할 수 없습니다.](../code-quality/ca2143.md) | 보안 투명 코드는 작업 보안을 확인할 책임이 없으므로 권한을 요구해서는 안 됩니다. 보안 투명 코드는 보안에 중요한 결정을 내리는 데 전체 요청을 사용해야 하며 안전에 중요한 코드는 전체 요청을 위해 투명 코드를 사용해서는 안 됩니다. |
| CA2144 | [CA2144: 투명 코드는 바이트 배열에서 어셈블리를 로드할 수 없습니다.](../code-quality/ca2144.md) | 투명 코드는 보안에 중요한 동작을 수행할 수 없기 때문에 투명 코드의 보안 검토는 중요 코드에 대한 보안 검토만큼 완벽하지 않습니다. 바이트 배열에서 로드된 어셈블리는 투명 코드에서 발견되지 않을 수 있으며 해당 바이트 배열은 감사할 필요가 있는 중요하거나 특히 안전에 중요한 코드를 포함할 수 있습니다. |
| CA2145 | [CA2145: 투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅할 수 없습니다.](../code-quality/ca2145.md) | SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅된 메서드에 이를 호출하는 메서드에 대한 암시적 LinkDemand가 배치되어 있습니다. 이 LinkDemand는 호출 코드가 보안을 중요시 하도록 요구합니다. SuppressUnmanagedCodeSecurity를 사용하는 메서드를 SecurityCriticalAttribute 특성으로 표시하면 이 요구 사항이 메서드 호출자에 더욱 명확하게 전달됩니다. |
| CA2146 | [CA2146: 형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.](../code-quality/ca2146.md) | 이 규칙은 파생 형식에 기본 형식 또는 구현된 인터페이스만큼 중요하지 않은 보안 투명성 특성이 있을 때 적용됩니다. 중요한 기본 형식에서 파생되거나 중요한 인터페이스를 구현할 수 있는 것은 중요한 형식뿐이고, 안전에 중요한 기본 형식에서 파생되거나 안전에 중요한 인터페이스를 구현할 수 있는 것은 중요하거나 안전에 중요한 형식뿐입니다. |
| CA2128 |[CA2147: 투명 메서드는 보안 어설션을 사용할 수 없습니다.](../code-quality/ca2147.md) | 이 규칙은 100% 투명 하거나 혼합 투명/중요 하 고 선언적 이거나 명령 적인 어설션 사용에 플래그를 제공 하는 어셈블리의 모든 형식과 메서드를 분석 합니다. |
| CA2147 |[CA2147: 투명 메서드는 보안 어설션을 사용할 수 없습니다.](../code-quality/ca2147.md) | SecurityTransparentAttribute로 표시된 코드에는 어설션하는 데 필요한 권한이 부여되지 않습니다. |
| CA2149 | [CA2149: 투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.](../code-quality/ca2149.md) | 이 규칙은 P/Invoke 등을 통해 네이티브 코드를 직접 호출하는 모든 투명 메서드에 적용됩니다. 이 규칙이 위반되면 수준 2 투명성 모델에서 MethodAccessException이 발생하고 수준 1 투명성 모델에서 UnmanagedCode에 대한 완전 요청이 발생합니다. |
| CA2151 |[CA2151: 중요한 형식이 포함된 필드는 보안에 중요한 필드여야 합니다.](../code-quality/ca2151.md) | 보안 중요 형식을 사용하려면 이 형식을 참조하는 코드가 보안 중요 또는 보안 안전 중요여야 합니다. 참조가 간접적인 경우에도 마찬가지입니다. 따라서 투명 코드는 필드에 액세스할 수 없으므로 보안 투명 또는 보안 안전 중요 필드가 있을 경우 잘못 해석됩니다. |
| CA2200 | [CA2200: 스택 정보를 유지하도록 다시 throw하십시오.](../code-quality/ca2200.md) | 예외가 다시 throw되며 예외가 throw 문에 명시적으로 지정되어 있습니다. throw 문에 예외를 지정하여 예외가 다시 throw되면 예외를 throw한 원래 메서드와 현재 메서드 간의 메서드 호출 목록이 손실됩니다. |
| CA2201 | [CA2201: 예약된 예외 형식을 발생시키지 마세요.](../code-quality/ca2201.md) | 따라서 원래 오류를 감지하고 디버깅하기 어렵게 됩니다. |
| CA2202 | [CA2202: 개체를 여러 번 삭제하지 마십시오.](../code-quality/ca2202.md) |같은 개체에 대해 System.IDisposable.Dispose 또는 Dispose와 동일한 기능의 메서드(예를 들어, 일부 형식의 Close() 메서드)가 여러 번 호출될 수 있는 코드 경로가 메서드 구현에 포함되어 있습니다. |
| CA2204 | [CA2204: 리터럴의 맞춤법이 정확해야 합니다.](../code-quality/ca2204.md) | 메서드 본문의 리터럴 문자열에 Microsoft 맞춤법 검사 라이브러리에서 인식하지 못하는 단어가 하나 이상 있습니다. |
| CA2205 | [CA2205: Win32 API의 동일한 관리형 기능을 사용하세요.](../code-quality/ca2205.md) | 운영 체제 호출 메서드가 정의 되 고 해당 기능을 포함 하는 .NET 메서드를 사용할 수 있습니다. |
| CA2207 | [CA2207: 값 형식 정적 필드 인라인을 초기화하십시오.](../code-quality/ca2207.md) | 값 형식에서 명시적인 정적 생성자를 선언합니다. 이 규칙 위반 문제를 해결하려면 모든 정적 데이터를 선언할 때 초기화하고 정적 생성자를 제거합니다. |
| CA2208 |[CA2208: 인수 예외를 올바르게 인스턴스화하세요.](../code-quality/ca2208.md) | ArgumentException 또는 ArgumentException에서 파생된 예외 형식의 기본(매개 변수가 없는) 생성자를 호출했거나, ArgumentException 또는 ArgumentException에서 파생된 예외 형식의 매개 변수가 있는 생성자에 잘못된 문자열 인수가 전달되었습니다. |
| CA2210 |[CA2210: 어셈블리에는 올바른 강력한 이름을 사용해야 합니다.](../code-quality/ca2210.md) | 강력한 이름은 클라이언트에서 무단으로 변경된 어셈블리를 모르는 사이에 로드하지 못하도록 보호합니다. 강력한 이름이 없는 어셈블리는 극히 제한된 시나리오 이외에는 배포하면 안 됩니다. 제대로 서명되지 않은 어셈블리를 공유하거나 배포하면 어셈블리가 무단으로 변경되거나, 공용 언어 런타임에서 어셈블리를 로드할 수 없거나, 사용자가 자신의 컴퓨터에서 확인을 사용하지 못하게 될 수 있습니다. |
| CA2211 |[CA2211: 비상수 필드는 노출되면 안 됩니다.](../code-quality/ca2211.md) | 상수도 아니고 읽기 전용도 아닌 static 필드는 스레드로부터 안전하지 않습니다. 이러한 필드에 대한 액세스는 신중하게 제어해야 하며 클래스 개체에 대한 액세스를 동기화하는 고급 프로그래밍 기술을 필요로 합니다. |
| CA2212 | [CA2212: 서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.](../code-quality/ca2212.md) |System.EnterpriseServices.ServicedComponent로부터 상속하는 형식의 메서드가 System.Web.Services.WebMethodAttribute로 표시되어 있습니다. WebMethodAttribute 및 ServicedComponent 메서드에는 컨텍스트와 트랜잭션 흐름에 있어 충돌하는 동작 및 요구 사항이 있으므로 메서드의 동작이 일부 시나리오에서 잘못됩니다. |
| CA2213 | [CA2213: 삭제 가능한 필드는 삭제해야 합니다.](../code-quality/ca2213.md) | System.IDisposable을 구현하는 형식이 마찬가지로 IDisposable을 구현하는 형식으로 된 필드를 선언합니다. 필드의 Dispose 메서드가 선언 형식의 Dispose 메서드에 의해 호출되지 않습니다. |
| CA2214 | [CA2214: 재정의 가능한 메서드를 생성자에서 호출하지 마십시오.](../code-quality/ca2214.md) | 생성자가 가상 메서드를 호출할 때 이 메서드를 호출하는 인스턴스의 생성자가 실행되지 않았을 가능성이 있습니다. |
| CA2215 | [CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.](../code-quality/ca2215.md) | 삭제 가능한 형식으로부터 상속하는 형식은 자신의 Dispose 메서드에서 기본 형식의 Dispose 메서드를 호출해야 합니다. |
| CA2216 |[CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.](../code-quality/ca2216.md) | System.IDisposable을 구현하고, 관리되지 않는 리소스의 사용을 암시하는 필드를 포함하는 형식이 Object.Finalize에 설명된 대로 종료자를 구현하지 않습니다. |
| CA2217 | [CA2217: 열거형을 FlagsAttribute로 표시하지 마세요.](../code-quality/ca2217.md) |외부에서 볼 수 있는 열거형이 FlagsAttribute로 표시되어 있고, 2의 거듭제곱 또는 열거형에 정의된 다른 값의 조합이 아닌 값이 하나 이상 들어 있습니다. |
| CA2218 |[CA2218: Equals를 재정할 때 GetHashCode를 재정의하세요.](../code-quality/ca2218.md) | GetHashCode는 현재 인스턴스를 기반으로 해싱 알고리즘 및 해시 테이블과 같은 데이터 구조체에 적합한 값을 반환합니다. 형식이 같은 동일한 두 개체는 동일한 해시 코드를 반환해야 합니다. |
| CA2219 | [CA2219: exception 절에서 예외를 발생시키지 마세요.](../code-quality/ca2219.md) | finally 또는 fault 절에서 예외가 발생하는 경우 새 예외가 활성 예외를 숨깁니다. filter 절에서 예외가 발생하는 경우 런타임이 자동으로 예외를 catch합니다. 따라서 원래 오류를 감지하고 디버깅하기 어렵게 됩니다. |
| CA2220 | [CA2220: 종료자는 기본 클래스 종료자를 호출해야 합니다.](../code-quality/ca2220.md) | 종료는 상속 계층을 통해 전파되어야 합니다. 이를 위해 형식은 자체 Finalize 메서드에서 기본 클래스의 Finalize 메서드를 호출해야 합니다. |
| CA2221 |[CA2221: 종료자는 protected여야 합니다.](../code-quality/ca2221.md) | 종료자에서는 패밀리 액세스 한정자를 사용해야 합니다. |
| CA2222 | [CA2222: 상속된 멤버 노출 수준을 낮추지 마세요.](../code-quality/ca2222.md) |상속된 멤버에 대한 액세스 한정자는 변경하면 안 됩니다. 상속된 멤버를 private으로 변경하더라도 호출자가 메서드의 기본 클래스 구현에 액세스하는 것을 막을 수 없습니다. |
| CA2223 | [CA2223: 멤버는 반환 형식 이외의 것도 달라야 합니다.](../code-quality/ca2223.md) | 공용 언어 런타임에서는 반환 값만 다르고 다른 면에서는 동일한 멤버를 구분할 수 있지만 이 기능은 공용 언어 사양에 해당되지 않으며 .NET 프로그래밍 언어의 공통 기능이 아닙니다. |
| CA2224 | [CA2224: 같음 연산자를 오버로드할 때 Equals를 재정의하세요.](../code-quality/ca2224.md) | public 형식이 같음 연산자를 구현하지만 Object.Equals를 재정의하지 않습니다. |
| CA2225 | [CA2225: 연산자 오버로드에는 명명된 대체 항목이 있습니다.](../code-quality/ca2225.md) |연산자 오버로드가 감지되었으며 예상되는 이름의 대체 메서드를 찾을 수 없습니다. 명명된 대체 멤버는 해당 연산자와 동일한 기능에 액세스할 수 있도록 해주며, 오버로드된 연산자가 지원되지 않는 언어로 프로그래밍하는 개발자에게 제공됩니다. |
| CA2226 | [CA2226: 연산자에는 대칭 오버로드가 있어야 합니다.](../code-quality/ca2226.md) | 형식이 같음 연산자 또는 같지 않음 연산자를 구현하면서 그 반대 연산자를 구현하지 않습니다. |
| CA2227 |[CA2227: 컬렉션 속성은 읽기 전용이어야 합니다.](../code-quality/ca2227.md) |쓰기 가능한 컬렉션 속성을 통해 사용자는 컬렉션을 다른 컬렉션으로 바꿀 수 있습니다. 읽기 전용 속성은 컬렉션을 바꾸지 못하도록 하지만 개별 멤버를 설정하는 것은 여전히 가능합니다. |
| CA2228 | [CA2228: 릴리스되지 않은 리소스 형식을 제공하지 마세요.](../code-quality/ca2228.md) | .NET의 시험판 버전을 사용 하 여 빌드한 리소스 파일은 지원 되는 버전의 .NET에서 사용 하지 못할 수 있습니다. |
| CA2229 | [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229.md) | 이 규칙 위반 문제를 해결하려면 serialization 생성자를 구현합니다. 봉인 클래스의 경우에는 생성자를 private으로 만들고, 그 밖의 경우에는 protected로 만듭니다. |
| CA2230 | [CA2230: 가변 인수로 params를 사용하세요.](../code-quality/ca2230.md) | public 또는 protected 형식에 params 키워드 대신 VarArgs 호출 규칙을 사용하는 public 또는 protected 메서드가 들어 있습니다. |
| CA2231 | [CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.](../code-quality/ca2231.md) | 값 형식이 Object.Equals를 재정의하지만 같음 연산자를 구현하지 않습니다. |
| CA2232 | [CA2232: Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.](../code-quality/ca2232.md) | STAThreadAttribute는 애플리케이션에 대한 COM 스레딩 모델이 단일 스레드 아파트임을 나타냅니다. 이 특성은 Windows Forms을 사용하는 애플리케이션의 진입점에 있어야 합니다. 이 특성을 생략하면 Windows 구성 요소가 제대로 작동하지 않을 수 있습니다. |
| CA2233 |[CA2233: 연산은 오버플로되지 않아야 합니다.](../code-quality/ca2233.md) | 산술 연산을 수행하려면 먼저 피연산자의 유효성을 검사하여 연산의 결과가 관련 데이터 형식의 가능한 값 범위를 벗어나지 않도록 해야 합니다. |
| CA2234 | [CA2234: 문자열 대신 System.Uri 개체를 전달하세요.](../code-quality/ca2234.md) | 이름에 "uri", "URI", "urn", "URN", "url" 또는 "URL"이 포함된 문자열 매개 변수가 있는 메서드가 호출되었습니다. 메서드의 선언 형식에 System.Uri 매개 변수를 가진 해당 메서드 오버로드가 들어 있습니다. |
| CA2235 | [CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.](../code-quality/ca2235.md) | serialize할 수 없는 형식의 인스턴스 필드가 serialize할 수 있는 형식에 정의되었습니다. |
| CA2236 | [CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.](../code-quality/ca2236.md) | 이 규칙 위반 문제를 해결하려면 해당하는 파생된 형식의 메서드나 생성자에서 기본 형식 GetObjectData 메서드나 serialization 생성자를 호출합니다. |
| CA2237 | [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237.md) | 공용 언어 런타임에서 serializable로 인식되도록 하려면 형식이 ISerializable 인터페이스 구현을 통해 사용자 지정 serialization 루틴을 사용하는 경우에도 형식을 SerializableAttribute 특성으로 표시해야 합니다. |
| CA2238 |[CA2238: serialization 메서드를 올바르게 구현하십시오.](../code-quality/ca2238.md) | serialization 이벤트를 처리하는 메서드에 올바른 시그니처, 반환 형식 또는 노출 수준이 없습니다. |
| CA2239 | [CA2239: 선택적 필드에 deserialization 메서드를 제공하세요.](../code-quality/ca2239.md) | 형식에 System.Runtime.Serialization.OptionalFieldAttribute 특성으로 표시된 필드가 있으며 형식에서 deserialization 이벤트 처리 메서드를 제공하지 않습니다. |
| CA2240 | [CA2240: ISerializable을 올바르게 구현하십시오.](../code-quality/ca2240.md) | 이 규칙 위반 문제를 해결하려면 GetObjectData 메서드를 표시하고 재정의 가능하도록 만든 다음 모든 인스턴스 필드가 serialization 프로세스에 포함되었는지 또는 NonSerializedAttribute 특성으로 명시적으로 표시되었는지 확인합니다. |
| CA2241 | [CA2241: 서식 지정 메서드에 올바른 인수를 제공하십시오.](../code-quality/ca2241.md) | System.String.Format에 전달된 format 인수에 각 개체 인수에 해당하는 형식 항목이 없거나 각 형식 항목에 해당하는 개체 인수가 없습니다. |
| CA2242 |[CA2242: NaN에 대해 정확하게 테스트하십시오.](../code-quality/ca2242.md) | 이 식은 Single.Nan 또는 Double.Nan에 대해 값을 테스트합니다. 값을 테스트하려면 Single.IsNan(Single) 또는 Double.IsNan(Double)을 사용합니다. |
| CA2243 |[CA2243: 특성 문자열 리터럴이 올바르게 구문 분석되어야 합니다.](../code-quality/ca2243.md) | 특성의 문자열 리터럴 매개 변수가 URL, GUID 또는 버전에 대해 구문을 올바르게 분석하지 않습니다. |
| CA2244 | [CA2244: 인덱싱된 요소의 초기화는 복제하면 안 됩니다.](../code-quality/ca2244.md) | 개체 이니셜라이저에 동일한 상수 인덱스를 사용 하는 두 개 이상의 인덱싱된 요소 이니셜라이저가 있습니다. 마지막 이니셜라이저가 아닌 모두 중복 됩니다. |
| CA2245 | [CA2245: 속성을 자체에 할당하지 마세요.](../code-quality/ca2245.md) | 속성이 실수로 자신에 게 할당 되었습니다. |
| CA2246 | [CA2246: 동일한 문에 기호 및 해당 멤버를 할당하지 마세요.](../code-quality/ca2246.md) | 동일한 문에서 기호와 해당 멤버, 즉 필드 또는 속성을 할당 하는 것은 권장 되지 않습니다. 멤버 액세스에서 할당 전 기호의 이전 값을 사용 하거나이 문의 할당에서 새 값을 사용 하기 위한 것은 분명 하지 않습니다. |
| CA2247 | [CA2247: Task Source 생성자에 전달 된 인수는 System.threading.tasks.taskcontinuationoptions enum이 아니라 TaskCreationOptions 열거형 이어야 합니다.](../code-quality/ca2247.md) | TaskTaskCreationOptions Source에는 기본 작업을 제어 하는 생성자와 작업에 저장 된 개체 상태를 사용 하는 생성자가 있습니다.  실수로 TaskCreationOptions 대신 System.threading.tasks.taskcontinuationoptions를 전달 하면 호출은 옵션을 state로 처리 합니다. |
| CA5122 | [CA5122 P/Invoke 선언이 안전 하 게 중요 한 것은 아닙니다.](../code-quality/ca5122.md) | 메서드는 보안에 중요한 작업을 수행할 때 SecuritySafeCritical로 표시되지만, 투명 코드에서도 안전하게 사용할 수 있습니다. 투명 코드는 P/Invoke를 통해 절대 네이티브 코드를 직접 호출할 수 없습니다. 따라서 P/Invoke를 SecuritySafeCritical로 표시할 경우 투명 코드가 P/Invoke를 호출할 수 없으며, 보안 분석에서 잘못 해석하는 원인이 됩니다. |
| CA5359 | [CA5359 인증서 유효성 검사를 사용 하지 않도록 설정 안 함](../code-quality/ca5359.md) | 인증서는 서버의 id를 인증 하는 데 도움이 될 수 있습니다. 클라이언트는 서버 인증서의 유효성을 검사 하 여 요청이 원하는 서버로 전송 되도록 해야 합니다. ServerCertificateValidationCallback에서 항상를 반환 `true` 하는 경우 모든 인증서가 유효성 검사를 통과 합니다. |
| CA5360 | [CA5360는 deserialization에서 위험한 메서드를 호출 하지 않습니다.](../code-quality/ca5360.md) | 안전 하지 않은 deserialization은 신뢰할 수 없는 데이터를 사용 하 여 응용 프로그램의 논리를 남용 하거나, DoS (서비스 거부) 공격을 수행 하거나, deserialize 될 때 임의의 코드를 실행할 때 발생 하는 취약성입니다. 응용 프로그램에서 제어 하는 신뢰할 수 없는 데이터를 deserialize 하는 경우 악의적인 사용자가 이러한 deserialization 기능을 악용할 수 있습니다. 특히 deserialization 프로세스에서 위험한 메서드를 호출 합니다. 안전 하지 않은 deserialization 공격에 성공 하면 공격자가 DoS 공격, 인증 바이패스 및 원격 코드 실행과 같은 공격을 수행할 수 있습니다. |
| CA5362 | [Deserialize 된 개체 그래프에서 잠재적 참조 주기 CA5362](../code-quality/ca5362.md) | 신뢰할 수 없는 데이터를 deserialize 하는 경우 deserialize 된 개체 그래프를 처리 하는 모든 코드는 무한 루프로 이동 하지 않고 참조 주기를 처리 해야 합니다. 여기에는 deserialization 콜백의 일부인 코드와 deserialization 완료 후 개체 그래프를 처리 하는 코드가 모두 포함 됩니다. 그렇지 않으면 공격자가 참조 주기를 포함 하는 악성 데이터를 사용 하 여 서비스 거부 공격을 수행할 수 있습니다. |
| CA5365 | [CA5365 HTTP 헤더 검사를 사용 하지 않도록 설정 안 함](../code-quality/ca5365.md) | HTTP 헤더 검사는 응답 헤더에 있는 캐리지 리턴 및 줄 바꿈 문자 (\r 및 \n)의 인코딩을 사용할 수 있도록 합니다. 이 인코딩 헤더에 포함 된 신뢰할 수 없는 데이터를 표시 하는 애플리케이션을 악용 하는 삽입 공격을 방지 하는 데 도움이 됩니다. |
| CA5366 | [CA5366 데이터 집합에 XmlReader를 사용 하 여 XML 읽기](../code-quality/ca5366.md) | 를 사용 하 여 <xref:System.Data.DataSet> 신뢰할 수 없는 데이터가 있는 XML을 읽으면 <xref:System.Xml.XmlReader> 보안 해결 프로그램을 사용 하거나 DTD 처리를 사용할 수 없는를 사용 하 여 제한 해야 하는 위험한 외부 참조가 로드 될 수 있습니다. |
| CA5367 | [CA5367는 포인터 필드를 사용 하 여 형식을 직렬화 하지 않습니다.](../code-quality/ca5367.md) | 이 규칙은 포인터 필드 또는 속성이 있는 serializable 클래스가 있는지 여부를 확인 합니다. Serialize 할 수 없는 멤버는 정적 멤버 또는로 표시 된 필드와 같은 포인터 일 수 있습니다 <xref:System.NonSerializedAttribute> . |
| CA5368 | [페이지에서 파생 된 클래스에 대 한 CA5368 Set ViewStateUserKey](../code-quality/ca5368.md) | 속성을 설정 하면 공격자가 변수를 사용 하 여 <xref:System.Web.UI.Page.ViewStateUserKey> 공격을 생성할 수 없도록 개별 사용자의 뷰 상태 변수에 식별자를 할당할 수 있으므로 응용 프로그램에 대 한 공격을 방지할 수 있습니다. 그렇지 않으면 교차 사이트 요청 위조에 대 한 취약성이 있습니다. |
| CA5374 | [CA5374 XslTransform 사용 안 함](../code-quality/ca5374.md) | 이 규칙 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 은가 코드에서 인스턴스화되어 있는지 확인 합니다. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 는 이제 사용 되지 않으며 사용할 수 없습니다. |
| CA5375 | [CA5375 계정 공유 액세스 서명 사용 안 함](../code-quality/ca5375.md) | 계정 SAS는 서비스 SAS로 허용 되지 않는 blob 컨테이너, 테이블, 큐 및 파일 공유에 대 한 읽기, 쓰기 및 삭제 작업에 대 한 액세스를 위임할 수 있습니다. 그러나 컨테이너 수준 정책을 지원 하지 않으며 부여 된 사용 권한에 대 한 유연성과 제어 수준이 낮습니다. 악의적인 사용자가이를 가져오면 저장소 계정이 쉽게 손상 됩니다. |
| CA5376 | [CA5376 SharedAccessProtocol HttpsOnly 사용](../code-quality/ca5376.md) | SAS는 HTTP에서 일반 텍스트로 전송할 수 없는 중요 한 데이터입니다. |
| CA5377 | [컨테이너 수준 액세스 정책을 사용 하는 CA5377](../code-quality/ca5377.md) | 컨테이너 수준 액세스 정책은 언제 든 지 수정 하거나 취소할 수 있습니다. 이를 통해 부여 되는 사용 권한을 보다 유연 하 게 제어할 수 있습니다. |
| CA5379 | [CA5379 약한 키 파생 함수 알고리즘 사용 안 함](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>클래스는 기본적으로 알고리즘을 사용 <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> 합니다. 이상에서 생성자의 일부 오버 로드에 사용할 해시 알고리즘을 지정 해야 합니다 <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> . 속성에는 <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> 접근자만 있으며 `get` 한정자가 없습니다 `overriden` . |
| CA5382 | [ASP.NET Core에서 보안 쿠키 사용 CA5382](../code-quality/ca5382.md) | HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 쿠키가 SSL(Secure Sockets Layer) (SSL)를 사용 하 여 전송 되어야 함을 브라우저에 표시 합니다. |
| CA5383 | [ASP.NET Core에서 보안 쿠키를 사용 하도록 CA5383](../code-quality/ca5383.md) | HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 쿠키가 SSL(Secure Sockets Layer) (SSL)를 사용 하 여 전송 되어야 함을 브라우저에 표시 합니다. |
| CA5384 | [CA5384 DSA (디지털 서명 알고리즘)를 사용 하지 않음](../code-quality/ca5384.md) | DSA는 약한 비대칭 암호화 알고리즘입니다. |
| CA5385 | [CA5385 Use Rivest – Rivest-shamir-adleman – Rivest-shamir-adleman (RSA) algorithm 키 크기가 충분 합니다.](../code-quality/ca5385.md) | 2048 비트 보다 작은 RSA 키는 무차별 암호 대입 공격에 보다 취약 합니다. |
| CA5387 | [CA5387 충분 하지 않은 반복 횟수로 약한 키 파생 함수를 사용 하지 않음](../code-quality/ca5387.md) | 이 규칙은 암호화 키가 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다. |
| CA5388 | [약한 키 파생 함수를 사용 하는 경우 충분 한 반복 횟수 확인 CA5388](../code-quality/ca5388.md) | 이 규칙은 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 암호화 키가 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다. |
| CA5390 | [CA5390 암호화 키를 하드 코딩 하지 않음](../code-quality/ca5390.md) | 대칭 알고리즘을 성공적으로 수행 하려면 비밀 키를 발신자와 수신자 에게만 인식 해야 합니다. 키가 하드 코드 되 면 쉽게 검색 됩니다. 컴파일된 이진 파일의 경우에도 악의적인 사용자가 쉽게 추출할 수 있습니다. 개인 키가 손상 되 면 암호화 텍스트를 직접 해독 하 여 더 이상 보호할 수 없습니다. |
| CA5391 | [ASP.NET Core MVC 컨트롤러에서 위조 방지 토큰 CA5391 사용](../code-quality/ca5391.md) | `POST` `PUT` `PATCH` `DELETE` 위조 방지 토큰의 유효성을 검사 하지 않고,, 또는 요청을 처리 하면 교차 사이트 요청 위조 공격에 취약할 수 있습니다. 사이트 간 요청 위조 공격은 인증 된 사용자의 악성 요청을 ASP.NET Core MVC 컨트롤러로 보낼 수 있습니다. |
| CA5392 | [P/Invoke에 대 한 CA5392 Use DefaultDllImportSearchPaths 특성](../code-quality/ca5392.md) | 기본적으로 P/Invoke 함수는 <xref:System.Runtime.InteropServices.DllImportAttribute> 로드 하는 라이브러리에 대 한 현재 작업 디렉터리를 포함 하 여 많은 디렉터리를 검색 합니다. 이는 특정 응용 프로그램에 대 한 보안 문제 이며 DLL 하이재킹이 될 수 있습니다. |
| CA5393 | [CA5393 unsafe DllImportSearchPath value 사용 안 함](../code-quality/ca5393.md) | 기본 DLL 검색 디렉터리와 어셈블리 디렉터리에 악성 DLL이 있을 수 있습니다. 또는 응용 프로그램이 실행 되는 위치에 따라 응용 프로그램 디렉터리에 악성 DLL이 있을 수 있습니다. |
| CA5394 | [CA5394은 안전 하지 않은 임의성을 사용 하지 않습니다.](../code-quality/ca5394.md) | 공격자는 암호화 된 약한 의사 난수 생성기를 사용 하 여 보안에 중요 한 값이 생성 되는 것을 예측할 수 있습니다. |
| CA5395 | [작업 메서드에 대 한 CA5395 누락 HttpVerb 특성](../code-quality/ca5395.md) | 데이터를 만들거나 편집, 삭제 또는 수정 하는 모든 작업 메서드는 사이트 간 요청 위조 공격 으로부터 위조 방지 특성으로 보호 해야 합니다. GET 작업을 수행 하는 것은 부작용이 없으며 지속형 데이터를 수정 하지 않는 안전 작업 이어야 합니다. |
| CA5396 | [되어에 대해 CA5396를 true로 설정 합니다.](../code-quality/ca5396.md) | 심층 방어 수단으로 보안에 민감한 HTTP 쿠키가 HttpOnly로 표시 되어 있는지 확인 합니다. 이는 웹 브라우저에서 스크립트가 쿠키에 액세스 하지 못하도록 하는 것을 의미 합니다. 삽입 된 악성 스크립트는 쿠키를 도용 하는 일반적인 방법입니다. |
| CA5399 | [CA5399 = HttpClient 인증서 해지 목록 확인](../code-quality/ca5399.md) | 해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다. |
| CA5400 | [CA5400 HttpClient 인증서 해지 목록 확인이 사용 하도록 설정 되지 않았는지 확인 합니다.](../code-quality/ca5400.md) | 해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다. |
| CA5401 | [CA5401는 기본값이 아닌 IV와 함께 CreateEncryptor를 사용 하지 않습니다.](../code-quality/ca5401.md) | 대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다. |
| CA5402 | [CA5402는 기본 IV와 함께 CreateEncryptor를 사용 합니다.](../code-quality/ca5402.md) | 대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다. |
| IL3000 | [IL3000 단일 파일로 게시할 때 어셈블리 파일 경로 액세스를 사용 하지 않습니다.](../code-quality/il3000.md) | 단일 파일로 게시할 때 어셈블리 파일 경로 액세스를 사용 하지 마십시오. |
