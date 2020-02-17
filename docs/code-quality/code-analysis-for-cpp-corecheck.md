---
title: C + + 핵심 지침 검사기 참조
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 2c3e1ba77f3f78de3fc1fac4185121ecb42b1b5b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271387"
---
# <a name="c-core-guidelines-checker-reference"></a>C + + 핵심 지침 검사기 참조

이 섹션에서는 c + + 핵심 지침 검사기 경고를 나열합니다. 코드 분석에 대 한 자세한 내용은 [/analyze (코드 분석)](/cpp/build/reference/analyze-code-analysis) 및 [빠른 시작: C/C++에 대 한 코드 분석](../code-quality/quick-start-code-analysis-for-c-cpp.md)을 참조 하세요.

> [!NOTE]
> 일부 경고 둘 이상의 그룹에 속하고 모든 경고의 경우에 완전 한 참조 항목입니다.

## <a name="owner_pointer-group"></a>OWNER_POINTER 그룹

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) 이동 생성자가 있는 경우 힙 할당 대신 범위 개체를 반환 합니다. [ C++ 핵심 지침 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)을 참조 하세요.

[C26403 RESET_OR_DELETE_OWNER](C26403.md) 소유자\<T > 포인터 '% variable% '을 (를) 다시 설정 하거나 명시적으로 삭제 하십시오. [ C++ 핵심 지침 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)을 참조 하세요.

[C26404 DONT_DELETE_INVALID](C26404.md) 잘못 된 상태일 수 있는 소유자\<T >를 삭제 하지 마세요. [ C++ 핵심 지침 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)을 참조 하세요.

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) 유효한 상태일 수 있는 소유자\<T >에 할당 하지 마세요. [ C++ 핵심 지침 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)을 참조 하세요.

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) 소유자\<T >에 원시 포인터를 할당 하지 않습니다. [ C++ 핵심 지침 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)을 참조 하세요.

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) 범위가 지정 된 개체를 선호 하 고, 불필요 하 게 힙 할당 하지 않습니다. [ C++ 핵심 지침 R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)를 참조 하세요.

[C26429 USE_NOTNULL](C26429.md) 기호 '% symbol% '은 (는) null로 표시 될 수 없습니다. not_null으로 표시할 수 있습니다. [ C++ 핵심 지침 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)을 참조 하세요.

[C26430 TEST_ON_ALL_PATHS](C26430.md) '% Symbol% ' 기호는 모든 경로에서 nullness에 대해 테스트 되지 않았습니다. [ C++ 핵심 지침 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)을 참조 하세요.

[C26431 DONT_TEST_NOTNULL](C26431.md) 식 '% expr% '의 유형이 이미 gsl:: not_null입니다. Nullness에 대해 테스트 하지 마십시오. [ C++ 핵심 지침 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)을 참조 하세요.

## <a name="raw_pointer-group"></a>RAW_POINTER 그룹

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) 소유자\<T > 반환 값을 포함 하는 함수 호출 또는 할당의 결과를 원시 포인터에 할당 하지 마십시오. 대신 owner\<T >를 사용 해야 합니다. [ C++ 핵심 지침 I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)을 참조 하세요.

[C26401 DONT_DELETE_NON_OWNER](c26401.md) 소유자\<T > 아닌 원시 포인터를 삭제 하지 마십시오. [ C++ 핵심 지침 I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)을 참조 하세요.

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  이동 생성자가 있는 경우 힙 할당 대신 범위 개체를 반환 합니다. [ C++ 핵심 지침 R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)을 참조 하세요.

[C26408 NO_MALLOC_FREE](C26408.md) Malloc () 및 free ()를 사용 하지 않고 delete와 함께 new의 nothrow 버전을 사용 하는 것이 좋습니다. [ C++ 핵심 지침 R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree)을 참조 하세요.

[C26409 NO_NEW_DELETE](C26409.md) 명시적으로 new 및 delete를 호출 하지 않고, 대신 std:: make_unique\<T >를 사용 합니다. [ C++ 핵심 지침 R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete)을 참조 하세요.

[C26429 USE_NOTNULL](C26429.md) 기호 '% symbol% '은 (는) null로 표시 될 수 없습니다. not_null으로 표시할 수 있습니다. [ C++ 핵심 지침 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)을 참조 하세요.

[C26430 TEST_ON_ALL_PATHS](C26430.md) '% Symbol% ' 기호는 모든 경로에서 nullness에 대해 테스트 되지 않았습니다. [ C++ 핵심 지침 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)을 참조 하세요.

[C26431 DONT_TEST_NOTNULL](C26431.md) 식 '% expr% '의 유형이 이미 gsl:: not_null입니다. Nullness에 대해 테스트 하지 마십시오. [ C++ 핵심 지침 F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)을 참조 하세요.

[C26481 NO_POINTER_ARITHMETIC](C26481.md) 포인터 산술 연산을 사용 하지 않습니다. 범위를 대신 사용 합니다. [ C++ 핵심 지침 범위를 참조 하세요. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
식 '%expr% ': 없는 배열에서 포인터로 감소 합니다. [ C++ 핵심 지침 범위. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)을 참조 하세요.

## <a name="unique_pointer-group"></a>UNIQUE_POINTER 그룹

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) '% Parameter% ' 매개 변수는 `const` 고유 포인터에 대 한 참조입니다. 대신 const T * 또는 const T &를 사용 하십시오. [ C++ 핵심 지침 R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam)를 참조 하세요.

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) '% Parameter% ' 매개 변수는 고유 포인터에 대 한 참조 이며 다시 할당 되거나 다시 설정 되지 않습니다. 대신 T * 또는 T &를 사용 하십시오. [ C++ 핵심 지침](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat)을 참조 하십시오.

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) 로컬 스마트 포인터 '% symbol% '을 (를) 이동, 복사, 다시 할당 또는 다시 설정 합니다. [ C++ 핵심 지침 R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)를 참조 하세요.

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) 스마트 포인터 매개 변수 '% symbol% '은 (는) 포함 된 포인터에 액세스 하는 데만 사용 됩니다. 대신 T \* 또는 T &를 사용 합니다. [ C++ 핵심 지침 R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)을 참조 하세요.

## <a name="shared_pointer-group"></a>SHARED_POINTER 그룹

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) 로컬 스마트 포인터 '% symbol% '을 (를) 이동, 복사, 다시 할당 또는 다시 설정 합니다. [ C++ 핵심 지침 R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)를 참조 하세요.

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) 스마트 포인터 매개 변수 '% symbol% '은 (는) 포함 된 포인터에 액세스 하는 데만 사용 됩니다. 대신 T \* 또는 T &를 사용 합니다. [ C++ 핵심 지침 R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)을 참조 하세요.

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) 공유 포인터 매개 변수 '% symbol% '이 (가) rvalue 참조로 전달 되었습니다. 대신 값으로 전달 합니다. [ C++ 핵심 지침 R .34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner)를 참조 하세요.

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) 공유 포인터 매개 변수 '% symbol% '이 (가) 참조로 전달 되었으며 다시 설정 되거나 다시 할당 되지 않았습니다. 대신 T \* 또는 T &를 사용 합니다. [ C++ 핵심 지침 R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam)를 참조 하세요.

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) 공유 포인터 매개 변수 '% symbol% '이 (가) 복사 되거나 이동 되지 않았습니다. 대신 T \* 또는 T &를 사용 합니다. [ C++ 핵심 지침 R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const)을 참조 하세요.

## <a name="declaration-group"></a>선언 그룹

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) 전역 이니셜라이저가 constexpr이 아닌 함수 '% symbol% '을 (를) 호출 합니다. [ C++ 핵심 지침 I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)를 참조 하세요.

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) 전역 이니셜라이저가 extern 개체 '% symbol% '에 액세스 합니다. [ C++ 핵심 지침 I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)를 참조 하세요.

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) 사용자 지정 생성 및 소멸이 있는 명명 되지 않은 개체를 사용 하지 않습니다. [이름 없이 지역 변수를 선언 합니다. 84](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)를 참조 하세요.

## <a name="class-group"></a>클래스 그룹

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) '% Symbol% ' 형식의 기본 작업을 정의 하거나 삭제 하는 경우 모두 정의 하거나 삭제 합니다. [ C++ 핵심 지침 C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all)을 참조 하세요.

[C26433 OVERRIDE_EXPLICITLY](c26433.md) 함수 '% symbol% '은 (는) ' override '로 표시 되어야 합니다. [C. 128 참조: 가상 함수는 가상, 재정의 또는 최종 중 하나만 지정 해야](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)합니다.

[C26434 DONT_HIDE_METHODS](C26434.md) '% Symbol_1% ' 함수가 비가상 '% symbol_2% ' 함수를 숨깁니다. [ C++ 핵심 지침 C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)을 참조 하세요.

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) 함수 '% symbol% '은 (는) ' virtual ', ' override ' 또는 ' final ' 중 하나를 정확 하 게 지정 해야 합니다. [C. 128 참조: 가상 함수는 가상, 재정의 또는 최종 중 하나만 지정 해야](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)합니다.

[C26436 NEED_VIRTUAL_DTOR](C26436.md) 가상 함수를 사용 하는 '% symbol% ' 형식에는 공용 가상 또는 보호 된 비가상 소멸자가 필요 합니다. [ C++ 핵심 지침 C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual)를 참조 하세요.

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) 재정의 하는 소멸자는 명시적인 ' override ' 또는 ' virtual ' 지정자를 사용 하면 안 됩니다. [C. 128 참조: 가상 함수는 가상, 재정의 또는 최종 중 하나만 지정 해야](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)합니다.

## <a name="type-group"></a>형식 그룹

[C26437 DONT_SLICE](C26437.md) 조각화 하지 않습니다. [ C++ 핵심 지침](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice)(영문)을 참조 하세요.

## <a name="style-group"></a>스타일 그룹

[C26438 NO_GOTO](C26438.md) `goto`하지 마십시오. [ C++ 핵심 지침을 참조 하십시오. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>함수 그룹

[C26439 SPECIAL_NOEXCEPT](C26439.md) 이러한 종류의 함수는 throw 할 수 없습니다. `noexcept`선언 합니다. [ C++ 핵심 지침 F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)을 참조 하세요.

[C26440 DECLARE_NOEXCEPT](C26440.md) '% Symbol% ' 함수를 `noexcept`선언할 수 있습니다. [ C++ 핵심 지침 F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)을 참조 하세요.

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) 함수는 **noexcept** 로 선언 되지만 예외를 throw 할 수 있는 함수를 호출 합니다.
[핵심 지침: F. 6: 함수가 throw 할 수 없는 경우 noexcept으로 선언 합니다. C++ ](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)

## <a name="concurrency-group"></a>동시성 그룹

[C26441 NO_UNNAMED_GUARDS](C26441.md) 가드 개체의 이름은로 지정 해야 합니다. [ C++ 핵심 지침 cp. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks)를 참조 하세요.

## <a name="const-group"></a>CONST 그룹

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) '% Function% ' 함수에 대 한 참조 인수 '% argument% '은 (는) `const`로 표시 될 수 있습니다. [ C++ 핵심 지침 con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)을 참조 하세요.

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): '% function% ' 함수에 대 한 포인터 인수 '% argument% '은 (는) `const`포인터로 표시할 수 있습니다. [ C++ 핵심 지침 con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)을 참조 하세요.

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) '% Variable% '이 (가) 가리키는 값은 한 번만 할당 되며 `const`에 대 한 포인터로 표시 합니다. [ C++ 핵심 지침 con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)를 참조 하십시오.

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) '% Array% ' 배열의 요소는 한 번만 할당 되며, 요소는 `const`표시 됩니다. [ C++ 핵심 지침 con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)를 참조 하십시오.

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) '% Array% ' 배열의 요소에서 가리키는 값은 한 번만 할당 되며, `const`에 대 한 포인터로 요소를 표시 합니다. [ C++ 핵심 지침 con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)를 참조 하십시오.

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) 변수 '% variable% '은 (는) 한 번만 할당 되었으므로 `const`로 표시 하십시오. [ C++ 핵심 지침 con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)를 참조 하십시오.

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) 컴파일 시간 계산이 필요한 경우% function% 함수를 `constexpr`으로 표시할 수 있습니다. [ C++ 핵심 지침 F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr)를 참조 하세요.

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) 컴파일 시간 계산이 필요한 경우이 함수 호출% function%에서 `constexpr`를 사용할 수 있습니다. [ C++ 핵심 지침 con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr)를 참조 하십시오.

## <a name="type-group"></a>형식 그룹

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) `const`를 캐스트 하는 데 `const_cast`를 사용 하지 마세요. `const_cast` 필요 하지 않습니다. 상수 또는 변동성가이 변환에 의해 제거 되지 않습니다. [ C++ 핵심 지침 형식. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast)을 참조 하세요.

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) `static_cast` downcasts를 사용 하지 마세요. 다형 형식에서 캐스팅은 dynamic_cast을 사용 해야 합니다. [ C++ 핵심 지침 유형 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast)를 참조 하세요.

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) `reinterpret_cast`사용 하지 마세요. Void *에서 캐스트는 `static_cast`사용할 수 있습니다. [ C++ 핵심 지침 형식. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)을 참조 하세요.

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) 산술 변환에는 `static_cast`를 사용 하지 마세요. 중괄호 초기화, gsl:: narrow_cast를 사용 합니다. [ C++ 핵심 지침 형식. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)을 참조 하세요.

[C26473 NO_IDENTITY_CAST](C26473.md) 소스 형식과 대상 형식이 같은 포인터 형식 간에는 캐스팅 하지 마십시오. [ C++ 핵심 지침 형식. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)을 참조 하세요.

[C26474 NO_IMPLICIT_CAST](C26474.md) 변환이 암시적 일 수 있을 때는 포인터 형식 간에 캐스팅 하지 마십시오. [ C++ 핵심 지침 형식. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)을 참조 하세요.

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) 함수 스타일 C 캐스트를 사용 하지 마십시오. [ C++ 핵심 지침을 참조 하십시오. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) `reinterpret_cast`사용 하지 마세요. [ C++ 핵심 지침 형식. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)을 참조 하세요.

[C26491 NO_STATIC_DOWNCAST](c26490.md) `static_cast` downcasts를 사용 하지 마세요. [ C++ 핵심 지침 유형 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)를 참조 하세요.

[C26492 NO_CONST_CAST](c26492.md) `const`를 캐스트 하는 데 `const_cast`를 사용 하지 마세요. [ C++ 핵심 지침 형식. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)을 참조 하세요.

[C26493 NO_CSTYLE_CAST](c26493.md) C 스타일 캐스트를 사용 하지 마세요. [ C++ 핵심 지침 형식 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)를 참조 하십시오.

[C26494 VAR_USE_BEFORE_INIT](c26494.md) 변수 '% variable% '이 (가) 초기화 되지 않았습니다. 항상 개체를 초기화 합니다. [ C++ 핵심 지침 형식. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)를 참조 하세요.

[C26495 MEMBER_UNINIT](c26495.md) 변수 '% variable% '이 (가) 초기화 되지 않았습니다. 항상 멤버 변수를 초기화 합니다. [ C++ 핵심 지침 형식. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)을 참조 하세요.

## <a name="bounds-group"></a>범위 그룹

[C26446 USE_GSL_AT](c26446.md) 확인 되지 않은 첨자 연산자 대신 `gsl::at()`를 사용 하는 것이 좋습니다. [ C++ 핵심 지침: 범위를 참조 하세요. 4: 범위를 선택 하지 않은 표준 라이브러리 함수 및 형식을 사용 하지](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)않습니다.

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
포인터 산술 연산을 사용 하지 마세요. 범위를 대신 사용 합니다. [ C++ 핵심 지침 범위를 참조 하세요. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) 상수 식을 사용 하는 배열로만 인덱싱합니다. [ C++ 핵심 지침 범위를 참조 하세요. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) 값% value%이 (가) 범위를 벗어났습니다 (0,% bound%). '% variable% ' 변수입니다. 배열 범위 내에 있는 상수 식을 사용 하는 배열로 인덱싱. [ C++ 핵심 지침 범위를 참조 하세요. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) 식 '% expr% ': 포인터를 포인터로 감소 하지 않습니다. [ C++ 핵심 지침 범위를 참조 하세요. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL 그룹

[C26445 NO_SPAN_REF](c26445.md) `gsl::span` 또는 `std::string_view`에 대 한 참조는 수명 문제를 나타낼 수 있습니다.
[ C++ 핵심 지침 gsl을 참조 하세요. 보기: 뷰](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) 확인 되지 않은 첨자 연산자 대신 `gsl::at()`를 사용 하는 것이 좋습니다. [ C++ 핵심 지침: 범위를 참조 하세요. 4: 범위를 선택 하지 않은 표준 라이브러리 함수 및 형식을 사용 하지](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)않습니다.

[C26448 USE_GSL_FINALLY](c26448.md) 최종 동작을 의도 한 경우 `gsl::finally`를 사용 하는 것이 좋습니다. [ C++ 핵심 지침: gsl. util: 유틸리티](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities)를 참조 하세요.

임시를 무효화 하는 경우 [C26449 NO_SPAN_FROM_TEMPORARY](c26449.md)
`gsl::span` 또는 임시에서 만든 `std::string_view`는 유효 하지 않게 됩니다. [ C++ 핵심 지침: gsl. 뷰: 뷰](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)를 참조 하세요.

## <a name="deprecated-warnings"></a>사용 되지 않는 경고

다음 경고 핵심 지침 검사기는 초기 실험적 규칙 집합에 있는 있지만 이제 되지 않으며 무시 해도 됩니다. 경고는 위의 목록에서 경고로 대체 됩니다.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>참고 항목
[C++ 핵심 지침 검사기 사용](using-the-cpp-core-guidelines-checkers.md)
