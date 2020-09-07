---
title: 코드 품질 규칙 개요
ms.date: 08/27/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
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
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
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
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8e4b728fab6eb47501bb0d1bb752d22c0c29a8b4
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509447"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>관리 코드 CheckId 별 코드 분석 경고

다음 표에서는 관리 코드에 대한 코드 분석 경고를 경고의 CheckId 식별자별로 보여 줍니다.

| CheckId | Warning | Description |
|---------| - | - |
| CA1000 | [CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.](../code-quality/ca1000.md) | 제네릭 형식의 정적 멤버를 호출할 때는 형식에 형식 인수를 지정해야 합니다. 유추를 지원하지 않는 제네릭 인스턴스 멤버를 호출할 때는 멤버에 형식 인수를 지정해야 합니다. 이 두 가지 경우에 형식 인수를 지정하기 위한 구문은 서로 다르며 혼동되기 쉽습니다. |
| CA1001 | [CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1001.md) | 클래스가 System.IDisposable 형식인 인스턴스 필드를 선언하고 구현하지만 IDisposable은 구현하지 않습니다. IDisposable 필드를 선언하는 클래스는 관리되지 않는 리소스를 간접적으로 소유하며 IDisposable 인터페이스를 구현해야 합니다. |
| CA1002 | [CA1002: 제네릭 목록을 노출하지 마세요.](../code-quality/ca1002.md) | < (Of \<(T> ) >)는 상속이 아닌 성능을 위해 디자인 된 제네릭 컬렉션입니다. 따라서 List에는 가상 멤버가 포함되지 않습니다. 상속을 위해 디자인된 제네릭 컬렉션이 대신 노출되어야 합니다. |
| CA1003 | [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.](../code-quality/ca1003.md) |void를 반환 하며 해당 시그니처에 두 개의 매개 변수 (개체가 첫 번째 및 두 번째는 EventArgs에 할당 될 수 있는 형식)를 포함 하는 대리자를 포함 하는 형식을 포함 하는 어셈블리에는 Microsoft.NET Framework 2.0 대상으로 합니다. |
| CA1005 | [CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.](../code-quality/ca1005.md) | 제네릭 형식에 포함된 형식 매개 변수가 많을수록 각 형식 매개 변수가 무엇을 나타내는지를 파악하거나 기억하기가 더 어렵습니다. 일반적으로 목록에서와 같이 하나의 형식 매개 변수를 사용 하 \<T> 고 사전에서와 같이 두 개의 형식 매개 변수를 사용 하는 것이 명확 \<TKey, TValue> 합니다. 그러나 형식 매개 변수가 세 개 이상이면 대부분의 사용자가 사용하기에 너무 어렵습니다. |
| CA1008 | [CA1008: 열거형에는 0 값이 있어야 합니다.](../code-quality/ca1008.md) | 초기화되지 않은 열거형의 기본값은 다른 값 형식과 마찬가지로 0입니다. 플래그 특성을 사용하지 않는 열거형에서는 기본값이 열거형의 유효한 값이 되도록 0 값을 사용하여 멤버를 정의해야 합니다. FlagsAttribute 특성이 적용된 열거형에서 0 값을 가진 멤버를 정의하는 경우에는 열거형에 값이 설정되지 않았음을 나타낼 수 있도록 해당 멤버 이름이 "None"이어야 합니다. |
| CA1010 | [CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.](../code-quality/ca1010.md) | 컬렉션의 유용성을 높이려면 제네릭 컬렉션 인터페이스 중 하나를 구현합니다. 그러면 컬렉션을 사용하여 제네릭 컬렉션 형식을 채울 수 있습니다. |
| CA1012 | [CA1012: 추상 형식에는 생성자를 사용하면 안 됩니다.](../code-quality/ca1012.md) | 추상 형식에 대한 생성자는 파생된 형식에서만 호출할 수 있습니다. public 생성자에서 형식의 인스턴스를 만들고 사용자는 추상 형식의 인스턴스를 만들 수 없기 때문에 public 생성자가 있는 추상 형식은 잘못 디자인된 것입니다. |
| CA1014 | [CA1014: CLSCompliantAttribute로 어셈블리를 표시하세요.](../code-quality/ca1014.md) | CLS(공용 언어 사양)는 어셈블리가 여러 프로그래밍 언어에 사용될 경우 준수해야 하는 명명 제한, 데이터 형식 및 규칙을 정의합니다. 모든 어셈블리에는 <xref:System.CLSCompliantAttribute>를 사용하여 CLS 규격을 명시적으로 나타내는 것이 좋습니다. 어셈블리에 이 특성이 없으면 해당 어셈블리는 규격을 따르지 않습니다. |
| CA1016 | [CA1016: AssemblyVersionAttribute로 어셈블리 표시](../code-quality/ca1016.md) | .NET에서는 버전 번호를 사용 하 여 어셈블리를 고유 하 게 식별 하 고 강력한 이름의 어셈블리에 있는 형식에 바인딩합니다. 버전 번호는 버전 및 게시자 정책과 함께 사용됩니다. 기본적으로 애플리케이션은 해당 애플리케이션이 빌드될 때 사용된 어셈블리 버전으로만 실행됩니다. |
| CA1017 | [CA1017: ComVisibleAttribute로 어셈블리를 표시하세요.](../code-quality/ca1017.md) |ComVisibleAttribute는 COM 클라이언트에서 관리 코드에 액세스하는 방식을 결정합니다. 어셈블리에서 COM에 노출할지 여부를 명시적으로 나타내는 것이 좋은 디자인입니다. 전체 어셈블리에 대해 COM 노출 여부를 설정한 다음 개별 형식 및 형식 멤버에 대해 이를 재정의할 수 있습니다. 이 특성이 없으면 COM 클라이언트에서 어셈블리의 내용을 볼 수 있습니다. |
| CA1018 | [CA1018: AttributeUsageAttribute로 특성을 표시하세요.](../code-quality/ca1018.md) | 사용자 지정 특성을 정의할 때는 해당 특성을 AttributeUsageAttribute로 표시하여 사용자 지정 특성을 적용할 수 있는 소스 코드의 위치를 나타냅니다. 특성의 의미 및 용도에 따라 코드에서의 유효한 위치가 결정됩니다. |
| CA1019 | [CA1019: 특성 인수의 접근자를 정의하세요.](../code-quality/ca1019.md) | 특성에서는 대상에 특성을 적용할 때 지정해야 하는 필수 인수를 정의할 수 있습니다. 이러한 인수는 특성 생성자에 위치 매개 변수로 제공되기 때문에 이러한 인수를 위치 인수라고도 합니다. 모든 필수 인수에 대해 특성은 실행 시간에 인수의 값을 검색할 수 있도록 해당하는 읽기 전용 속성도 제공해야 합니다. 특성에서는 명명된 인수라고 하는 선택적 인수도 정의할 수 있습니다. 이들 인수는 이름으로 특성 생성자에 제공되며 해당하는 읽기/쓰기 특성이 있어야 합니다. |
| CA1021 | [CA1021: out 매개 변수를 사용하지 마세요.](../code-quality/ca1021.md) | out 또는 ref를 사용하여 참조로 형식을 전달하려면 포인터 사용 방법을 알고 있어야 하고, 값 형식과 참조 형식이 어떻게 다른지 알고 있어야 하며, 반환 값이 여러 개인 메서드를 처리할 수 있어야 합니다. 또한 out 매개 변수와 ref 매개 변수의 차이점은 잘 알려져 있지 않습니다. |
| CA1024 | [CA1024: 적합한 속성을 사용하세요.](../code-quality/ca1024.md) | public 또는 protected 메서드가 "Get"으로 시작하는 이름을 사용하고, 매개 변수를 사용하지 않으며, 배열이 아닌 값을 반환합니다. 이 메서드는 속성이 될 수 있는 좋은 예일 수 있습니다. |
| CA1027 |[CA1027: 열거형을 FlagsAttribute로 표시하세요.](../code-quality/ca1027.md) | 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 명명된 상수를 의미 있게 조합할 수 있는 경우 열거형에 FlagsAttribute를 적용합니다. |
| CA1028 | [CA1028: 열거형 스토리지는 Int32여야 합니다.](../code-quality/ca1028.md) | 열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 기본적으로 System.Int32 데이터 형식은 상수 값을 저장하는 데 사용됩니다. 이 내부 형식을 변경할 수 있지만 대부분의 시나리오에서는 변경이 필요하지 않거나 권장되지 않습니다. |
| CA1030 | [CA1030: 적절한 경우 이벤트를 사용하세요.](../code-quality/ca1030.md) |이 규칙에서는 보통 이벤트에 사용되는 이름을 갖는 메서드를 찾아냅니다. 명확하게 정의된 상태 변경에 대한 응답으로 메서드를 호출할 경우 이 메서드는 이벤트 처리기에서 호출해야 합니다. 메서드를 호출하는 개체는 메서드를 직접 호출하는 대신 이벤트를 발생시켜야 합니다. |
| CA1031 | [CA1031: 일반적인 예외 형식을 catch하지 마세요.](../code-quality/ca1031.md) | 일반 예외는 catch하면 안 됩니다. 보다 구체적인 예외를 catch하거나, 일반적인 예외를 catch 블록의 마지막 문으로 다시 throw해야 합니다. |
| CA1032 |[CA1032: 표준 예외 생성자를 구현하세요.](../code-quality/ca1032.md) | 이들 생성자 집합을 전부 제공하지 못하면 예외를 제대로 처리하기 어려울 수 있습니다. |
| CA1033 | [CA1033: 인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.](../code-quality/ca1033.md) | 외부에서 볼 수 있는 unsealed 형식이 public 인터페이스의 명시적 메서드 구현을 제공하면서 외부에서 볼 수 있는 같은 이름의 대체 메서드를 제공하지 않습니다. |
| CA1034 | [CA1034: 중첩 형식은 노출되면 안 됩니다.](../code-quality/ca1034.md) | 중첩 형식은 다른 형식의 범위 내에 선언된 형식입니다. 중첩 형식은 포함하는 형식의 private 구현 정보를 캡슐화하는 데 유용합니다. 이 용도로 사용할 경우 중첩 형식은 외부에 노출되면 안 됩니다. |
| CA1036 | [CA1036: 비교 가능한 형식에 메서드를 재정의하세요.](../code-quality/ca1036.md) |public 또는 protected 형식이 System.IComparable 인터페이스를 구현합니다. 이 형식은 Object.Equals를 재정의하지 않으며 같음, 같지 않음, 보다 작음 또는 보다 큼에 대한 언어별 연산자를 오버로드하지 않습니다. |
| CA1040 |[CA1040: 빈 인터페이스를 사용하지 마세요.](../code-quality/ca1040.md) | 인터페이스에서는 동작이나 사용 계약을 제공하는 멤버를 정의합니다. 인터페이스에 의해 설명되는 기능은 상속 계층 구조에서 형식이 나타나는 위치에 관계없이 모든 형식에서 사용할 수 있습니다. 형식에서는 인터페이스의 멤버에 대한 구현을 제공하여 인터페이스를 구현합니다. 빈 인터페이스는 멤버를 정의하지 않으므로 구현 가능한 계약을 정의하지 않습니다. |
| CA1041 | [CA1041: ObsoleteAttribute 메시지를 제공하세요.](../code-quality/ca1041.md) | 형식 또는 멤버가 ObsoleteAttribute.Message 속성이 지정되지 않은 System.ObsoleteAttribute 특성으로 표시되어 있습니다. ObsoleteAttribute로 표시된 형식 또는 멤버를 컴파일하면 해당 특성의 Message 속성이 표시되어 사용되지 않는 형식 또는 멤버에 대한 정보가 사용자에게 제공됩니다. |
| CA1043 | [CA1043: 인덱서에 정수 또는 문자열 인수를 사용하세요.](../code-quality/ca1043.md) | 인덱서, 즉 인덱싱된 속성은 인덱스에 정수 계열 형식이나 문자열 형식을 사용해야 합니다. 이러한 형식은 대개 데이터 구조를 인덱싱하는 데 사용되며 라이브러리의 유용성을 증가시킵니다. Object 형식은 디자인 타임에 특정 정수 계열 형식이나 문자열 형식을 지정할 수 없는 경우에만 제한적으로 사용해야 합니다. |
| CA1044 | [CA1044: 속성은 쓰기 전용이면 안 됩니다.](../code-quality/ca1044.md) | 읽기 전용 속성을 사용하는 것은 가능하고 종종 필요하기도 하지만 쓰기 전용 속성의 사용은 금지되어 있습니다. 사용자에게 값을 설정하도록 허용한 다음 해당 값을 볼 수 없도록 하면 보안상 문제가 있기 때문입니다. 또한 읽기 권한이 없으면 공유 개체의 상태를 볼 수 없으므로 사용하는 데 제한을 받습니다. |
| CA1045 |[CA1045: 참조로 형식을 전달하지 마세요.](../code-quality/ca1045.md) | out 또는 ref를 사용하여 참조로 형식을 전달하려면 포인터 사용 방법을 알고 있어야 하고, 값 형식과 참조 형식이 어떻게 다른지 알고 있어야 하며, 반환 값이 여러 개인 메서드를 처리할 수 있어야 합니다. 일반 사용자를 위해 디자인 한 라이브러리 설계자는 사용자가 `out` 또는 매개 변수로 작업 하는 것을 원하지 않습니다 `ref` . |
| CA1046 | [CA1046: 참조 형식에 같음 연산자를 오버로드하지 마세요.](../code-quality/ca1046.md) | 참조 형식의 경우 같음 연산자의 기본 구현은 대부분 항상 올바릅니다. 기본적으로 두 참조는 같은 개체를 가리킬 경우에만 같습니다. |
| CA1047 |[CA1047: protected 멤버를 sealed 형식으로 선언하지 마세요.](../code-quality/ca1047.md) | 형식에서는 상속하는 형식에서 멤버에 액세스하거나 멤버를 재정의할 수 있도록 하기 위해 protected 멤버를 선언합니다. 정의에 따라 sealed 형식은 상속할 수 없으므로 sealed 형식에 대해 protected 메서드를 호출할 수 없습니다. |
| CA1050 | [CA1050: 네임스페이스에 형식을 선언하세요.](../code-quality/ca1050.md) | 이름 충돌을 방지하고 관련된 형식을 개체 계층 구조로 구성하기 위해 형식은 네임스페이스 안에 선언됩니다. |
| CA1051 | [CA1051: 표시되는 인스턴스 필드를 선언하지 마세요.](../code-quality/ca1051.md) | 필드의 주된 용도는 구현을 세부적으로 설명하는 것입니다. 필드는 private 또는 internal이어야 하고 속성을 통해 노출되어야 합니다. |
| CA1052 | [CA1052: 정적 소유자 형식은 sealed여야 합니다.](../code-quality/ca1052.md) | public 또는 protected 형식이 정적 멤버만 포함하며 sealed(C# 참조)(NotInheritable) 한정자로 선언되지 않았습니다. 상속을 고려하지 않은 형식은 sealed 한정자로 표시하여 기본 형식으로 사용되지 않도록 해야 합니다. |
| CA1053 |[CA1053: 정적 소유자 형식에는 생성자를 사용하면 안 됩니다.](../code-quality/ca1053.md) | public 또는 중첩된 public 형식에서 정적 멤버만 선언하며 public 또는 protected 기본 생성자를 사용합니다. 호출하는 정적 멤버에 형식의 인스턴스가 필요하지 않기 때문에 생성자가 필요 없습니다. 문자열 오버로드는 안전과 보안을 위해 문자열 인수를 사용하여 URI(Uniform Resource Identifier) 오버로드를 호출해야 합니다. |
| CA1054 | [CA1054: URI 매개 변수는 문자열이면 안 됩니다.](../code-quality/ca1054.md) | 메서드가 URI의 문자열 표현을 사용하면 URI 클래스의 인스턴스를 사용하는 해당 오버로드를 제공해야 합니다. 이렇게 하면 서비스가 안전한 방식으로 제공됩니다. |
| CA1055 | [CA1055: URI 반환 값은 문자열이면 안 됩니다.](../code-quality/ca1055.md) | 이 규칙에서는 메서드가 URI를 반환한다고 가정합니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. System.Uri 클래스는 이러한 서비스를 안전한 방식으로 제공합니다. |
| CA1056 | [CA1056: URI 속성은 문자열이면 안 됩니다.](../code-quality/ca1056.md) | 이 규칙에서는 속성이 URI(Uniform Resource Identifier)를 나타낸다고 가정합니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. System.Uri 클래스는 이러한 서비스를 안전한 방식으로 제공합니다. |
| CA1058 | [CA1058: 형식은 특정 기본 형식을 확장하면 안 됩니다.](../code-quality/ca1058.md) | 외부에서 볼 수 있는 형식이 특정 기본 형식을 확장합니다. 다음 방법 중 하나를 사용합니다. |
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
| CA1303 | [CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.](../code-quality/ca1303.md) | 외부에서 볼 수 있는 메서드는 문자열 리터럴을 .NET 생성자 또는 메서드에 대 한 매개 변수로 전달 하 고 해당 문자열을 지역화할 수 있어야 합니다. |
| CA1304 | [CA1304: CultureInfo를 지정하세요.](../code-quality/ca1304.md) | 메서드 또는 생성자가 System.Globalization.CultureInfo 매개 변수를 받아들이는 오버로드가 있는 멤버를 호출하지만 CultureInfo 매개 변수를 사용하는 오버로드는 호출하지 않습니다. CultureInfo 또는 System.IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다. |
| CA1305 | [CA1305: IFormatProvider를 지정하세요.](../code-quality/ca1305.md) | 메서드 또는 생성자가 System.IFormatProvider 매개 변수를 받아들이는 오버로드가 있는 하나 이상의 멤버를 호출하지만 IFormatProvider 매개 변수를 사용하는 오버로드는 호출하지 않습니다. System.Globalization.CultureInfo 또는 IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다. |
| CA1307 | [CA1307: 명확성을 위해 StringComparison 지정](../code-quality/ca1307.md) | 문자열 비교 작업에서 StringComparison 매개 변수를 설정하지 않는 메서드 오버로드를 사용합니다. |
| CA1308 |[CA1308: 대문자로 문자열을 정규화하세요.](../code-quality/ca1308.md) | 문자열은 대문자로 정규화되어야 합니다. 일부 문자는 소문자로 변환될 때 다시 대문자로 변환될 수 없습니다. |
| CA1309 | [CA1309: 서수 StringComparison을 사용하세요.](../code-quality/ca1309.md) | 비언어 문자열 비교 작업에서는 StringComparison 매개 변수를 Ordinal 또는 OrdinalIgnoreCase로 설정하지 않습니다. 매개 변수가 명시적으로 StringComparison.Ordinal 또는 StringComparison.OrdinalIgnoreCase로 설정되기 때문에 코드 실행 속도, 정확도 및 신뢰도가 향상됩니다. |
| CA1310 | [CA1310: 정확성을 위해 StringComparison 지정](../code-quality/ca1310.md) | 문자열 비교 작업은 StringComparison 매개 변수를 설정 하지 않고 기본적으로 문화권별 문자열 비교를 사용 하는 메서드 오버 로드를 사용 합니다. |
| CA1401 | [CA1401: P/Invoke는 노출 되지 않아야 합니다.](../code-quality/ca1401.md) | public 형식의 public 또는 protected 메서드는 System.Runtime.InteropServices.DllImportAttribute 특성을 가지며 또한 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]에서 Declare 키워드로 구현됩니다. 이러한 메서드는 노출되지 않아야 합니다. |
| CA1417 | [CA1417: `OutAttribute` P/invoke에 문자열 매개 변수를 사용 하지 마십시오.](../code-quality/ca1417.md) | 로 값으로 전달 되는 문자열 매개 변수는 `OutAttribute` 문자열이 인턴 문자열이 면 런타임을 불안정 하 게 만들 수 있습니다. |
| CA1501 | [CA1501: 상속성을 너무 많이 사용하지 마세요.](../code-quality/ca1501.md) | 형식이 상속 계층 구조에서 네 단계보다 아래에 있습니다. 여러 번 중첩된 형식 계층 구조는 추적하고, 이해하고, 유지 관리하기가 어렵습니다. |
| CA1502 | [CA1502: 지나치게 복잡하게 만들지 마세요.](../code-quality/ca1502.md) | 이 규칙은 메서드를 통과하는 선형 독립 경로의 수를 측정하며 조건부 분기의 수와 복잡성에 의해 결정됩니다. |
| CA1505 | [CA1505: 유지 관리할 수 없는 코드를 사용하지 마세요.](../code-quality/ca1505.md) | 형식 또는 메서드에 낮은 유지 관리 인덱스 값이 있습니다. 낮은 유지 관리 인덱스는 형식 또는 메서드가 유지 관리하기 어렵고 다시 디자인될 수 있음을 나타냅니다. |
| CA1506 | [CA1506: 클래스를 지나치게 많이 결합하지 마세요.](../code-quality/ca1506.md) | 이 규칙은 형식 또는 메서드에 들어 있는 고유한 형식 참조의 개수를 계산하여 클래스 결합을 측정합니다. |
| CA1507 | [CA1507: 문자열 대신 nameof 사용](../code-quality/ca1507.md) | 문자열 리터럴은 식을 사용할 수 있는 인수로 사용 됩니다 `nameof` . |
| CA1508 | [CA1508: 데드 조건부 코드 방지](../code-quality/ca1508.md) | 메서드에는 항상 `true` 또는 런타임 시로 계산 되는 조건부 코드가 있습니다 `false` . 이렇게 하면 조건의 분기에서 데드 코드가 발생 `false` 합니다. |
| CA1509 | [CA1509: 코드 메트릭 구성 파일의 잘못된 항목](../code-quality/ca1509.md) | [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) 및 [CA1506](ca1506.md)와 같은 코드 메트릭 규칙에서 `CodeMetricsConfig.txt` 잘못 된 항목을 포함 하는 이라는 구성 파일을 제공 했습니다. |
| CA1700 | [CA1700: 열거형 값의 이름을 'Reserved'로 지정하지 마세요.](../code-quality/ca1700.md) | 이 규칙에서는 "reserved"라는 단어가 포함된 이름을 갖는 열거형 멤버가 현재 사용되지는 않지만 이후 버전에서 이름이 바뀌거나 제거될 자리 표시자라고 가정합니다. 멤버의 이름을 바꾸거나 멤버를 제거하는 것은 주요 변경에 해당합니다. |
| CA1707 | [CA1707: 식별자에는 밑줄을 사용할 수 없습니다.](../code-quality/ca1707.md) | 규칙에 따라 식별자 이름에는 밑줄 문자(_)가 포함될 수 없습니다. 이 규칙에서는 네임스페이스, 형식, 멤버 및 매개 변수를 검사합니다. |
| CA1708 | [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708.md) | 공용 언어 런타임을 대상으로 하는 언어는 대/소문자를 구분하지 않으므로 네임스페이스, 형식, 멤버 및 매개 변수의 식별자가 대/소문자만 달라서는 안 됩니다. |
| CA1710 | [CA1710: 식별자에는 올바른 접미사를 사용해야 합니다.](../code-quality/ca1710.md) |규칙에 따라 특정 기본 형식을 확장하거나 특정 인터페이스를 구현하는 형식 또는 이러한 형식에서 파생되는 형식은 이름에 기본 형식이나 인터페이스와 연관된 접미사를 갖습니다. |
| CA1711 | [CA1711: 식별자에는 올바른 접미사를 사용해야 합니다.](../code-quality/ca1711.md) | 규칙에 따라 특정 기본 형식을 확장하거나 특정 인터페이스를 구현하는 형식의 이름 또는 이러한 형식에서 파생되는 형식의 이름만이 예약된 특정 접미사로 끝나야 합니다. 다른 형식 이름에는 이러한 예약된 접미사를 사용하면 안 됩니다. |
| CA1712 | [CA1712: 열거형 값에 형식 이름을 접두사로 사용하지 마세요.](../code-quality/ca1712.md) | 개발 도구에서 형식 정보를 제공하므로 열거형 멤버의 이름에는 형식 이름을 접두사로 사용하지 않습니다. |
| CA1713 | [CA1713: 이벤트에 Before 또는 After 접두사를 사용하지 마세요.](../code-quality/ca1713.md) | 이벤트 이름이 "Before" 또는 "After"로 시작합니다. 특정 시퀀스에서 발생하는 관련 이벤트의 이름을 지정하려면 현재 또는 과거 시제를 사용하여 동작 시퀀스 내의 상대적인 위치를 나타냅니다. |
| CA1714 | [CA1714: 플래그 열거형에는 복수형 이름을 사용해야 합니다.](../code-quality/ca1714.md) | public 열거형에 System.FlagsAttribute 특성이 있고 이름이 "s"로 끝나지 않았습니다. FlagsAttribute 특성은 둘 이상의 값을 지정할 수 있음을 나타내므로 이 특성으로 표시된 형식은 복수형 이름을 갖습니다. |
| CA1715 | [CA1715: 식별자에는 올바른 접두사를 사용해야 합니다.](../code-quality/ca1715.md) | 외부에 노출되는 인터페이스의 이름이 대문자 "I"로 시작하지 않습니다. 외부에 노출되는 형식 또는 메서드의 제네릭 형식 매개 변수 이름이 대문자 "T"로 시작하지 않습니다. |
| CA1716 | [CA1716: 식별자는 키워드와 달라야 합니다.](../code-quality/ca1716.md) | 네임스페이스 이름 또는 형식 이름이 프로그래밍 언어의 예약된 키워드와 일치합니다. 네임스페이스 및 형식에 대한 식별자는 공용 언어 런타임을 대상으로 하는 언어에서 정의된 키워드와 일치하면 안 됩니다. |
| CA1717 | [CA1717: FlagsAttribute 열거형만 복수형 이름을 가질 수 있습니다.](../code-quality/ca1717.md) | 명명 규칙은 열거형 이름이 복수형인 경우 여러 열거 값을 동시에 지정할 수 있음을 나타내도록 되어 있습니다. |
| CA1720 |[CA1720: 식별자에 형식 이름을 포함하면 안 됩니다.](../code-quality/ca1720.md) | 외부에 노출되는 멤버의 매개 변수 이름에 데이터 형식 이름이 포함되어 있거나 외부에 노출되는 멤버의 이름에 언어에 따라 다른 데이터 형식 이름이 포함되어 있습니다. |
| CA1721 | [CA1721: 속성 이름은 Get 메서드와 달라야 합니다.](../code-quality/ca1721.md) |public 또는 protected 멤버의 이름이 "Get"으로 시작하며 이름의 나머지 부분이 public 또는 protected 속성의 이름과 같습니다. "Get" 메서드와 속성은 서로가 분명히 구분되는 이름을 사용해야 합니다. |
| CA1724 | [CA1724: 형식 이름은 네임스페이스와 달라야 합니다.](../code-quality/ca1724.md) | 형식 이름은 .NET 네임 스페이스의 이름과 일치 하면 안 됩니다. 이 규칙을 위반하면 라이브러리의 유용성이 저하될 수 있습니다. |
| CA1725 | [CA1725: 매개 변수 이름은 기본 선언과 일치해야 합니다.](../code-quality/ca1725.md) | 재정의 계층 구조에서 매개 변수 이름을 일관되게 지정하면 메서드 재정의를 더 편리하게 사용할 수 있습니다. 파생된 메서드의 매개 변수 이름이 기본 선언의 이름과 다르면 메서드가 기본 메서드의 재정의인지 메서드의 새 오버로드인지를 혼동할 수 있습니다. |
| CA1801 | [CA1801: 사용되지 않은 매개 변수를 검토하세요.](../code-quality/ca1801.md) | 메서드 시그니처에 메서드 본문에서 사용되지 않는 매개 변수가 있습니다. |
| CA1802 |[CA1802: 가능하면 리터럴을 사용하세요.](../code-quality/ca1802.md) |필드가 static 및 read-only([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]의 경우 Shared 및 ReadOnly)로 선언되었으며 컴파일할 때 계산할 수 있는 값으로 초기화되어 있습니다. 컴파일 시간에 대상된 필드에 할당 되는 값을 계산할 이기 때문에 const 선언을 변경 (에서 Const [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 필드 값을 런타임 대신 컴파일 시간에 계산 되도록 합니다. |
| CA1805 | [CA1805: 불필요하게 초기화하지 마세요.](../code-quality/ca1805.md) | .NET 런타임은 생성자를 실행 하기 전에 참조 형식의 모든 필드를 기본값으로 초기화 합니다. 대부분의 경우 필드를 기본값으로 명시적으로 초기화 하면 유지 관리 비용이 증가 하 고 성능이 저하 될 수 있습니다 (예: 어셈블리 크기 증가). |
| CA1806 | [CA1806: 메서드 결과를 무시하지 마세요.](../code-quality/ca1806.md) | 새 개체가 만들어지지만 사용되지 않거나, 새 문자열을 만들고 반환하는 메서드가 호출되고 새 문자열이 사용되지 않거나, COM 또는 P/Invoke 메서드가 사용되지 않는 오류 코드나 HRESULT를 반환합니다. |
| CA1810 | [CA1810: 참조 형식 정적 필드를 인라인으로 초기화하세요.](../code-quality/ca1810.md) | 형식이 명시적인 정적 생성자를 선언하면 JIT(Just-in-Time) 컴파일러는 형식의 각 정적 메서드와 인스턴스 생성자에 검사를 추가하여 정적 생성자를 이전에 호출했는지 확인합니다. 정적 생성자 검사로 인해 성능이 저하될 수 있습니다. |
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
| CA1834 |[CA1834: 단일 문자열에 대해 StringBuilder. Append (char)를 사용 하십시오.](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder>`Append`에는를 인수로 사용 하는 오버 로드가 있습니다 `char` . 성능상의 이유로 오버 로드를 호출 하는 것이 좋습니다 `char` . |
| CA1835 |[CA1835: ' ReadAsync ' 및 ' WriteAsync '에 대해 ' Memory' 기반 오버 로드를 선호 합니다.](../code-quality/ca1835.md) | ' Stream '에는 첫 번째 인수로 ' Memory Byte '를 사용 하는 ' ReadAsync ' 오버 로드 &lt; &gt; 와 ' ReadOnlyMemory &lt; Byte &gt; '를 첫 번째 인수로 사용 하는 ' WriteAsync ' 오버 로드가 있습니다. 더 효율적인 메모리 기반 오버 로드를 호출 하는 것이 좋습니다. |
| CA1836 |[CA1836: `IsEmpty` `Count` 사용 가능한 경우 선호](../code-quality/ca1836.md) | `IsEmpty`, 또는 보다 효율적인 속성을 사용 `Count` `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 하 여 개체에 항목이 포함 되어 있는지 여부를 확인 하는 것이 좋습니다. |
| CA1837 | [CA1837: 대신을 사용 합니다. `Environment.ProcessId``Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` 는 보다 간단 하 고 빠릅니다 `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: `StringBuilder` P/invoke에 대 한 매개 변수를 사용 하지 않습니다.](../code-quality/ca1838.md) | ' StringBuilder '를 마샬링하면 항상 네이티브 버퍼 복사본이 만들어지므로 하나의 마샬링 작업에 대해 여러 할당이 발생 합니다. |
| CA2000 | [CA2000: 범위를 벗어나기 전에 개체를 삭제하세요.](../code-quality/ca2000.md) | 개체의 종료자가 실행되지 못하도록 하는 예외 이벤트가 발생할 수 있기 때문에 개체에 대한 모든 참조가 범위를 벗어나기 전에 개체를 명시적으로 삭제해야 합니다. |
| CA2002 |[CA2002: 약한 ID를 가진 개체를 잠그지 마십시오.](../code-quality/ca2002.md) |애플리케이션 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다. 약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 애플리케이션 도메인의 스레드에 의해 차단될 수 있습니다. |
| CA2007 | [CA2007: 작업을 직접 대기하지 마세요.](ca2007.md) | 비동기 메서드는를 직접 [기다립니다](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> 합니다. 비동기 메서드가 <xref:System.Threading.Tasks.Task> 직접 기다립니다 작업을 만든 스레드와 동일한 스레드에서 연속 작업을 수행 합니다. 이 동작은 성능 측면에서 비용이 많이 들 수 있으며 UI 스레드에 교착 상태가 발생할 수 있습니다. 을 호출 <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> 하 여 연속 작업을 위한 신호를 보내는 것이 좋습니다. |
| CA2008 | [CA2008: TaskScheduler를 전달하지 않은 상태에서 작업을 만들지 않음](ca2008.md) | 작업 만들기 또는 연속 작업에서 매개 변수를 지정 하지 않는 메서드 오버 로드를 사용 <xref:System.Threading.Tasks.TaskScheduler> 합니다. |
| CA2009 | [CA2009: ImmutableCollection 값의 ToImmutableCollection을 호출하지 마세요.](ca2009.md) | `ToImmutable` 네임 스페이스의 변경할 수 없는 컬렉션에 대해 메서드를 불필요 하 게 호출 했습니다 <xref:System.Collections.Immutable> . |
| CA2011 | [CA2011: Setter 내에서 속성을 할당하지 마세요.](ca2011.md) | 속성에 해당 하는 자체 [set 접근자](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)내에 값이 실수로 할당 되었습니다. |
| CA2012 | [CA2012: ValueTasks를 올바르게 사용하세요.](ca2012.md) | 멤버 호출에서 반환 되는 ValueTasks는 직접 대기 합니다.  는 특정 기능을 여러 번 사용 하거나 완료 되기 전에 한 결과에 직접 액세스 하려고 시도 하 여 예외 또는 손상이 발생할 수 있습니다.  이러한 것을 무시 하면 기능적 버그를 나타낼 수 있으며 성능이 저하 될 수 있습니다. |
| CA2013 | [CA2013: 값 형식과 함께 ReferenceEquals를 사용하지 마세요.](ca2013.md) | 를 사용 하 여 값을 비교할 때 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> objA와 Obja가 값 형식이 면 메서드로 전달 되기 전에 boxing 됩니다 <xref:System.Object.ReferenceEquals%2A> . 즉, objA와 Obja가 모두 값 형식의 동일한 인스턴스를 나타내는 경우에도 <xref:System.Object.ReferenceEquals%2A> 메서드에서 false를 반환 합니다. |
| CA2014 | [CA2014: 루프에서 stackalloc을 사용 하지 마십시오.](ca2014.md) | Stackalloc에 의해 할당 된 스택 공간은 현재 메서드 호출의 끝 에서만 해제 됩니다.  루프에서이를 사용 하면 바인딩되지 않은 스택 증가 및 최종 스택 오버플로 조건이 발생할 수 있습니다. |
| CA2015 | [CA2015: MemoryManager T에서 파생 된 형식에 대 한 종료자를 정의 하지 않습니다. &lt;&gt;](ca2015.md) | 에서 파생 된 형식에 종료자를 추가 하면에서 <xref:System.Buffers.MemoryManager%601> 아직 사용 중인 메모리를 해제할 수 있습니다 <xref:System.Span%601> . |
| CA2016 | [CA2016: 인수 하나를 사용하는 메서드에 CancellationToken 매개 변수를 전달하세요.](ca2016.md) | `CancellationToken`매개 변수를 사용 하 여 작업 취소 알림이 제대로 전파 되는지 확인 하거나 `CancellationToken.None` 의도적으로 토큰을 전파 하지 않도록 명시적으로 전달 하는 메서드에 매개 변수를 전달 합니다. |
| CA2100 | [CA2100: 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.](../code-quality/ca2100.md) | 메서드가 메서드에 대한 문자열 인수로부터 만들어진 문자열을 사용하여 System.Data.IDbCommand.CommandText 속성을 설정합니다. 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다. |
| CA2101 |[CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101.md) | 플랫폼 호출 멤버가 부분 신뢰 호출자를 허용하고, 문자열 매개 변수를 사용하고, 문자열을 명시적으로 마샬링하지 않습니다. 이렇게 하면 보안상 위험할 수 있습니다. |
| CA2109 | [CA2109: 표시되는 이벤트 처리기를 검토하세요.](../code-quality/ca2109.md) | public 또는 protected 이벤트 처리 메서드를 발견했습니다. 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다. |
| CA2119 | [CA2119: private 인터페이스를 만족하는 메서드를 봉인하세요.](../code-quality/ca2119.md) | 상속할 수 있는 public 형식에서는 internal([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]의 경우 Friend) 인터페이스의 재정의 가능한 메서드 구현을 제공합니다. 이 규칙 위반 문제를 해결하려면 어셈블리 외부에서 메서드가 재정의되지 않도록 합니다. |
| CA2153 |[CA2153: 손상 된 상태 예외 처리 방지](../code-quality/ca2153.md) | CSEs (손상 된 상태 예외)는 프로세스에 메모리 손상이 있는지를 표시 합니다. 프로세스 충돌을 허용하는 대신 catch하면 공격자가 손상된 메모리 영역에 익스플로잇을 배치할 수 있는 경우 보안 취약점이 발생할 수 있습니다. |
| CA2200 | [CA2200: 스택 정보를 유지하도록 다시 throw하십시오.](../code-quality/ca2200.md) | 예외가 다시 throw되며 예외가 throw 문에 명시적으로 지정되어 있습니다. throw 문에 예외를 지정하여 예외가 다시 throw되면 예외를 throw한 원래 메서드와 현재 메서드 간의 메서드 호출 목록이 손실됩니다. |
| CA2201 | [CA2201: 예약된 예외 형식을 발생시키지 마세요.](../code-quality/ca2201.md) | 따라서 원래 오류를 감지하고 디버깅하기 어렵게 됩니다. |
| CA2207 | [CA2207: 값 형식 정적 필드 인라인을 초기화하십시오.](../code-quality/ca2207.md) | 값 형식에서 명시적인 정적 생성자를 선언합니다. 이 규칙 위반 문제를 해결하려면 모든 정적 데이터를 선언할 때 초기화하고 정적 생성자를 제거합니다. |
| CA2208 |[CA2208: 인수 예외를 올바르게 인스턴스화하세요.](../code-quality/ca2208.md) | ArgumentException 또는 ArgumentException에서 파생된 예외 형식의 기본(매개 변수가 없는) 생성자를 호출했거나, ArgumentException 또는 ArgumentException에서 파생된 예외 형식의 매개 변수가 있는 생성자에 잘못된 문자열 인수가 전달되었습니다. |
| CA2211 |[CA2211: 비상수 필드는 노출되면 안 됩니다.](../code-quality/ca2211.md) | 상수도 아니고 읽기 전용도 아닌 static 필드는 스레드로부터 안전하지 않습니다. 이러한 필드에 대한 액세스는 신중하게 제어해야 하며 클래스 개체에 대한 액세스를 동기화하는 고급 프로그래밍 기술을 필요로 합니다. |
| CA2213 | [CA2213: 삭제 가능한 필드는 삭제해야 합니다.](../code-quality/ca2213.md) | System.IDisposable을 구현하는 형식이 마찬가지로 IDisposable을 구현하는 형식으로 된 필드를 선언합니다. 필드의 Dispose 메서드가 선언 형식의 Dispose 메서드에 의해 호출되지 않습니다. |
| CA2214 | [CA2214: 재정의 가능한 메서드를 생성자에서 호출하지 마십시오.](../code-quality/ca2214.md) | 생성자가 가상 메서드를 호출할 때 이 메서드를 호출하는 인스턴스의 생성자가 실행되지 않았을 가능성이 있습니다. |
| CA2215 | [CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.](../code-quality/ca2215.md) | 삭제 가능한 형식으로부터 상속하는 형식은 자신의 Dispose 메서드에서 기본 형식의 Dispose 메서드를 호출해야 합니다. |
| CA2216 |[CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.](../code-quality/ca2216.md) | System.IDisposable을 구현하고, 관리되지 않는 리소스의 사용을 암시하는 필드를 포함하는 형식이 Object.Finalize에 설명된 대로 종료자를 구현하지 않습니다. |
| CA2217 | [CA2217: 열거형을 FlagsAttribute로 표시하지 마세요.](../code-quality/ca2217.md) |외부에서 볼 수 있는 열거형이 FlagsAttribute로 표시되어 있고, 2의 거듭제곱 또는 열거형에 정의된 다른 값의 조합이 아닌 값이 하나 이상 들어 있습니다. |
| CA2219 | [CA2219: exception 절에서 예외를 발생시키지 마세요.](../code-quality/ca2219.md) | finally 또는 fault 절에서 예외가 발생하는 경우 새 예외가 활성 예외를 숨깁니다. filter 절에서 예외가 발생하는 경우 런타임이 자동으로 예외를 catch합니다. 따라서 원래 오류를 감지하고 디버깅하기 어렵게 됩니다. |
| CA2225 | [CA2225: 연산자 오버로드에는 명명된 대체 항목이 있습니다.](../code-quality/ca2225.md) |연산자 오버로드가 감지되었으며 예상되는 이름의 대체 메서드를 찾을 수 없습니다. 명명된 대체 멤버는 해당 연산자와 동일한 기능에 액세스할 수 있도록 해주며, 오버로드된 연산자가 지원되지 않는 언어로 프로그래밍하는 개발자에게 제공됩니다. |
| CA2226 | [CA2226: 연산자에는 대칭 오버로드가 있어야 합니다.](../code-quality/ca2226.md) | 형식이 같음 연산자 또는 같지 않음 연산자를 구현하면서 그 반대 연산자를 구현하지 않습니다. |
| CA2227 |[CA2227: 컬렉션 속성은 읽기 전용이어야 합니다.](../code-quality/ca2227.md) |쓰기 가능한 컬렉션 속성을 통해 사용자는 컬렉션을 다른 컬렉션으로 바꿀 수 있습니다. 읽기 전용 속성은 컬렉션을 바꾸지 못하도록 하지만 개별 멤버를 설정하는 것은 여전히 가능합니다. |
| CA2229 | [CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229.md) | 이 규칙 위반 문제를 해결하려면 serialization 생성자를 구현합니다. 봉인 클래스의 경우에는 생성자를 private으로 만들고, 그 밖의 경우에는 protected로 만듭니다. |
| CA2231 | [CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.](../code-quality/ca2231.md) | 값 형식이 Object.Equals를 재정의하지만 같음 연산자를 구현하지 않습니다. |
| CA2234 | [CA2234: 문자열 대신 System.Uri 개체를 전달하세요.](../code-quality/ca2234.md) | 이름에 "uri", "URI", "urn", "URN", "url" 또는 "URL"이 포함된 문자열 매개 변수가 있는 메서드가 호출되었습니다. 메서드의 선언 형식에 System.Uri 매개 변수를 가진 해당 메서드 오버로드가 들어 있습니다. |
| CA2235 | [CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.](../code-quality/ca2235.md) | serialize할 수 없는 형식의 인스턴스 필드가 serialize할 수 있는 형식에 정의되었습니다. |
| CA2237 | [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237.md) | 공용 언어 런타임에서 serializable로 인식되도록 하려면 형식이 ISerializable 인터페이스 구현을 통해 사용자 지정 serialization 루틴을 사용하는 경우에도 형식을 SerializableAttribute 특성으로 표시해야 합니다. |
| CA2241 | [CA2241: 서식 지정 메서드에 올바른 인수를 제공하십시오.](../code-quality/ca2241.md) | System.String.Format에 전달된 format 인수에 각 개체 인수에 해당하는 형식 항목이 없거나 각 형식 항목에 해당하는 개체 인수가 없습니다. |
| CA2242 |[CA2242: NaN에 대해 정확하게 테스트하십시오.](../code-quality/ca2242.md) | 이 식은 Single.Nan 또는 Double.Nan에 대해 값을 테스트합니다. 값을 테스트하려면 Single.IsNan(Single) 또는 Double.IsNan(Double)을 사용합니다. |
| CA2243 |[CA2243: 특성 문자열 리터럴이 올바르게 구문 분석되어야 합니다.](../code-quality/ca2243.md) | 특성의 문자열 리터럴 매개 변수가 URL, GUID 또는 버전에 대해 구문을 올바르게 분석하지 않습니다. |
| CA2244 | [CA2244: 인덱싱된 요소의 초기화는 복제하면 안 됩니다.](../code-quality/ca2244.md) | 개체 이니셜라이저에 동일한 상수 인덱스를 사용 하는 두 개 이상의 인덱싱된 요소 이니셜라이저가 있습니다. 마지막 이니셜라이저가 아닌 모두 중복 됩니다. |
| CA2245 | [CA2245: 속성을 자체에 할당하지 마세요.](../code-quality/ca2245.md) | 속성이 실수로 자신에 게 할당 되었습니다. |
| CA2246 | [CA2246: 동일한 문에 기호 및 해당 멤버를 할당하지 마세요.](../code-quality/ca2246.md) | 동일한 문에서 기호와 해당 멤버, 즉 필드 또는 속성을 할당 하는 것은 권장 되지 않습니다. 멤버 액세스에서 할당 전 기호의 이전 값을 사용 하거나이 문의 할당에서 새 값을 사용 하기 위한 것은 분명 하지 않습니다. |
| CA2247 | [CA2247: Task Source 생성자에 전달 된 인수는 System.threading.tasks.taskcontinuationoptions enum이 아니라 TaskCreationOptions 열거형 이어야 합니다.](../code-quality/ca2247.md) | TaskTaskCreationOptions Source에는 기본 작업을 제어 하는 생성자와 작업에 저장 된 개체 상태를 사용 하는 생성자가 있습니다.  실수로 TaskCreationOptions 대신 System.threading.tasks.taskcontinuationoptions를 전달 하면 호출은 옵션을 state로 처리 합니다. |
| CA2248 | [CA2248: Enum.HasFlag에 올바른 enum 인수를 제공하세요.](../code-quality/ca2248.md) | 메서드 호출에 인수로 전달 된 열거형 형식이 호출 하는 `HasFlag` 열거형 형식과 다릅니다. |
| CA2249 | [CA2249: ‘String.IndexOf’ 대신 ‘String.Contains’ 사용 고려](../code-quality/ca2249.md) | 결과를 `string.IndexOf` 사용 하 여 부분 문자열의 존재 여부를 확인 하는 호출을로 바꿀 수 있습니다 `string.Contains` . |
| CA2300 | [CA2300: 안전하지 않은 역직렬 변환기 BinaryFormatter를 사용하지 마세요.](../code-quality/ca2300.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2301 | [CA2301: 먼저 BinaryFormatter.Binder를 설정하지 않고 BinaryFormatter.Deserialize를 호출하지 마세요.](../code-quality/ca2301.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2302 | [CA2302: BinaryFormatter.Deserialize를 호출하기 전에 BinaryFormatter.Binder가 설정되었는지 확인합니다.](../code-quality/ca2302.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2305 | [CA2305: 안전하지 않은 역직렬 변환기 LosFormatter를 사용하지 마세요.](../code-quality/ca2305.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2310 | [CA2310: 안전하지 않은 역직렬 변환기 NetDataContractSerializer를 사용하지 마세요.](../code-quality/ca2310.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2311 | [CA2311: 먼저 NetDataContractSerializer.Binder를 설정하지 않고 역직렬화하지 마세요.](../code-quality/ca2311.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2312 | [CA2312: 역직렬화하기 전에 NetDataContractSerializer.Binder를 설정해야 합니다.](../code-quality/ca2312.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2315 | [CA2315: 안전하지 않은 역직렬 변환기 ObjectStateFormatter를 사용하지 마세요.](../code-quality/ca2315.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2321 | [CA2321: SimpleTypeResolver를 사용하여 JavaScriptSerializer를 통해 역직렬화하지 마세요.](../code-quality/ca2321.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2322 | [CA2322: JavaScriptSerializer가 역직렬화하기 전에 SimpleTypeResolver로 초기화되지 않는지 확인하세요.](../code-quality/ca2322.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2326 | [CA2326: None 이외의 TypeNameHandling 값을 사용하지 마세요.](../code-quality/ca2326.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2327 | [CA2327: 안전하지 않은 JsonSerializerSettings를 사용하지 마세요.](../code-quality/ca2327.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2328 | [CA2328: JsonSerializerSettings가 안전한지 확인하세요.](../code-quality/ca2328.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2329 | [CA2329: 안전하지 않은 구성을 사용하여 JsonSerializer로 역직렬화하지 마세요.](../code-quality/ca2329.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2330 | [CA2330: 역직렬화할 때 JsonSerializer에 보안 구성이 있는지 확인하세요.](../code-quality/ca2330.md) | 안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. |
| CA2350 | [CA2350: DataTable.ReadXml()의 입력을 신뢰할 수 있는지 확인하세요.](ca2350.md) | 신뢰할 수 없는 입력으로를 deserialize 할 때 <xref:System.Data.DataTable> 공격자는 서비스 거부 공격을 수행할 악성 입력을 만들 수 있습니다. 알 수 없는 원격 코드 실행 취약점이 있을 수 있습니다. |
| CA2351 | [CA2351: DataSet.ReadXml()의 입력을 신뢰할 수 있는지 확인하세요.](ca2351.md) | 신뢰할 수 없는 입력으로를 deserialize 할 때 <xref:System.Data.DataSet> 공격자는 서비스 거부 공격을 수행할 악성 입력을 만들 수 있습니다. 알 수 없는 원격 코드 실행 취약점이 있을 수 있습니다. |
| CA2352 | [CA2352: 직렬화 가능 형식의 안전하지 않은 데이터 세트 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있습니다.](ca2352.md) | 로 표시 된 클래스 또는 구조체에 <xref:System.SerializableAttribute> <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable> 필드 또는 속성이 포함 되어 있고가 없는 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 경우 |
| CA2353 | [CA2353: 직렬화 가능 형식의 안전하지 않은 데이터 세트 또는 DataTable입니다.](ca2353.md) | XML serialization 특성 또는 데이터 계약 특성으로 표시 된 클래스 또는 구조체에 <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable> 필드 또는 속성이 포함 되어 있습니다. |
| CA2354 | [CA2354: 역직렬화된 개체 그래프의 안전하지 않은 데이터 세트 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있습니다.](ca2354.md) | Serialize 된로 deserialize <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> 하 고, 캐스트 된 형식의 개체 그래프에 또는가 포함 될 수 있습니다 <xref:System.Data.DataSet> <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: 역직렬화된 개체 그래프의 안전하지 않은 데이터 세트 또는 DataTable](ca2355.md) | 캐스팅 되거나 지정 된 형식의 개체 그래프에 또는가 포함 될 수 있는 경우 deserialize <xref:System.Data.DataSet> <xref:System.Data.DataTable> |
| CA2356 | [CA2356: 웹 deserialize 된 개체 그래프의 안전 하지 않은 데이터 집합 또는 DataTable](ca2356.md) | 또는를 사용 하는 메서드에 <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 또는를 참조할 수 있는 매개 변수가 있습니다 <xref:System.Data.DataSet> <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: DataSet.ReadXml()을 포함하는 자동 생성된 클래스가 신뢰할 수 없는 데이터와 함께 사용되지 않도록 하기](ca2361.md) | 신뢰할 수 없는 입력으로를 deserialize 할 때 <xref:System.Data.DataSet> 공격자는 서비스 거부 공격을 수행할 악성 입력을 만들 수 있습니다. 알 수 없는 원격 코드 실행 취약점이 있을 수 있습니다. |
| CA2362 | [CA2362: 자동 생성된 직렬화 가능 형식의 안전하지 않은 DataSet 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있음](ca2362.md) | 를 사용 하 여 신뢰할 수 없는 입력 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 을 deserialize 하 고 deserialize 된 개체 그래프에 또는가 포함 된 경우 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 공격자는 악의적인 페이로드를 만들어 원격 코드 실행 공격을 수행할 수 있습니다. |
| CA3001 | [CA3001: 코드에서 SQL 주입 취약점에 대해 검토합니다.](../code-quality/ca3001.md) | 신뢰할 수 없는 입력 및 SQL 명령으로 작업 하는 경우 SQL 삽입 공격에 유의 해야 합니다. SQL 삽입 공격은 악의적인 SQL 명령을 실행 하 여 응용 프로그램의 보안 및 무결성을 손상 시킬 수 있습니다. |
| CA3002 | [CA3002: 코드에서 XSS 취약점에 대해 검토합니다.](../code-quality/ca3002.md) | 웹 요청에서 신뢰할 수 없는 입력으로 작업할 때는 XSS (사이트 간 스크립팅) 공격에 주의 해야 합니다. XSS 공격은 신뢰할 수 없는 입력을 원시 HTML 출력에 삽입 하 여 공격자가 악의적인 스크립트를 실행 하거나 웹 페이지의 콘텐츠를 악의적으로 수정할 수 있도록 합니다. |
| CA3003 | [CA3003: 코드에서 파일 경로 삽입 취약성에 대해 검토합니다.](../code-quality/ca3003.md) | 웹 요청에서 신뢰할 수 없는 입력으로 작업 하는 경우 파일에 대 한 경로를 지정 하는 경우 사용자가 제어 하는 입력을 사용할 수 있습니다. |
| CA3004 | [CA3004: 코드에서 정보 공개 취약성에 대해 검토합니다.](../code-quality/ca3004.md) | 예외 정보를 공개 하면 공격자가 응용 프로그램의 내부 정보를 파악할 수 있으므로 공격자가 다른 취약점을 악용할 수 있습니다. |
| CA3006 | [CA3006: 코드에서 프로세스 명령 주입 취약점에 대해 검토합니다.](../code-quality/ca3006.md) | 신뢰할 수 없는 입력으로 작업 하는 경우 명령 삽입 공격에 유의 해야 합니다. 명령 삽입 공격은 서버와의 보안 및 무결성을 손상 시키는 기본 운영 체제에서 악성 명령을 실행할 수 있습니다. |
| CA3007 | [CA3007: 코드에서 오픈 리디렉션 취약점에 대해 검토합니다.](../code-quality/ca3007.md) | 신뢰할 수 없는 입력으로 작업 하는 경우 개방형 리디렉션 취약성에 유의 해야 합니다. 공격자는 오픈 리디렉션 취약성을 악용 하 여 합법적인 URL의 모양을 제공 하는 데 웹 사이트를 사용할 수 있지만, 의심 되는 방문자를 피싱 또는 기타 악성 웹 페이지로 리디렉션할 수 있습니다. |
| CA3008 | [CA3008: 코드에서 XPath 삽입 취약성에 대해 검토합니다.](../code-quality/ca3008.md) | 신뢰할 수 없는 입력으로 작업할 때는 XPath 삽입 공격에 유의 해야 합니다. 신뢰할 수 없는 입력을 사용 하 여 XPath 쿼리를 생성 하면 공격자가 쿼리를 악의적으로 조작 하 여 의도 하지 않은 결과를 반환 하 고 쿼리 된 XML의 콘텐츠를 공개할 수 있습니다. |
| CA3009 | [CA3009: 코드에서 XML 삽입 취약성에 대해 검토합니다.](../code-quality/ca3009.md) | 신뢰할 수 없는 입력으로 작업 하는 경우 XML 삽입 공격에 유의 해야 합니다. |
| CA3010 | [CA3010: 코드에서 XAML 삽입 취약성에 대해 검토합니다.](../code-quality/ca3010.md) | 신뢰할 수 없는 입력으로 작업 하는 경우 XAML 삽입 공격에 유의 해야 합니다. XAML은 개체 인스턴스화 및 실행을 직접적으로 나타내는 태그 언어입니다. 즉, XAML로 생성 된 요소는 시스템 리소스 (예: 네트워크 액세스 및 파일 시스템 IO)와 상호 작용할 수 있습니다. |
| CA3011 | [CA3011: 코드에서 DLL 삽입 취약성에 대해 검토합니다.](../code-quality/ca3011.md) | 신뢰할 수 없는 입력으로 작업할 때는 신뢰할 수 없는 코드를 로드 하는 것에 유의 해야 합니다. 웹 응용 프로그램이 신뢰할 수 없는 코드를 로드 하는 경우 공격자가 프로세스에 악성 Dll을 삽입 하 고 악성 코드를 실행할 수 있습니다. |
| CA3012 | [CA3012: 코드에서 regex 삽입 취약성에 대해 검토합니다.](../code-quality/ca3012.md) | 신뢰할 수 없는 입력으로 작업할 때는 regex 삽입 공격에 유의 해야 합니다. 공격자는 regex 주입을 사용 하 여 정규식을 악의적으로 수정 하거나 regex가 의도 하지 않은 결과와 일치 하도록 하거나 regex가 과도 한 CPU를 사용 하 여 서비스 거부 공격을 내릴 수 있습니다. |
| CA3061 | [CA3061: URL로 스키마를 추가하지 마세요.](../code-quality/ca3061.md) | 위험한 외부 참조를 유발할 수 있으므로 Add 메서드의 unsafe 오버 로드를 사용 하지 마세요. |
| CA3075 | [CA3075: DTD 처리가 안전하지 않습니다.](../code-quality/ca3075.md) | 안전하지 않은 DTDProcessing 인스턴스를 사용하거나 외부 엔터티 소스를 참조하면 파서는 신뢰할 수 없는 입력을 허용하고 공격자에게 중요 한 정보를 공개할 수 있습니다. |
| CA3076 | [CA3076: XSLT 스크립트 실행이 안전하지 않습니다.](../code-quality/ca3076.md) | .NET 응용 프로그램에서 비보안 방식에서 XSLT (Extensible Stylesheet Language) 변환 (XSLT)을 실행 하는 경우 프로세서는 공격자에 게 중요 한 정보를 노출 하 여 서비스 거부 및 사이트 간 공격을 유발할 수 있는 신뢰할 수 없는 URI 참조를 해결할 수 있습니다. |
| CA3077 | [CA3077: API 디자인, XML 문서 및 XML 텍스트 판독기의 처리가 안전하지 않습니다.](../code-quality/ca3077.md) | XMLDocument 및 XMLTextReader에서 파생된 API를 디자인할 경우 DtdProcessing에 주의해야 합니다. 외부 엔터티 소스를 참조하거나 확인할 때 안전하지 않은 DTDProcessing 인스턴스를 사용하거나 XML에서 안전하지 않은 값을 설정하면 정보가 공개될 수 있습니다. |
| CA3147 | [CA3147: ValidateAntiForgeryToken을 사용하여 동사 처리기를 표시하세요.](../code-quality/ca3147.md) | ASP.NET MVC 컨트롤러를 설계할 때 사이트 간 요청 위조 공격을 염두에 둘 수 있습니다. 교차 사이트 요청 위조 공격은 인증 된 사용자의 악성 요청을 ASP.NET MVC 컨트롤러로 보낼 수 있습니다. |
| CA5350 | [CA5350: 취약한 암호화 알고리즘을 사용하지 마세요.](../code-quality/ca5350.md) | 오늘날 여러 가지 이유로 약한 암호화 알고리즘 및 해시 함수가 사용되지만 데이터의 무결성과 기밀성을 보장하기 위해서는 이 방법을 사용하지 않아야 합니다. 이 규칙은 코드에 TripleDES, SHA1 또는 RIPEMD160 알고리즘이 있을 때 발생합니다.|
| CA5351 | [CA5351 끊어진 암호화 알고리즘 사용 안 함](../code-quality/ca5351.md) | 끊어진 암호화 알고리즘은 안전하지 않은 것으로 간주되므로 사용해서는 안 됩니다. 이 규칙은 코드에 MD5 해시 알고리즘 또는 DES나 RC2 암호화 알고리즘이 있을 때 트리거됩니다. |
| CA5358 | [CA5358: 안전하지 않은 암호화 모드를 사용하지 마세요.](../code-quality/ca5358.md) | 안전하지 않은 암호화 모드를 사용하지 마세요. |
| CA5359 | [CA5359 인증서 유효성 검사를 사용 하지 않도록 설정 안 함](../code-quality/ca5359.md) | 인증서는 서버의 id를 인증 하는 데 도움이 될 수 있습니다. 클라이언트는 서버 인증서의 유효성을 검사 하 여 요청이 원하는 서버로 전송 되도록 해야 합니다. ServerCertificateValidationCallback에서 항상를 반환 `true` 하는 경우 모든 인증서가 유효성 검사를 통과 합니다. |
| CA5360 | [CA5360는 deserialization에서 위험한 메서드를 호출 하지 않습니다.](../code-quality/ca5360.md) | 안전 하지 않은 deserialization은 신뢰할 수 없는 데이터를 사용 하 여 응용 프로그램의 논리를 남용 하거나, DoS (서비스 거부) 공격을 수행 하거나, deserialize 될 때 임의의 코드를 실행할 때 발생 하는 취약성입니다. 응용 프로그램에서 제어 하는 신뢰할 수 없는 데이터를 deserialize 하는 경우 악의적인 사용자가 이러한 deserialization 기능을 악용할 수 있습니다. 특히 deserialization 프로세스에서 위험한 메서드를 호출 합니다. 안전 하지 않은 deserialization 공격에 성공 하면 공격자가 DoS 공격, 인증 바이패스 및 원격 코드 실행과 같은 공격을 수행할 수 있습니다. |
| CA5361 | [CA5361: 강력한 암호의 SChannel 사용을 비활성화하지 마세요.](../code-quality/ca5361.md) | `Switch.System.Net.DontEnableSchUseStrongCrypto`를로 설정 `true` 하면 weakens TLS (전송 계층 보안) 연결에 사용 되는 암호화가 사용 됩니다. 약한 암호화는 응용 프로그램과 서버 간 통신의 기밀성을 손상 시켜 공격자가 중요 한 데이터를 보다 쉽게 도청 수 있도록 합니다. |
| CA5362 | [Deserialize 된 개체 그래프에서 잠재적 참조 주기 CA5362](../code-quality/ca5362.md) | 신뢰할 수 없는 데이터를 deserialize 하는 경우 deserialize 된 개체 그래프를 처리 하는 모든 코드는 무한 루프로 이동 하지 않고 참조 주기를 처리 해야 합니다. 여기에는 deserialization 콜백의 일부인 코드와 deserialization 완료 후 개체 그래프를 처리 하는 코드가 모두 포함 됩니다. 그렇지 않으면 공격자가 참조 주기를 포함 하는 악성 데이터를 사용 하 여 서비스 거부 공격을 수행할 수 있습니다. |
| CA5363 | [CA5363: 요청 유효성 검사를 사용하지 않도록 설정하지 마세요.](../code-quality/ca5363.md) | 요청 유효성 검사는 HTTP 요청을 검사 하 고 사이트 간 스크립팅을 포함 하 여 삽입 공격으로 이어질 수 있는 잠재적으로 위험한 콘텐츠가 포함 되어 있는지 여부를 확인 하는 ASP.NET의 기능입니다. |
| CA5364 | [CA5364: 사용되지 않는 보안 프로토콜을 사용하지 마세요.](../code-quality/ca5364.md) | TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다. |
| CA5365 | [CA5365 HTTP 헤더 검사를 사용 하지 않도록 설정 안 함](../code-quality/ca5365.md) | HTTP 헤더 검사는 응답 헤더에 있는 캐리지 리턴 및 줄 바꿈 문자 (\r 및 \n)의 인코딩을 사용할 수 있도록 합니다. 이 인코딩 헤더에 포함 된 신뢰할 수 없는 데이터를 표시 하는 애플리케이션을 악용 하는 삽입 공격을 방지 하는 데 도움이 됩니다. |
| CA5366 | [CA5366 데이터 집합에 XmlReader를 사용 하 여 XML 읽기](../code-quality/ca5366.md) | 를 사용 하 여 <xref:System.Data.DataSet> 신뢰할 수 없는 데이터가 있는 XML을 읽으면 <xref:System.Xml.XmlReader> 보안 해결 프로그램을 사용 하거나 DTD 처리를 사용할 수 없는를 사용 하 여 제한 해야 하는 위험한 외부 참조가 로드 될 수 있습니다. |
| CA5367 | [CA5367는 포인터 필드를 사용 하 여 형식을 직렬화 하지 않습니다.](../code-quality/ca5367.md) | 이 규칙은 포인터 필드 또는 속성이 있는 serializable 클래스가 있는지 여부를 확인 합니다. Serialize 할 수 없는 멤버는 정적 멤버 또는로 표시 된 필드와 같은 포인터 일 수 있습니다 <xref:System.NonSerializedAttribute> . |
| CA5368 | [페이지에서 파생 된 클래스에 대 한 CA5368 Set ViewStateUserKey](../code-quality/ca5368.md) | 속성을 설정 하면 공격자가 변수를 사용 하 여 <xref:System.Web.UI.Page.ViewStateUserKey> 공격을 생성할 수 없도록 개별 사용자의 뷰 상태 변수에 식별자를 할당할 수 있으므로 응용 프로그램에 대 한 공격을 방지할 수 있습니다. 그렇지 않으면 교차 사이트 요청 위조에 대 한 취약성이 있습니다. |
| CA5369 | [CA5369: 역직렬화에 XmlReader를 사용하세요.](../code-quality/ca5369.md) | 신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 해야 하는 위험한 외부 참조를 로드할 수 있습니다. |
| CA5370 | [CA5370: 판독기 유효성 검사에 XmlReader를 사용하세요.](../code-quality/ca5370.md) | 신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 이 위험한 로드는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 하 여 제한할 수 있습니다. |
| CA5371 | [CA5371: 스키마 읽기에 XmlReader를 사용하세요.](../code-quality/ca5371.md) | 신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 보안 해결 프로그램을 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않는 XmlReader를 사용 하면이이 제한 됩니다. |
| CA5372 | [CA5372: XPathDocument에 XmlReader를 사용하세요.](../code-quality/ca5372.md) | 신뢰할 수 없는 데이터에서 XML을 처리 하면 위험한 외부 참조가 로드 될 수 있으며,이는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 처리를 사용 하지 않도록 설정할 수 있습니다. |
| CA5373 | [CA5373: 사용되지 않는 키 파생 함수를 사용하지 마세요.](../code-quality/ca5373.md) | 이 규칙은 약한 키 파생 메서드 및의 호출을 검색 합니다 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 약한 알고리즘 PBKDF1을 사용 했습니다. |
| CA5374 | [CA5374 XslTransform 사용 안 함](../code-quality/ca5374.md) | 이 규칙 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 은가 코드에서 인스턴스화되어 있는지 확인 합니다. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 는 이제 사용 되지 않으며 사용할 수 없습니다. |
| CA5375 | [CA5375 계정 공유 액세스 서명 사용 안 함](../code-quality/ca5375.md) | 계정 SAS는 서비스 SAS로 허용 되지 않는 blob 컨테이너, 테이블, 큐 및 파일 공유에 대 한 읽기, 쓰기 및 삭제 작업에 대 한 액세스를 위임할 수 있습니다. 그러나 컨테이너 수준 정책을 지원 하지 않으며 부여 된 사용 권한에 대 한 유연성과 제어 수준이 낮습니다. 악의적인 사용자가이를 가져오면 저장소 계정이 쉽게 손상 됩니다. |
| CA5376 | [CA5376 SharedAccessProtocol HttpsOnly 사용](../code-quality/ca5376.md) | SAS는 HTTP에서 일반 텍스트로 전송할 수 없는 중요 한 데이터입니다. |
| CA5377 | [컨테이너 수준 액세스 정책을 사용 하는 CA5377](../code-quality/ca5377.md) | 컨테이너 수준 액세스 정책은 언제 든 지 수정 하거나 취소할 수 있습니다. 이를 통해 부여 되는 사용 권한을 보다 유연 하 게 제어할 수 있습니다. |
| CA5378 | [CA5378: ServicePointManagerSecurityProtocols를 비활성화하지 마세요.](../code-quality/ca5378.md) | `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`로 설정 `true` 하면 Windows Communication FRAMEWORK의 Tls (전송 계층 보안) 연결을 tls 1.0을 사용 하도록 제한 합니다. 해당 버전의 TLS는 더 이상 사용 되지 않습니다. |
| CA5379 | [CA5379 약한 키 파생 함수 알고리즘 사용 안 함](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>클래스는 기본적으로 알고리즘을 사용 <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> 합니다. 이상에서 생성자의 일부 오버 로드에 사용할 해시 알고리즘을 지정 해야 합니다 <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> . 속성에는 <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> 접근자만 있으며 `get` 한정자가 없습니다 `overriden` . |
| CA5380 | [CA5380: 루트 저장소에 인증서를 추가하지 마세요.](../code-quality/ca5380.md) | 이 규칙은 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca 집합을 사용 하 여 구성 됩니다. |
| CA5381 | [CA5381: 인증서가 루트 저장소에 추가되지 않았는지 확인하세요.](../code-quality/ca5381.md) | 이 규칙은 잠재적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca (인증 기관) 집합으로 구성 됩니다. |
| CA5382 | [ASP.NET Core에서 보안 쿠키 사용 CA5382](../code-quality/ca5382.md) | HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 쿠키가 SSL(Secure Sockets Layer) (SSL)를 사용 하 여 전송 되어야 함을 브라우저에 표시 합니다. |
| CA5383 | [ASP.NET Core에서 보안 쿠키를 사용 하도록 CA5383](../code-quality/ca5383.md) | HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 쿠키가 SSL(Secure Sockets Layer) (SSL)를 사용 하 여 전송 되어야 함을 브라우저에 표시 합니다. |
| CA5384 | [CA5384 DSA (디지털 서명 알고리즘)를 사용 하지 않음](../code-quality/ca5384.md) | DSA는 약한 비대칭 암호화 알고리즘입니다. |
| CA5385 | [CA5385 Use Rivest – Rivest-shamir-adleman – Rivest-shamir-adleman (RSA) algorithm 키 크기가 충분 합니다.](../code-quality/ca5385.md) | 2048 비트 보다 작은 RSA 키는 무차별 암호 대입 공격에 보다 취약 합니다. |
| CA5386 | [CA5386: SecurityProtocolType 값을 하드 코딩하지 마세요.](../code-quality/ca5386.md) | TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램의 보안을 유지 하려면 프로토콜 버전을 하드 코딩 하지 않고 .NET Framework v 4.7.1 이상을 대상으로 해야 합니다. |
| CA5387 | [CA5387 충분 하지 않은 반복 횟수로 약한 키 파생 함수를 사용 하지 않음](../code-quality/ca5387.md) | 이 규칙은 암호화 키가 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다. |
| CA5388 | [약한 키 파생 함수를 사용 하는 경우 충분 한 반복 횟수 확인 CA5388](../code-quality/ca5388.md) | 이 규칙은 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 암호화 키가 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다. |
| CA5389 | [CA5389: 대상 파일 시스템 경로에 보관 항목의 경로를 추가하지 마세요.](../code-quality/ca5389.md) | 파일 경로는 상대적일 수 있으며, 예상 된 파일 시스템 대상 경로 외부에서 파일 시스템에 액세스할 수 있으며,이로 인해 악의적인 구성 변경 내용 및 대기 방식 기술을 통해 원격 코드를 실행할 수 있습니다. |
| CA5390 | [CA5390 암호화 키를 하드 코딩 하지 않음](../code-quality/ca5390.md) | 대칭 알고리즘을 성공적으로 수행 하려면 비밀 키를 발신자와 수신자 에게만 인식 해야 합니다. 키가 하드 코드 되 면 쉽게 검색 됩니다. 컴파일된 이진 파일의 경우에도 악의적인 사용자가 쉽게 추출할 수 있습니다. 개인 키가 손상 되 면 암호화 텍스트를 직접 해독 하 여 더 이상 보호할 수 없습니다. |
| CA5391 | [ASP.NET Core MVC 컨트롤러에서 위조 방지 토큰 CA5391 사용](../code-quality/ca5391.md) | `POST` `PUT` `PATCH` `DELETE` 위조 방지 토큰의 유효성을 검사 하지 않고,, 또는 요청을 처리 하면 교차 사이트 요청 위조 공격에 취약할 수 있습니다. 사이트 간 요청 위조 공격은 인증 된 사용자의 악성 요청을 ASP.NET Core MVC 컨트롤러로 보낼 수 있습니다. |
| CA5392 | [P/Invoke에 대 한 CA5392 Use DefaultDllImportSearchPaths 특성](../code-quality/ca5392.md) | 기본적으로 P/Invoke 함수는 <xref:System.Runtime.InteropServices.DllImportAttribute> 로드 하는 라이브러리에 대 한 현재 작업 디렉터리를 포함 하 여 많은 디렉터리를 검색 합니다. 이는 특정 응용 프로그램에 대 한 보안 문제 이며 DLL 하이재킹이 될 수 있습니다. |
| CA5393 | [CA5393 unsafe DllImportSearchPath value 사용 안 함](../code-quality/ca5393.md) | 기본 DLL 검색 디렉터리와 어셈블리 디렉터리에 악성 DLL이 있을 수 있습니다. 또는 응용 프로그램이 실행 되는 위치에 따라 응용 프로그램 디렉터리에 악성 DLL이 있을 수 있습니다. |
| CA5394 | [CA5394은 안전 하지 않은 임의성을 사용 하지 않습니다.](../code-quality/ca5394.md) | 공격자는 암호화 된 약한 의사 난수 생성기를 사용 하 여 보안에 중요 한 값이 생성 되는 것을 예측할 수 있습니다. |
| CA5395 | [작업 메서드에 대 한 CA5395 누락 HttpVerb 특성](../code-quality/ca5395.md) | 데이터를 만들거나 편집, 삭제 또는 수정 하는 모든 작업 메서드는 사이트 간 요청 위조 공격 으로부터 위조 방지 특성으로 보호 해야 합니다. GET 작업을 수행 하는 것은 부작용이 없으며 지속형 데이터를 수정 하지 않는 안전 작업 이어야 합니다. |
| CA5396 | [되어에 대해 CA5396를 true로 설정 합니다.](../code-quality/ca5396.md) | 심층 방어 수단으로 보안에 민감한 HTTP 쿠키가 HttpOnly로 표시 되어 있는지 확인 합니다. 이는 웹 브라우저에서 스크립트가 쿠키에 액세스 하지 못하도록 하는 것을 의미 합니다. 삽입 된 악성 스크립트는 쿠키를 도용 하는 일반적인 방법입니다. |
| CA5397 | [CA5397: 사용되지 않는 SslProtocols 값을 사용하지 마세요.](../code-quality/ca5397.md) | TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다. |
| CA5398 | [CA5398: SslProtocols 값을 하드 코딩하지 마세요.](../code-quality/ca5398.md) | TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램이 안전 하 게 유지 되도록 하려면 프로토콜 버전을 하드 코딩 하지 마십시오. |
| CA5399 | [CA5399 = HttpClient 인증서 해지 목록 확인](../code-quality/ca5399.md) | 해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다. |
| CA5400 | [CA5400 HttpClient 인증서 해지 목록 확인이 사용 하도록 설정 되지 않았는지 확인 합니다.](../code-quality/ca5400.md) | 해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다. |
| CA5401 | [CA5401는 기본값이 아닌 IV와 함께 CreateEncryptor를 사용 하지 않습니다.](../code-quality/ca5401.md) | 대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다. |
| CA5402 | [CA5402는 기본 IV와 함께 CreateEncryptor를 사용 합니다.](../code-quality/ca5402.md) | 대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다. |
| CA5403 | [CA5403: 인증서 하드 코딩 안 함](../code-quality/ca5403.md) | `data` `rawData` 또는 생성자의 또는 매개 변수는 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 하드 코드 되어 있습니다. |
| IL3000 | [단일 파일로 게시할 때 어셈블리 파일 경로에 액세스 하지 IL3000](../code-quality/il3000.md) | 단일 파일로 게시할 때 어셈블리 파일 경로 액세스를 사용 하지 마십시오. |
| IL3001 | [단일 파일로 게시할 때 어셈블리 파일 경로에 액세스 하지 IL3001](../code-quality/il3001.md) | 단일 파일로 게시할 때 어셈블리 파일 경로에 액세스 하지 않습니다. |
