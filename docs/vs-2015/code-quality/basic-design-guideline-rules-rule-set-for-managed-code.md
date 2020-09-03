---
title: 관리 코드에 대 한 기본 디자인 지침 규칙 규칙 집합 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cefe4864db8455ba6712dc728b342f49b6c7d5d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655116"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>관리 코드에 대한 기본 디자인 지침 규칙 규칙 집합
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 기본 디자인 지침 규칙 규칙 집합을 사용 하 여 코드를 더 쉽게 이해 하 고 사용할 수 있도록 집중할 수 있습니다. 프로젝트에 라이브러리 코드가 포함 되어 있거나 유지 관리가 쉬운 코드에 대 한 모범 사례를 적용 하려는 경우이 규칙 집합을 포함 해야 합니다.

 기본 디자인 지침 규칙은 Microsoft Minimum Recommeded Rules 규칙 집합의 모든 규칙을 포함 합니다. 최소 규칙 목록은 관리 되는 [권장 규칙 규칙 집합 관리 코드](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)를 참조 하세요.

 다음 표에서는 Microsoft 기본 디자인 지침 규칙 규칙 집합의 모든 규칙에 대해 설명 합니다.

|규칙|설명|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|이벤트 처리기를 제대로 선언하십시오.|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|AssemblyVersionAttribute로 어셈블리 표시|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/Invoke를 NativeMethods 클래스로 이동|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|기본 클래스 메서드를 숨기지 마십시오.|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable을 올바르게 구현하십시오.|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|예기치 않은 위치에서 예외를 발생시키지 마십시오.|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|중복 액셀러레이터 키를 사용하지 마십시오.|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke 진입점이 있어야 합니다.|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke는 노출되지 않아야 합니다.|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|자동 레이아웃 형식은 COM 노출이면 안 됩니다.|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/Invoke 다음에 바로 GetLastError를 호출하십시오.|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 노출 형식의 기본 형식은 COM 노출이어야 합니다.|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM 등록 메서드는 일치해야 합니다.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invoke를 올바르게 선언하십시오.|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|빈 종료자를 제거하십시오.|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|값 형식 필드는 이식 가능해야 합니다.|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke 선언은 이식 가능해야 합니다.|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|약한 ID를 가진 개체를 잠그지 마십시오.|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke 문자열 인수에 대해 마샬링을 지정하십시오.|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|값 형식에서 선언적 보안을 검토하십시오.|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|포인터는 노출되면 안 됩니다.|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|보안 형식은 필드를 노출하면 안 됩니다.|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|메서드 보안은 형식의 상위 집합이어야 합니다.|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA 메서드는 APTCA 메서드만 호출해야 합니다.|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|재정의 링크 요청은 기본 링크 요청과 같아야 합니다.|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|취약한 finally 절을 외부 try에 래핑하십시오.|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|형식 링크 요청에는 상속 요청이 필요합니다.|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|투명 메서드는 LinkDemands를 충족해서는 안 됩니다|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|투명 메서드는 보안 어설션을 사용할 수 없습니다.|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|스택 정보를 유지하도록 다시 throw하십시오.|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|개체를 여러 번 삭제하지 마십시오.|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|값 형식 정적 필드 인라인을 초기화하십시오.|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|삭제 가능한 필드는 삭제해야 합니다.|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|재정의 가능한 메서드를 생성자에서 호출하지 마십시오.|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|삭제 가능한 형식은 종료자를 선언해야 합니다.|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|종료자는 기본 클래스 종료자를 호출해야 합니다.|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|serialization 생성자를 구현하십시오.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|모두 serialize할 수 없는 필드로 표시하십시오.|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|SerializableAttribute로 ISerializable 형식 표시|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|serialization 메서드를 올바르게 구현하십시오.|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable을 올바르게 구현하십시오.|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|서식 지정 메서드에 올바른 인수를 제공하십시오.|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN에 대해 정확하게 테스트하십시오.|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|정적 멤버를 제네릭 형식으로 선언하지 마세요.|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|제네릭 목록을 노출하지 마세요.|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|제네릭 이벤트 처리기 인스턴스를 사용하세요.|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|제네릭 메서드는 형식 매개 변수를 제공해야 합니다.|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|제네릭 형식에 매개 변수를 너무 많이 사용하지 마세요.|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|멤버 시그니처에 제네릭 형식을 중첩하지 마세요.|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|적합한 제네릭을 사용하세요.|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|열거형에는 0 값이 있어야 합니다.|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|컬렉션은 제네릭 인터페이스를 구현해야 합니다.|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|기본 형식을 매개 변수로 전달해 보세요.|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|추상 형식에는 생성자를 사용하면 안 됩니다.|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|더하기 및 빼기를 오버로드할 때 같음 연산자를 오버로드하세요.|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|CLSCompliantAttribute로 어셈블리를 표시하세요.|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute로 어셈블리를 표시하세요.|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|AttributeUsageAttribute로 특성을 표시하세요.|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|특성 인수의 접근자를 정의하세요.|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|다차원 인덱서를 사용하지 마세요.|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|적합한 속성을 사용하세요.|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|반복 인수를 매개 변수 배열로 바꾸세요.|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|기본 매개 변수를 사용하면 안 됩니다.|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|열거형을 FlagsAttribute로 표시하세요.|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|열거형 스토리지는 Int32여야 합니다.|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|적절한 경우 이벤트를 사용하세요.|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|일반적인 예외 형식을 catch하지 마세요.|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|표준 예외 생성자를 구현하세요.|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|중첩 형식은 노출되면 안 됩니다.|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection 구현에 강력한 형식의 멤버가 있습니다.|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|비교 가능한 형식에 메서드를 재정의하세요.|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|열거자는 강력한 형식이어야 합니다.|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|목록은 강력한 형식이어야 합니다.|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|ObsoleteAttribute 메시지를 제공하세요.|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|인덱서에 정수 또는 문자열 인수를 사용하세요.|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|속성은 쓰기 전용이면 안 됩니다.|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|참조 형식에 같음 연산자를 오버로드하지 마세요.|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|protected 멤버를 sealed 형식으로 선언하지 마세요.|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|가상 멤버를 sealed 형식으로 선언하지 마세요.|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|네임스페이스에 형식을 선언하세요.|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|표시되는 인스턴스 필드를 선언하지 마세요.|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|정적 소유자 형식은 sealed여야 합니다.|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|정적 소유자 형식에는 생성자를 사용하면 안 됩니다.|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI 매개 변수는 문자열이면 안 됩니다.|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 반환 값은 문자열이면 안 됩니다.|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI 속성은 문자열이면 안 됩니다.|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|문자열 URI 오버로드는 System.Uri 오버로드를 호출합니다.|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|형식은 특정 기본 형식을 확장하면 안 됩니다.|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|멤버는 구체적인 특정 형식을 노출하면 안 됩니다.|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|예외는 public이어야 합니다.|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|변수 이름은 필드 이름과 달라야 합니다.|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|지나치게 복잡하게 만들지 마세요.|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|식별자는 키워드와 달라야 합니다.|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|사용되지 않은 매개 변수를 검토하세요.|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|사용되지 않는 로컬 항목을 제거하세요.|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|불필요한 로컬 항목을 사용하지 마세요.|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|참조 형식 정적 필드를 인라인으로 초기화하세요.|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|호출되지 않는 전용 코드를 사용하지 마세요.|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|인스턴스화되지 않은 내부 클래스를 사용하지 마세요.|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|봉인되지 않은 특성을 사용하지 마세요.|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|다차원 배열보다 가변 배열을 사용하세요.|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|값 형식에서 Equals 또는 같음 연산자를 재정의하세요.|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|속성은 배열을 반환해서는 안 됩니다.|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|문자열 길이를 사용하여 빈 문자열을 테스트하세요.|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|멤버를 static으로 표시하세요.|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|사용되지 않는 전용 필드를 사용하지 마세요.|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|예약된 예외 형식을 발생시키지 마세요.|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API의 동일한 관리형 기능을 사용하세요.|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|인수 예외를 올바르게 인스턴스화하세요.|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|비상수 필드는 노출되면 안 됩니다.|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|열거형을 FlagsAttribute로 표시하지 마세요.|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|exception 절에서 예외를 발생시키지 마세요.|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|종료자는 protected여야 합니다.|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|상속된 멤버 노출 수준을 낮추지 마세요.|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|멤버는 반환 형식 이외의 것도 달라야 합니다.|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|같음 연산자를 오버로드할 때 Equals를 재정의하세요.|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|연산자 오버로드에는 명명된 대체 항목이 있습니다.|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|연산자에는 대칭 오버로드가 있어야 합니다.|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|컬렉션 속성은 읽기 전용이어야 합니다.|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|가변 인수로 params를 사용하세요.|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|문자열 대신 System.Uri 개체를 전달하세요.|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|선택적 필드에 deserialization 메서드를 제공하세요.|
