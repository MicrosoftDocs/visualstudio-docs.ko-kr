---
title: 관리 코드에 대 한 확장 수정 규칙 규칙 집합 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bef208dbcb4c1017840602d198b5099267b25a99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667633"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>관리 코드에 대한 확장 수정 규칙 규칙 집합
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 확장 수정 규칙 규칙 집합은 코드 분석을 통해 보고 되는 논리 및 프레임 워크 사용 오류를 최대화 합니다. COM 상호 운용성 및 모바일 응용 프로그램과 같은 특정 시나리오에 대 한 추가 강조가 있습니다. 이러한 시나리오 중 하나가 프로젝트에 적용 되거나 프로젝트에서 추가 문제를 발견 하는 경우이 규칙 집합을 포함 하는 것을 고려해 야 합니다.

 Microsoft 확장 수정 규칙 규칙 집합에는 Microsoft 기본 수정 규칙 규칙 집합에 있는 규칙이 포함 됩니다. 기본 정확성 규칙에는 Microsoft 최소 권장 규칙 규칙 집합에 있는 규칙이 포함 됩니다. 자세한 내용은 관리 코드에 대 한 [기본 수정 규칙 규칙 집합](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) 및 관리 [코드에 대 한 관리 권장 규칙](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) 규칙 집합을 참조 하세요.

 다음 표에서는 Microsoft 확장 수정 규칙 규칙 집합의 모든 규칙에 대해 설명 합니다.

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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|열거형에는 0 값이 있어야 합니다.|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|더하기 및 빼기를 오버로드할 때 같음 연산자를 오버로드하세요.|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|리터럴을 지역화된 매개 변수로 전달하지 마세요.|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|대문자로 문자열을 정규화하세요.|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|메서드 결과를 무시하지 마세요.|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|GC.SuppressFinalize를 올바르게 호출하세요.|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|속성은 배열을 반환해서는 안 됩니다.|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|문자열 길이를 사용하여 빈 문자열을 테스트하세요.|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|대상 프레임워크의 API만 사용하세요.|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|GC.KeepAlive에 대한 호출을 제거하세요.|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|SafeHandle을 사용하여 네이티브 리소스를 캡슐화하세요.|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|일반 처리기에서 비 CLSCompliant 예외를 catch하세요.|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|변경 가능한 읽기 전용 참조 형식을 선언하지 마세요.|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|배열 필드는 읽기 전용이면 안 됩니다.|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|어설션을 안전하게 보호하세요.|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하세요.|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|private 인터페이스를 만족하는 메서드를 봉인하세요.|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|serialization 생성자를 안전하게 하세요.|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|정적 생성자는 private이어야 합니다.|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|보안에 중요한 상수는 투명해야 합니다.|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API의 동일한 관리형 기능을 사용하세요.|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|종료자는 protected여야 합니다.|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|상속된 멤버 노출 수준을 낮추지 마세요.|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|멤버는 반환 형식 이외의 것도 달라야 합니다.|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|같음 연산자를 오버로드할 때 Equals를 재정의하세요.|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|연산자에는 대칭 오버로드가 있어야 합니다.|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|컬렉션 속성은 읽기 전용이어야 합니다.|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|선택적 필드에 deserialization 메서드를 제공하세요.|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|표준 예외 생성자를 구현하세요.|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI 매개 변수는 문자열이면 안 됩니다.|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 반환 값은 문자열이면 안 됩니다.|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI 속성은 문자열이면 안 됩니다.|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|문자열 URI 오버로드는 System.Uri 오버로드를 호출합니다.|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|COM 노출 인터페이스에서 오버로드를 사용하지 마세요.|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 클라이언트에서는 Int64 인수를 사용하지 마세요.|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM 노출 형식에 정적 멤버를 사용하지 마세요.|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|AutoDual ClassInterfaceType을 사용하지 마세요.|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Com 노출 형식을 만들 수 있어야 합니다.|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|COM 등록 메서드는 노출되면 안 됩니다.|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|ComSource 인터페이스를 IDispatch로 표시하세요.|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|COM 노출 값 형식에 public이 아닌 필드를 사용하지 마세요.|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|부울 P/Invoke 인수를 MarshalAs로 표시하세요.|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|유휴 프로세스 우선 순위를 사용하지 마세요.|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|전원 상태 변경을 방해하는 타이머를 사용하지 마세요.|
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|NeutralResourcesLanguageAttribute로 어셈블리를 표시하세요.|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|문제가 있는 메서드는 호출하지 마세요.|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|파이버를 스레드로 취급하지 마세요.|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|수준 2 어셈블리는 LinkDemands를 포함할 수 없습니다.|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|멤버는 충돌하는 투명도 주석을 포함할 수 없습니다.|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|투명 메서드는 HandleProcessCorruptingExceptions 특성을 사용할 수 없습니다.|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|투명 코드는 LinkDemands로 보호될 수 없습니다.|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|투명 메서드는 보안 요청을 사용할 수 없습니다.|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|투명 코드는 바이트 배열에서 어셈블리를 로드할 수 없습니다.|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|투명 메서드는 SuppressUnmanagedCodeSecurityAttribute 특성으로 데코레이팅할 수 없습니다.|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|리터럴의 맞춤법이 정확해야 합니다.|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|비상수 필드는 노출되면 안 됩니다.|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|열거형을 FlagsAttribute로 표시하지 마세요.|
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Equals를 재정할 때 GetHashCode를 재정의하세요.|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|exception 절에서 예외를 발생시키지 마세요.|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|연산자 오버로드에는 명명된 대체 항목이 있습니다.|
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|릴리스되지 않은 리소스 형식을 제공하지 마세요.|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|가변 인수로 params를 사용하세요.|
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|연산은 오버플로되지 않아야 합니다.|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|문자열 대신 System.Uri 개체를 전달하세요.|
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|특성 문자열 리터럴이 올바르게 구문 분석되어야 합니다.|
