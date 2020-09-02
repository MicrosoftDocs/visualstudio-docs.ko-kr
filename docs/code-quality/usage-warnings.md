---
title: 사용법 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66d78988ef70e4f991dd02cb16a164cbf48e55f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176080"
---
# <a name="usage-warnings"></a>사용법 경고

사용 경고는 .NET의 적절 한 사용을 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1801: 사용되지 않은 매개 변수를 검토하세요.](../code-quality/ca1801.md)|메서드 시그니처에 메서드 본문에서 사용되지 않는 매개 변수가 있습니다.|
|[CA1806: 메서드 결과를 무시하지 마세요.](../code-quality/ca1806.md)|새 개체가 만들어지지만 사용되지 않거나, 새 문자열을 만들고 반환하는 메서드가 호출되고 새 문자열이 사용되지 않거나, COM 또는 P/Invoke 메서드가 사용되지 않는 오류 코드나 HRESULT를 반환합니다.|
|[CA1816: GC.SuppressFinalize를 올바르게 호출하세요.](../code-quality/ca1816.md)|Dispose 구현인 메서드가 GC를 호출 하지 않습니다. SuppressFinalize; 또는 Dispose 구현 되지 않는 메서드가 GC를 호출 합니다. SuppressFinalize; 또는 GC를 호출 합니다. SuppressFinalize 및 전달이 (Visual Basic의 Me) 이외의 것입니다.|
|[CA2200: 스택 정보를 유지하도록 다시 throw하십시오.](../code-quality/ca2200.md)|예외가 다시 throw되며 예외가 throw 문에 명시적으로 지정되어 있습니다. throw 문에 예외를 지정하여 예외가 다시 throw되면 예외를 throw한 원래 메서드와 현재 메서드 간의 메서드 호출 목록이 손실됩니다.|
|[CA2201: 예약된 예외 형식을 발생시키지 마세요.](../code-quality/ca2201.md)|이렇게 하면 원래 오류를 검색 하 고 디버그 하기가 어렵습니다.|
|[CA2202: 개체를 여러 번 삭제하지 마십시오.](../code-quality/ca2202.md)|같은 개체에 대해 System.IDisposable.Dispose 또는 Dispose와 동일한 기능의 메서드(예를 들어, 일부 형식의 Close() 메서드)가 여러 번 호출될 수 있는 코드 경로가 메서드 구현에 포함되어 있습니다.|
|[CA2204: 리터럴의 맞춤법이 정확해야 합니다.](../code-quality/ca2204.md)|메서드 본문의 리터럴 문자열에 Microsoft 맞춤법 검사 라이브러리에서 인식하지 못하는 단어가 하나 이상 있습니다.|
|[CA2205: Win32 API의 동일한 관리형 기능을 사용하세요.](../code-quality/ca2205.md)|플랫폼 호출 메서드가 정의 되 고 해당 기능을 사용 하는 .NET 메서드를 사용할 수 있습니다.|
|[CA2207: 값 형식 정적 필드 인라인을 초기화하십시오.](../code-quality/ca2207.md)|값 형식에서 명시적인 정적 생성자를 선언합니다. 이 규칙 위반 문제를 해결하려면 모든 정적 데이터를 선언할 때 초기화하고 정적 생성자를 제거합니다.|
|[CA2208: 인수 예외를 올바르게 인스턴스화하세요.](../code-quality/ca2208.md)|ArgumentException 또는 ArgumentException에서 파생된 예외 형식의 기본(매개 변수가 없는) 생성자를 호출했거나, ArgumentException 또는 ArgumentException에서 파생된 예외 형식의 매개 변수가 있는 생성자에 잘못된 문자열 인수가 전달되었습니다.|
|[CA2211: 비상수 필드는 노출되면 안 됩니다.](../code-quality/ca2211.md)|상수 또는 읽기 전용 정적 필드는 스레드로부터 안전 하지 않습니다. 이러한 필드에 대 한 액세스는 신중 하 게 제어 해야 하며 클래스 개체에 대 한 액세스를 동기화 하기 위한 고급 프로그래밍 기술이 필요 합니다.|
|[CA2212: 서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.](../code-quality/ca2212.md)|System.enterpriseservices에서 상속 되는 형식의 메서드는 WebMethodAttribute로 표시 됩니다.. WebMethodAttribute 및 ServicedComponent 메서드에는 컨텍스트와 트랜잭션 흐름에 있어 충돌하는 동작 및 요구 사항이 있으므로 메서드의 동작이 일부 시나리오에서 잘못됩니다.|
|[CA2213: 삭제 가능한 필드는 삭제해야 합니다.](../code-quality/ca2213.md)|System.IDisposable을 구현하는 형식이 마찬가지로 IDisposable을 구현하는 형식으로 된 필드를 선언합니다. 필드의 Dispose 메서드가 선언 형식의 Dispose 메서드에 의해 호출되지 않습니다.|
|[CA2214: 재정의 가능한 메서드를 생성자에서 호출하지 마십시오.](../code-quality/ca2214.md)|생성자가 가상 메서드를 호출 하는 경우 메서드를 호출 하는 인스턴스에 대 한 생성자가 실행 되지 않았을 수 있습니다.|
|[CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.](../code-quality/ca2215.md)|삭제 가능한 형식으로부터 상속하는 형식은 자신의 Dispose 메서드에서 기본 형식의 Dispose 메서드를 호출해야 합니다.|
|[CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.](../code-quality/ca2216.md)|System.string을 구현 하 고 관리 되지 않는 리소스의 사용을 제안 하는 필드를 포함 하는 형식입니다. Finalize에 설명 된 대로 종료자를 구현 하지 않습니다.|
|[CA2217: 열거형을 FlagsAttribute로 표시하지 마세요.](../code-quality/ca2217.md)|외부에서 볼 수 있는 열거형은 FlagsAttribute로 표시 되 고, 두의 거듭제곱이 아닌 하나 이상의 값 또는 열거형에 정의 된 다른 값의 조합이 있습니다.|
|[CA2218: Equals를 재정할 때 GetHashCode를 재정의하세요.](../code-quality/ca2218.md)|GetHashCode는 현재 인스턴스를 기반으로 해싱 알고리즘 및 해시 테이블과 같은 데이터 구조체에 적합한 값을 반환합니다. 형식이 같은 동일한 두 개체는 동일한 해시 코드를 반환해야 합니다.|
|[CA2219: exception 절에서 예외를 발생시키지 마세요.](../code-quality/ca2219.md)|finally 또는 fault 절에서 예외가 발생하는 경우 새 예외가 활성 예외를 숨깁니다. filter 절에서 예외가 발생하는 경우 런타임이 자동으로 예외를 catch합니다. 이렇게 하면 원래 오류를 검색 하 고 디버그 하기가 어렵습니다.|
|[CA2220: 종료자는 기본 클래스 종료자를 호출해야 합니다.](../code-quality/ca2220.md)|종료는 상속 계층을 통해 전파되어야 합니다. 이를 위해 형식은 자체 Finalize 메서드에서 기본 클래스의 Finalize 메서드를 호출해야 합니다.|
|[CA2221: 종료자는 protected여야 합니다.](../code-quality/ca2221.md)|종료자에서는 패밀리 액세스 한정자를 사용해야 합니다.|
|[CA2222: 상속된 멤버 노출 수준을 낮추지 마세요.](../code-quality/ca2222.md)|상속 된 멤버의 액세스 한정자를 변경 하지 마세요. 상속된 멤버를 private으로 변경하더라도 호출자가 메서드의 기본 클래스 구현에 액세스하는 것을 막을 수 없습니다.|
|[CA2223: 멤버는 반환 형식 이외의 것도 달라야 합니다.](../code-quality/ca2223.md)|공용 언어 런타임에서는 반환 값만 다르고 다른 면에서는 동일한 멤버를 구분할 수 있지만 이 기능은 공용 언어 사양에 해당되지 않으며 .NET 프로그래밍 언어의 공통 기능이 아닙니다.|
|[CA2224: 같음 연산자를 오버로드할 때 Equals를 재정의하세요.](../code-quality/ca2224.md)|Public 형식이 같음 연산자를 구현 하지만 개체. Equals를 재정의 하지 않습니다.|
|[CA2225: 연산자 오버로드에는 명명된 대체 항목이 있습니다.](../code-quality/ca2225.md)|연산자 오버로드가 감지되었으며 예상되는 이름의 대체 메서드를 찾을 수 없습니다. 명명 된 대체 멤버는 연산자와 같은 기능에 대 한 액세스를 제공 하며 오버 로드 된 연산자를 지원 하지 않는 언어로 프로그래밍 하는 개발자를 위해 제공 됩니다.|
|[CA2226: 연산자에는 대칭 오버로드가 있어야 합니다.](../code-quality/ca2226.md)|형식은 같음 또는 같지 않음 연산자를 구현 하며, 반대 연산자를 구현 하지 않습니다.|
|[CA2227: 컬렉션 속성은 읽기 전용이어야 합니다.](../code-quality/ca2227.md)|쓰기 가능한 컬렉션 속성을 통해 사용자는 컬렉션을 다른 컬렉션으로 바꿀 수 있습니다. 읽기 전용 속성은 컬렉션을 바꾸지 못하도록 하지만 개별 멤버를 설정하는 것은 여전히 가능합니다.|
|[CA2228: 릴리스되지 않은 리소스 형식을 제공하지 마세요.](../code-quality/ca2228.md)|.NET의 시험판 버전을 사용 하 여 빌드된 리소스 파일은 지원 되는 버전의 .NET에서 사용 하지 못할 수 있습니다.|
|[CA2229: serialization 생성자를 구현하십시오.](../code-quality/ca2229.md)|이 규칙 위반 문제를 해결하려면 serialization 생성자를 구현합니다. 봉인 클래스의 경우에는 생성자를 private으로 만들고, 그 밖의 경우에는 protected로 만듭니다.|
|[CA2230: 가변 인수로 params를 사용하세요.](../code-quality/ca2230.md)|public 또는 protected 형식에 params 키워드 대신 VarArgs 호출 규칙을 사용하는 public 또는 protected 메서드가 들어 있습니다.|
|[CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.](../code-quality/ca2231.md)|값 형식이를 재정의 `Object.Equals` 하지만 같음 연산자를 구현 하지 않습니다.|
|[CA2232: Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.](../code-quality/ca2232.md)|STAThreadAttribute는 애플리케이션에 대한 COM 스레딩 모델이 단일 스레드 아파트임을 나타냅니다. 이 특성은 Windows Forms을 사용하는 애플리케이션의 진입점에 있어야 합니다. 이 특성을 생략하면 Windows 구성 요소가 제대로 작동하지 않을 수 있습니다.|
|[CA2233: 연산은 오버플로되지 않아야 합니다.](../code-quality/ca2233.md)|연산 결과가 관련 데이터 형식에 대해 가능한 값의 범위를 벗어나지 않도록 하려면 먼저 피연산자의 유효성을 검사 하지 않고 산술 연산을 수행 하면 안 됩니다.|
|[CA2234: 문자열 대신 System.Uri 개체를 전달하세요.](../code-quality/ca2234.md)|이름에 "uri", "URI", "urn", "URN", "url" 또는 "URL"이 포함된 문자열 매개 변수가 있는 메서드가 호출되었습니다.  메서드의 선언 형식에 System.Uri 매개 변수를 가진 해당 메서드 오버로드가 들어 있습니다.|
|[CA2235: 모두 serialize할 수 없는 필드로 표시하십시오.](../code-quality/ca2235.md)|serialize할 수 없는 형식의 인스턴스 필드가 serialize할 수 있는 형식에 정의되었습니다.|
|[CA2236: ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.](../code-quality/ca2236.md)|이 규칙 위반 문제를 해결하려면 해당하는 파생된 형식의 메서드나 생성자에서 기본 형식 GetObjectData 메서드나 serialization 생성자를 호출합니다.|
|[CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237.md)|공용 언어 런타임에서 serializable로 인식할 수 있도록 형식에서 ISerializable 인터페이스 구현을 통해 사용자 지정 serialization 루틴을 사용 하는 경우에도 형식을 SerializableAttribute 특성으로 표시 해야 합니다.|
|[CA2238: serialization 메서드를 올바르게 구현하십시오.](../code-quality/ca2238.md)|serialization 이벤트를 처리하는 메서드에 올바른 시그니처, 반환 형식 또는 노출 수준이 없습니다.|
|[CA2239: 선택적 필드에 deserialization 메서드를 제공하세요.](../code-quality/ca2239.md)|형식에 OptionalFieldAttribute 특성으로 표시 된 필드가 있으며,이 형식은 역직렬화 이벤트 처리 메서드를 제공 하지 않습니다.|
|[CA2240: ISerializable을 올바르게 구현하십시오.](../code-quality/ca2240.md)|이 규칙 위반 문제를 해결 하려면 GetObjectData 메서드를 표시 하 고 재정의 가능 하 게 설정 하 고 모든 인스턴스 필드가 serialization 프로세스에 포함 되거나 명시적으로 NonSerializedAttribute 특성으로 표시 되어 있는지 확인 합니다.|
|[CA2241: 서식 지정 메서드에 올바른 인수를 제공하십시오.](../code-quality/ca2241.md)|System.string에 전달 된 format 인수에 각 개체 인수에 해당 하는 형식 항목이 포함 되어 있지 않거나 그 반대의 경우도 마찬가지입니다.|
|[CA2242: NaN에 대해 정확하게 테스트하십시오.](../code-quality/ca2242.md)|이 식은 Single.Nan 또는 Double.Nan에 대해 값을 테스트합니다. 값을 테스트하려면 Single.IsNan(Single) 또는 Double.IsNan(Double)을 사용합니다.|
|[CA2243: 특성 문자열 리터럴이 올바르게 구문 분석되어야 합니다.](../code-quality/ca2243.md)|특성의 문자열 리터럴 매개 변수는 URL, GUID 또는 버전에 대해 올바르게 구문 분석 되지 않습니다.|
|[CA2244: 인덱싱된 요소의 초기화는 복제하면 안 됩니다.](../code-quality/ca2244.md)|개체 이니셜라이저에 동일한 상수 인덱스를 사용 하는 두 개 이상의 인덱싱된 요소 이니셜라이저가 있습니다. 마지막 이니셜라이저가 아닌 모두 중복 됩니다.|
|[CA2245: 속성을 자체에 할당하지 마세요.](../code-quality/ca2245.md)|속성이 실수로 자신에 게 할당 되었습니다.|
|[CA2246: 동일한 문에 기호 및 해당 멤버를 할당하지 마세요.](../code-quality/ca2246.md)|동일한 문에서 기호와 해당 멤버, 즉 필드 또는 속성을 할당 하는 것은 권장 되지 않습니다. 멤버 액세스에서 할당 전 기호의 이전 값을 사용 하거나이 문의 할당에서 새 값을 사용 하기 위한 것은 분명 하지 않습니다.|
|[CA2247: TaskCompletionSource 생성자로 전달된 인수는 TaskContinuationOptions 열거형이 아닌 TaskCreationOptions 열거형이어야 합니다.](../code-quality/ca2246.md)|TaskTaskCreationOptions Source에는 기본 작업을 제어 하는 생성자와 작업에 저장 된 개체 상태를 사용 하는 생성자가 있습니다.  실수로 TaskCreationOptions 대신 System.threading.tasks.taskcontinuationoptions를 전달 하면 호출은 옵션을 state로 처리 합니다.|
|[CA2248: ' Enum. HasFlag '에 올바른 ' enum ' 인수를 제공 하십시오.](../code-quality/ca2248.md)|메서드 호출에 인수로 전달 된 열거형 형식이 호출 하는 `HasFlag` 열거형 형식과 다릅니다.|
|[CA2249: ‘String.IndexOf’ 대신 ‘String.Contains’ 사용 고려](../code-quality/ca2249.md)|결과를 `string.IndexOf` 사용 하 여 부분 문자열의 존재 여부를 확인 하는 호출을로 바꿀 수 있습니다 `string.Contains` .|
