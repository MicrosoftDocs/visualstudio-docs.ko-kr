---
title: 디자인 경고 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.designrules
helpviewer_keywords:
- design warnings
- managed code analysis warnings, design warnings
- warnings, design
ms.assetid: 34e65a18-560c-423f-814f-519089e318cf
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 16b44304dbfed49a72a19a15229f3e4754e0573e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667656"
---
# <a name="design-warnings"></a>디자인 경고
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디자인 경고는 .NET Framework 디자인 지침을 준수 하도록 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|제네릭 형식의 정적 멤버를 호출할 때는 형식에 형식 인수를 지정해야 합니다. 유추를 지원하지 않는 제네릭 인스턴스 멤버를 호출할 때는 멤버에 형식 인수를 지정해야 합니다. 이 두 가지 경우에 형식 인수를 지정하기 위한 구문은 서로 다르며 혼동되기 쉽습니다.|
|[CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|클래스는 system.string 형식이 고 클래스에서 IDisposable을 구현 하지 않는 인스턴스 필드를 선언 하 고 구현 합니다. IDisposable 필드를 선언하는 클래스는 관리되지 않는 리소스를 간접적으로 소유하며 IDisposable 인터페이스를 구현해야 합니다.|
|[CA1002: 제네릭 목록을 노출하지 마세요.](../code-quality/ca1002-do-not-expose-generic-lists.md)|< (Of \<(T> ) >)는 상속이 아닌 성능을 위해 디자인 된 제네릭 컬렉션입니다. 따라서 List에는 가상 멤버가 포함되지 않습니다. 상속을 위해 디자인된 제네릭 컬렉션이 대신 노출되어야 합니다.|
|[CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하세요.](../code-quality/ca1003-use-generic-event-handler-instances.md)|형식에 void를 반환 하는 대리자가 포함 되어 있습니다. 해당 시그니처에는 두 개의 매개 변수 (첫 번째 개체와 EventArgs에 할당할 수 있는 두 번째 형식)와 포함 하는 어셈블리 대상이 포함 됩니다 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .|
|[CA1004: 제네릭 메서드는 형식 매개 변수를 제공해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|제네릭 메서드의 형식 인수가 형식 인수를 명시적으로 지정하는 대신 메서드로 전달된 인수의 형식에 따라 결정되는 방식을 유추라고 합니다. 유추를 사용하려면 제네릭 메서드의 매개 변수 시그니처에 메서드에 대한 형식 매개 변수와 같은 형식의 매개 변수가 포함되어야 합니다. 이 경우 형식 인수는 지정할 필요가 없습니다. 모든 형식 매개 변수에 대해 유추를 사용 하는 경우 제네릭 및 제네릭이 아닌 인스턴스 메서드를 호출 하는 구문은 동일 합니다. 이렇게 하면 제네릭 메서드의 유용성이 간소화 됩니다.|
|[CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|제네릭 형식에 포함된 형식 매개 변수가 많을수록 각 형식 매개 변수가 무엇을 나타내는지를 파악하거나 기억하기가 더 어렵습니다. 일반적으로 목록에서와 같이 하나의 형식 매개 변수를 사용 하 \<T> 고 사전에서와 같이 두 개의 형식 매개 변수를 사용 하는 것이 명확 \<TKey, TValue> 합니다. 그러나 형식 매개 변수가 세 개 이상이면 대부분의 사용자가 사용하기에 너무 어렵습니다.|
|[CA1006: 멤버 시그니처에 제네릭 형식을 중첩하지 마세요.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|중첩된 형식 인수는 제네릭 형식의 인수입니다. 시그니처에 중첩된 형식 인수가 포함되어 있는 멤버를 호출하려면 제네릭 형식 하나를 인스턴스화하고 이 형식을 두 번째 제네릭 형식의 생성자에 전달해야 합니다. 이 경우 복잡한 프로시저와 구문이 필요하므로 이 방법을 피해야 합니다.|
|[CA1007: 적합한 제네릭을 사용하세요.](../code-quality/ca1007-use-generics-where-appropriate.md)|외부에서 볼 수 있는 메서드에 System.Object 형식의 참조 매개 변수가 포함되어 있습니다. 제네릭 메서드를 사용하면 제약 조건에 따라 형식을 참조 매개 변수 형식으로 먼저 캐스팅하지 않고도 모든 형식을 메서드에 전달할 수 있습니다.|
|[CA1008: 열거형에는 0 값이 있어야 합니다.](../code-quality/ca1008-enums-should-have-zero-value.md)|초기화되지 않은 열거형의 기본값은 다른 값 형식과 마찬가지로 0입니다. 플래그가 지정 되지 않은 특성 사용 열거형은 기본값이 열거형의 유효한 값이 되도록 0 값을 사용 하 여 멤버를 정의 해야 합니다. FlagsAttribute 특성이 적용된 열거형에서 0 값을 가진 멤버를 정의하는 경우에는 열거형에 값이 설정되지 않았음을 나타낼 수 있도록 해당 멤버 이름이 "None"이어야 합니다.|
|[CA1009: 이벤트 처리기를 제대로 선언하십시오.](../code-quality/ca1009-declare-event-handlers-correctly.md)|이벤트 처리기 메서드는 두 개의 매개 변수를 사용합니다. 첫 번째 매개 변수는 System.Object 형식이고 이름은 "sender"입니다. 이 매개 변수는 이벤트를 발생시킨 개체입니다. 두 번째 매개 변수는 System.EventArgs 형식이고 이름은 "e"입니다. 이 매개 변수는 이벤트와 관련된 데이터입니다. 이벤트 처리기 메서드는 값을 반환하지 않아야 하며, C# 프로그래밍 언어에서 이는 반환 형식 void로 표시됩니다.|
|[CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)|컬렉션의 유용성을 높이려면 제네릭 컬렉션 인터페이스 중 하나를 구현합니다. 그러면 컬렉션을 사용하여 제네릭 컬렉션 형식을 채울 수 있습니다.|
|[CA1011: 기본 형식을 매개 변수로 전달해 보세요.](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|기본 형식이 메서드 선언의 매개 변수로 지정된 경우 기본 형식에서 파생된 모든 형식을 해당 인수로 메서드에 전달할 수 있습니다. 파생된 매개 변수 형식에서 제공하는 추가 기능이 필요하지 않은 경우 기본 형식을 사용하면 메서드를 보다 광범위하게 사용할 수 있습니다.|
|[CA1012: 추상 형식에는 생성자를 사용하면 안 됩니다.](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|추상 형식에 대한 생성자는 파생된 형식에서만 호출할 수 있습니다. public 생성자에서 형식의 인스턴스를 만들고 사용자는 추상 형식의 인스턴스를 만들 수 없기 때문에 public 생성자가 있는 추상 형식은 잘못 디자인된 것입니다.|
|[CA1013: 더하기 및 빼기를 오버로드할 때 같음 연산자를 오버로드하세요.](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|public 또는 protected 형식이 같음 연산자를 구현하지 않고 더하기 또는 빼기 연산자를 구현합니다.|
|[CA1014: CLSCompliantAttribute로 어셈블리를 표시하세요.](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|CLS(공용 언어 사양)는 어셈블리가 여러 프로그래밍 언어에 사용될 경우 준수해야 하는 명명 제한, 데이터 형식 및 규칙을 정의합니다. 바람직한 디자인은 모든 어셈블리가 CLSCompliantAttribute를 사용 하 여 CLS 규격을 명시적으로 표시 하도록 지시 합니다. 어셈블리에 이 특성이 없으면 해당 어셈블리는 규격을 따르지 않습니다.|
|[CA1016: AssemblyVersionAttribute로 어셈블리 표시](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|.NET Framework 버전 번호를 사용 하 여 어셈블리를 고유 하 게 식별 하 고 강력한 이름의 어셈블리에 있는 형식에 바인딩합니다. 버전 번호는 버전 및 게시자 정책과 함께 사용됩니다. 기본적으로 애플리케이션은 해당 애플리케이션이 빌드될 때 사용된 어셈블리 버전으로만 실행됩니다.|
|[CA1017: ComVisibleAttribute로 어셈블리를 표시하세요.](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute는 COM 클라이언트에서 관리 코드에 액세스하는 방식을 결정합니다. 어셈블리에서 COM에 노출할지 여부를 명시적으로 나타내는 것이 좋은 디자인입니다. 전체 어셈블리에 대해 COM 노출 여부를 설정한 다음 개별 형식 및 형식 멤버에 대해 이를 재정의할 수 있습니다. 이 특성이 없으면 COM 클라이언트에서 어셈블리의 내용을 볼 수 있습니다.|
|[CA1018: AttributeUsageAttribute로 특성을 표시하세요.](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|사용자 지정 특성을 정의할 때는 해당 특성을 AttributeUsageAttribute로 표시하여 사용자 지정 특성을 적용할 수 있는 소스 코드의 위치를 나타냅니다. 특성의 의미 및 용도에 따라 코드에서의 유효한 위치가 결정됩니다.|
|[CA1019: 특성 인수의 접근자를 정의하세요.](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|특성에서는 대상에 특성을 적용할 때 지정해야 하는 필수 인수를 정의할 수 있습니다. 이러한 인수는 특성 생성자에 위치 매개 변수로 제공되기 때문에 이러한 인수를 위치 인수라고도 합니다. 모든 필수 인수에 대해 특성은 실행 시간에 인수의 값을 검색할 수 있도록 해당하는 읽기 전용 속성도 제공해야 합니다. 특성에서는 명명된 인수라고 하는 선택적 인수도 정의할 수 있습니다. 이들 인수는 이름으로 특성 생성자에 제공되며 해당하는 읽기/쓰기 특성이 있어야 합니다.|
|[CA1020: 형식이 부족한 네임스페이스를 사용하지 마세요.](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|각 네임 스페이스에 논리적 구성이 있는지 확인 하 고, 부족 하 게 채워진 네임 스페이스에 형식을 배치 하는 유효한 이유가 있는지 확인 합니다.|
|[CA1021: out 매개 변수를 사용하지 마세요.](../code-quality/ca1021-avoid-out-parameters.md)|out 또는 ref를 사용하여 참조로 형식을 전달하려면 포인터 사용 방법을 알고 있어야 하고, 값 형식과 참조 형식이 어떻게 다른지 알고 있어야 하며, 반환 값이 여러 개인 메서드를 처리할 수 있어야 합니다. 또한 out 매개 변수와 ref 매개 변수의 차이점은 잘 알려져 있지 않습니다.|
|[CA1023: 다차원 인덱서를 사용하지 마세요.](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|인덱서, 즉 인덱싱된 속성은 단일 인덱스를 사용해야 합니다. 다차원 인덱서를 사용하면 라이브러리의 유용성이 현저히 줄어들 수 있습니다.|
|[CA1024: 적합한 속성을 사용하세요.](../code-quality/ca1024-use-properties-where-appropriate.md)|public 또는 protected 메서드가 "Get"으로 시작하는 이름을 사용하고, 매개 변수를 사용하지 않으며, 배열이 아닌 값을 반환합니다. 이 메서드는 속성이 될 수 있는 좋은 예일 수 있습니다.|
|[CA1025: 반복 인수를 매개 변수 배열로 바꾸세요.](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|인수의 정확한 개수를 알 수 없는데 가변 인수가 같은 형식이거나 같은 형식으로서 전달될 수 있는 경우에는 반복되는 인수 대신 매개 변수 배열을 사용합니다.|
|[CA1026: 기본 매개 변수를 사용하면 안 됩니다.](../code-quality/ca1026-default-parameters-should-not-be-used.md)|CLS에서는 기본 매개 변수를 사용하는 메서드를 허용하지만 컴파일러가 이러한 매개 변수에 할당된 값을 무시할 수 있도록 합니다. 여러 프로그래밍 언어에서 원하는 동작을 유지하려면 기본 매개 변수를 사용하는 메서드를 기본 매개 변수를 제공하는 메서드 오버로드로 바꿔야 합니다.|
|[CA1027: 열거형을 FlagsAttribute로 표시하세요.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 명명된 상수를 의미 있게 조합할 수 있는 경우 열거형에 FlagsAttribute를 적용합니다.|
|[CA1028: 열거형 스토리지는 Int32여야 합니다.](../code-quality/ca1028-enum-storage-should-be-int32.md)|열거형은 서로 관련 있는 명명된 상수 집합을 정의하는 값 형식입니다. 기본적으로 System.Int32 데이터 형식은 상수 값을 저장하는 데 사용됩니다. 이 기본 형식을 변경할 수 있지만 대부분의 시나리오에서는 필요 하지 않거나 권장 되지 않습니다.|
|[CA1030: 적절한 경우 이벤트를 사용하세요.](../code-quality/ca1030-use-events-where-appropriate.md)|이 규칙에서는 보통 이벤트에 사용되는 이름을 갖는 메서드를 찾아냅니다. 명확하게 정의된 상태 변경에 대한 응답으로 메서드를 호출할 경우 이 메서드는 이벤트 처리기에서 호출해야 합니다. 메서드를 호출하는 개체는 메서드를 직접 호출하는 대신 이벤트를 발생시켜야 합니다.|
|[CA1031: 일반적인 예외 형식을 catch하지 마세요.](../code-quality/ca1031-do-not-catch-general-exception-types.md)|일반 예외는 catch하면 안 됩니다. 더 구체적인 예외를 catch 하거나 catch 블록의 마지막 문으로 일반 예외를 다시 throw 합니다.|
|[CA1032: 표준 예외 생성자를 구현하세요.](../code-quality/ca1032-implement-standard-exception-constructors.md)|이들 생성자 집합을 전부 제공하지 못하면 예외를 제대로 처리하기 어려울 수 있습니다.|
|[CA1033: 인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|외부에서 볼 수 있는 unsealed 형식이 public 인터페이스의 명시적 메서드 구현을 제공하면서 외부에서 볼 수 있는 같은 이름의 대체 메서드를 제공하지 않습니다.|
|[CA1034: 중첩 형식은 노출되면 안 됩니다.](../code-quality/ca1034-nested-types-should-not-be-visible.md)|중첩 형식은 다른 형식의 범위 내에 선언된 형식입니다. 중첩 형식은 포함하는 형식의 private 구현 정보를 캡슐화하는 데 유용합니다. 이 용도로 사용할 경우 중첩 형식은 외부에 노출되면 안 됩니다.|
|[CA1035: ICollection 구현에 강력한 형식의 멤버가 있습니다.](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|이 규칙에서는 사용자가 인터페이스에서 제공하는 기능을 사용할 때 인수를 Object 형식으로 캐스팅할 필요가 없도록 ICollection 구현에서 강력한 형식의 멤버를 제공할 것을 요구합니다. 이 규칙에서는 ICollection을 구현하는 형식이 이를 수행하여 Object보다 강력한 형식의 인스턴스 컬렉션을 관리한다고 가정합니다.|
|[CA1036: 비교 가능한 형식에 메서드를 재정의하세요.](../code-quality/ca1036-override-methods-on-comparable-types.md)|public 또는 protected 형식이 System.IComparable 인터페이스를 구현합니다. 이 형식은 Object.Equals를 재정의하지 않으며 같음, 같지 않음, 보다 작음 또는 보다 큼에 대한 언어별 연산자를 오버로드하지 않습니다.|
|[CA1038: 열거자는 강력한 형식이어야 합니다.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|이 규칙에서는 사용자가 인터페이스에서 제공하는 기능을 사용할 때 반환 값을 강력한 형식으로 캐스팅할 필요가 없도록 IEnumerator 구현에서 Current 속성의 강력한 형식 버전도 제공할 것을 요구합니다.|
|[CA1039: 목록은 강력한 형식이어야 합니다.](../code-quality/ca1039-lists-are-strongly-typed.md)|이 규칙에서는 사용자가 인터페이스에서 제공하는 기능을 사용할 때 인수를 System.Object 형식으로 캐스팅할 필요가 없도록 IList 구현에서 강력한 형식의 멤버를 제공할 것을 요구합니다.|
|[CA1040: 빈 인터페이스를 사용하지 마세요.](../code-quality/ca1040-avoid-empty-interfaces.md)|인터페이스에서는 동작이나 사용 계약을 제공하는 멤버를 정의합니다. 인터페이스에 의해 설명되는 기능은 상속 계층 구조에서 형식이 나타나는 위치에 관계없이 모든 형식에서 사용할 수 있습니다. 형식에서는 인터페이스의 멤버에 대한 구현을 제공하여 인터페이스를 구현합니다. 빈 인터페이스는 멤버를 정의하지 않으므로 구현 가능한 계약을 정의하지 않습니다.|
|[CA1041: ObsoleteAttribute 메시지를 제공하세요.](../code-quality/ca1041-provide-obsoleteattribute-message.md)|형식 또는 멤버가 ObsoleteAttribute.Message 속성이 지정되지 않은 System.ObsoleteAttribute 특성으로 표시되어 있습니다. ObsoleteAttribute를 사용 하 여 표시 된 형식 또는 멤버를 컴파일하면 특성의 메시지 속성이 표시 되어 사용 되지 않는 형식 또는 멤버에 대 한 정보를 사용자에 게 제공 합니다.|
|[CA1043: 인덱서에 정수 또는 문자열 인수를 사용하세요.](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|인덱서, 즉 인덱싱된 속성은 인덱스에 정수 계열 형식이나 문자열 형식을 사용해야 합니다. 이러한 형식은 대개 데이터 구조를 인덱싱하는 데 사용되며 라이브러리의 유용성을 증가시킵니다. Object 형식은 디자인 타임에 특정 정수 계열 형식이나 문자열 형식을 지정할 수 없는 경우에만 제한적으로 사용해야 합니다.|
|[CA1044: 속성은 쓰기 전용이면 안 됩니다.](../code-quality/ca1044-properties-should-not-be-write-only.md)|읽기 전용 속성을 사용하는 것은 가능하고 종종 필요하기도 하지만 쓰기 전용 속성의 사용은 금지되어 있습니다. 사용자에게 값을 설정하도록 허용한 다음 해당 값을 볼 수 없도록 하면 보안상 문제가 있기 때문입니다. 또한 읽기 권한이 없으면 공유 개체의 상태를 볼 수 없으므로 사용하는 데 제한을 받습니다.|
|[CA1045: 참조로 형식을 전달하지 마세요.](../code-quality/ca1045-do-not-pass-types-by-reference.md)|out 또는 ref를 사용하여 참조로 형식을 전달하려면 포인터 사용 방법을 알고 있어야 하고, 값 형식과 참조 형식이 어떻게 다른지 알고 있어야 하며, 반환 값이 여러 개인 메서드를 처리할 수 있어야 합니다. 일반 사용자를 대상으로 디자인하는 라이브러리 설계자는 사용자가 out 또는 ref 매개 변수를 사용하는 작업에 능숙할 것이라고 기대해서는 안 됩니다.|
|[CA1046: 참조 형식에 같음 연산자를 오버로드하지 마세요.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|참조 형식의 경우 같음 연산자의 기본 구현은 대부분 항상 올바릅니다. 기본적으로 두 참조는 같은 개체를 가리킬 경우에만 같습니다.|
|[CA1047: protected 멤버를 sealed 형식으로 선언하지 마세요.](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|형식에서는 상속하는 형식에서 멤버에 액세스하거나 멤버를 재정의할 수 있도록 하기 위해 protected 멤버를 선언합니다. 정의에 따라 sealed 형식은 상속할 수 없으므로 sealed 형식에 대해 protected 메서드를 호출할 수 없습니다.|
|[CA1048: 가상 멤버를 sealed 형식으로 선언하지 마세요.](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|상속 형식이 가상 메서드의 구현을 재정의할 수 있도록 하기 위해 형식은 메서드를 가상으로 선언합니다. 정의에 따라 sealed 형식은 상속할 수 없습니다. 따라서 sealed 형식에 대한 가상 메서드는 의미가 없습니다.|
|[CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|관리되지 않는 리소스를 할당하는 형식은 IDisposable을 구현하여 호출자가 필요할 때 해당 리소스를 해제할 수 있도록 하고 리소스를 차지하고 있는 개체의 수명을 줄여야 합니다.|
|[CA1050: 네임스페이스에 형식을 선언하세요.](../code-quality/ca1050-declare-types-in-namespaces.md)|이름 충돌을 방지하고 관련된 형식을 개체 계층 구조로 구성하기 위해 형식은 네임스페이스 안에 선언됩니다.|
|[CA1051: 표시되는 인스턴스 필드를 선언하지 마세요.](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|필드의 주된 용도는 구현을 세부적으로 설명하는 것입니다. 필드는 private 또는 internal이어야 하고 속성을 통해 노출되어야 합니다.|
|[CA1052: 정적 소유자 형식은 sealed여야 합니다.](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Public 또는 protected 형식이 정적 멤버만 포함 하며 sealed (c #) 또는 NotInheritable (Visual Basic) 한정자를 사용 하 여 선언 되지 않았습니다. 상속을 고려하지 않은 형식은 sealed 한정자로 표시하여 기본 형식으로 사용되지 않도록 해야 합니다.|
|[CA1053: 정적 소유자 형식에는 생성자를 사용하면 안 됩니다.](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|public 또는 중첩된 public 형식에서 정적 멤버만 선언하며 public 또는 protected 기본 생성자를 사용합니다. 호출하는 정적 멤버에 형식의 인스턴스가 필요하지 않기 때문에 생성자가 필요 없습니다. 문자열 오버로드는 안전과 보안을 위해 문자열 인수를 사용하여 URI(Uniform Resource Identifier) 오버로드를 호출해야 합니다.|
|[CA1054: URI 매개 변수는 문자열이면 안 됩니다.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|메서드가 URI의 문자열 표현을 사용하면 URI 클래스의 인스턴스를 사용하는 해당 오버로드를 제공해야 합니다. 이렇게 하면 서비스가 안전한 방식으로 제공됩니다.|
|[CA1055: URI 반환 값은 문자열이면 안 됩니다.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|이 규칙에서는 메서드가 URI를 반환한다고 가정합니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. System.Uri 클래스는 이러한 서비스를 안전한 방식으로 제공합니다.|
|[CA1056: URI 속성은 문자열이면 안 됩니다.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|이 규칙은 속성이 URI를 나타내는 것으로 가정 합니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. System.Uri 클래스는 이러한 서비스를 안전한 방식으로 제공합니다.|
|[CA1057: 문자열 URI 오버로드는 System.Uri 오버로드를 호출합니다.](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|형식에서 문자열 매개 변수가 System.Uri 매개 변수로 바뀐 점만 다른 메서드 오버로드를 선언합니다. 문자열 매개 변수를 사용하는 오버로드는 URI 매개 변수를 사용하는 오버로드를 호출하지 않습니다.|
|[CA1058: 형식은 특정 기본 형식을 확장하면 안 됩니다.](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|외부에서 볼 수 있는 형식이 특정 기본 형식을 확장합니다. 다음 방법 중 하나를 사용합니다.|
|[CA1059: 멤버는 구체적인 특정 형식을 노출하면 안 됩니다.](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|구체적인 형식은 완전히 구현되었기 때문에 인스턴스화할 수 있는 형식을 말합니다. 멤버를 광범위하게 사용할 수 있도록 하려면 구체적인 형식을 제안된 인터페이스로 바꾸십시오.|
|[CA1060: P/Invoke를 NativeMethods 클래스로 이동 합니다.](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|에서 Declare 키워드를 사용 하 여 정의 된 또는 메서드로 표시 된 것과 같은 플랫폼 호출 메서드는 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 비관리 코드에 액세스 합니다. 이러한 메서드는 NativeMethods, SafeNativeMethods 또는 UnsafeNativeMethods 클래스에 속해야 합니다.|
|[CA1061: 기본 클래스 메서드를 숨기지 마십시오.](../code-quality/ca1061-do-not-hide-base-class-methods.md)|파생된 메서드의 매개 변수 시그니처가 기본 메서드의 매개 변수 시그니처에 있는 해당 형식보다 더 약하게 파생된 형식이라는 점만 다른 경우 기본 형식의 메서드는 파생된 형식에 있는 동일한 이름의 메서드에 의해 숨겨집니다.|
|[CA1062: public 메서드의 인수에 대한 유효성을 검사하세요.](../code-quality/ca1062-validate-arguments-of-public-methods.md)|외부에서 볼 수 있는 메서드에 전달되는 모든 참조 인수는 null인지 여부를 검사해야 합니다.|
|[CA1063: IDisposable을 올바르게 구현하십시오.](../code-quality/ca1063-implement-idisposable-correctly.md)|모든 IDisposable 형식은 Dispose 패턴을 올바르게 구현해야 합니다.|
|[CA1064: 예외는 public이어야 합니다.](../code-quality/ca1064-exceptions-should-be-public.md)|내부 예외는 내부 범위 내에만 표시됩니다. 예외가 내부 범위 밖에 놓이게 되면 예외를 catch하는 데 기본 예외만 사용할 수 있습니다. 내부 예외에서 상속 되 면 <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, 또는 <xref:System.ApplicationException?displayProperty=fullName>, 외부 코드에 예외를 사용 하 여 수행할 작업을 알고에 충분 한 정보가 없습니다.|
|[CA1065: 예기치 않은 위치에서 예외를 발생시키지 마십시오.](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|예외를 throw하지 않아야 하는 메서드가 예외를 throw했습니다.|
|[CA2210: 어셈블리에는 올바른 강력한 이름을 사용해야 합니다.](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|강력한 이름은 클라이언트에서 무단으로 변경된 어셈블리를 모르는 사이에 로드하지 못하도록 보호합니다. 강력한 이름이 없는 어셈블리는 극히 제한된 시나리오 이외에는 배포하면 안 됩니다. 제대로 서명되지 않은 어셈블리를 공유하거나 배포하면 어셈블리가 무단으로 변경되거나, 공용 언어 런타임에서 어셈블리를 로드할 수 없거나, 사용자가 자신의 컴퓨터에서 확인을 사용하지 못하게 될 수 있습니다.|
