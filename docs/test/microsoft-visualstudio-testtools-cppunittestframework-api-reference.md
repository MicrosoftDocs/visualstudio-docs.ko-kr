---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jillfra
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 8a71b6d406b7507930a5d1a7ce593a296220d5a6
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278653"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework API 참조

이 항목에서는 `Microsoft::VisualStudio::CppUnitTestFramework` 네임스페이스의 public 구성원 목록을 제공합니다. 이 API를 사용하여 Microsoft Native Unit Test Framework를 기반으로 C++ 단위 테스트를 작성합니다. 이 항목의 마지막에는 [사용 예제](#example)가 있습니다.

헤더 및 lib 파일은 *\<Visual Studio 설치 폴더>\VC\Auxiliary\VS\UnitTest*에 있습니다.

헤더 및 라이브러리 경로는 기본 테스트 프로젝트에서 자동으로 구성됩니다.

## <a name="In_this_topic"></a> 항목 내용

[CppUnitTest.h](#cppUnitTest_h)

- [테스트 클래스와 메서드 만들기](#create_test_classes_and_methods)

- [초기화 및 정리](#Initialize_and_cleanup)

  - [테스트 메서드](#test_methods)

  - [테스트 클래스](#test_classes)

  - [테스트 모듈](#test_modules)

- [테스트 특성 만들기](#create_test_attributes)

  - [테스트 메서드 특성](#test_method_attributes)

  - [테스트 클래스 특성](#test_class_attributes)

  - [테스트 모듈 특성](#test_module_attributes)

  - [미리 정의된 특성](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [일반 어설션](#general_asserts)

    - [AreEqual](#general_are_equal)

    - [AreNotEqual](#general_are_not_equal)

    - [AreSame](#general_are_same)

    - [AreNotSame](#general_are_not_same)

    - [IsNull](#general_is_null)

    - [IsNotNull](#general_is_not_null)

    - [IsTrue](#general_is_True)

    - [IsFalse](#general_is_false)

    - [Fail](#general_Fail)

  - [Windows 런타임 어설션](#winrt_asserts)

    - [AreEqual](#winrt_are_equal)

    - [AreSame](#winrt_are_same)

    - [AreNotEqual](#winrt_are_not_equal)

    - [AreNotSame](#winrt_are_not_same)

    - [IsNull](#winrt_is_null)

    - [IsNotNull](#winrt_is_not_null)

  - [예외 어설션](#exception_asserts)

    - [EXPECTEXCEPTION](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Logger](#logger)

    - [메시지 작성](#write_message)

  - [사용 예제](#example)

## <a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create_test_classes_and_methods"></a> 테스트 클래스와 메서드 만들기

```cpp
TEST_CLASS(className)
```

테스트 메서드를 포함하는 각 클래스에 필요합니다. *className*을 테스트 클래스로 식별합니다. 네임스페이스 범위에서 `TEST_CLASS`를 선언해야 합니다.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

*methodName*을 테스트 메서드로 정의합니다. 메서드의 클래스 범위에서 `TEST_METHOD`를 선언해야 합니다.

### <a name="Initialize_and_cleanup"></a> 초기화 및 정리

#### <a name="test_methods"></a> 테스트 메서드

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

각 테스트 메서드를 실행하기 전에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_METHOD_INITIALIZE`는 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스의 범위에서 정의해야 합니다.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

각 테스트 메서드를 실행한 후에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_METHOD_CLEANUP`는 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스의 범위에서 정의해야 합니다.

#### <a name="test_classes"></a> 테스트 클래스

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

각 테스트 클래스를 만들기 전에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_CLASS_INITIALIZE`는 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스의 범위에서 정의해야 합니다.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

각 테스트 클래스를 만든 후에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_CLASS_CLEANUP`은 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스의 범위에서 정의해야 합니다.

#### <a name="test_modules"></a> 테스트 모듈

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

모듈을 로드할 때 실행되는 메서드 *methodName*을 정의합니다. `TEST_MODULE_INITIALIZE`는 테스트 모듈에서 한 번만 정의할 수 있으며 네임스페이스 범위에서 선언해야 합니다.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

모듈을 언로드할 때 실행되는 메서드 *methodName*을 정의합니다. `TEST_MODULE_CLEANUP`은 테스트 모듈에서 한 번만 정의할 수 있으며 네임스페이스 범위에서 선언해야 합니다.

### <a name="create_test_attributes"></a> 테스트 특성 만들기

#### <a name="test_method_attributes"></a> 테스트 메서드 특성

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

하나 이상의 `TEST_METHOD_ATTRIBUTE` 매크로로 정의된 특성을 테스트 메서드 *testMethodName*에 추가합니다.

`TEST_METHOD_ATTRIBUTE` 매크로는 이름 *attributeName* 및 값 *attributeValue*를 사용하여 특성을 정의합니다.

#### <a name="test_class_attributes"></a> 테스트 클래스 특성

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

하나 이상의 `TEST_CLASS_ATTRIBUTE` 매크로로 정의된 특성을 테스트 클래스 *testClassName*에 추가합니다.

`TEST_CLASS_ATTRIBUTE` 매크로는 이름 *attributeName* 및 값 *attributeValue*를 사용하여 특성을 정의합니다.

#### <a name="test_module_attributes"></a> 테스트 모듈 특성

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

하나 이상의 `TEST_MODULE_ATTRIBUTE` 매크로로 정의된 특성을 테스트 모듈 *testModuleName*에 추가합니다.

`TEST_MODULE_ATTRIBUTE` 매크로는 이름 *attributeName* 및 값 *attributeValue*를 사용하여 특성을 정의합니다.

#### <a name="pre_defined_attributes"></a> 미리 정의된 특성

미리 정의된 이러한 특성 매크로는 일반적인 경우에 간편하게 사용할 수 있도록 제공됩니다. 위에서 설명한 `TEST_METHOD_ATTRIBUTE` 매크로 대신 사용할 수 있습니다.

```cpp
TEST_OWNER(ownerAlias)
```

이름 `Owner` 및 특성 값 *ownerAlias*를 사용하여 `TEST_METHOD_ATTRIBUTE`를 정의합니다.

```cpp
TEST_DESCRIPTION(description)
```

이름 `Description` 및 특성 값 *description*을 사용하여 `TEST_METHOD_ATTRIBUTE`를 정의합니다.

```cpp
TEST_PRIORITY(priority)
```

이름 `Priority` 및 특성 값 *priority*를 사용하여 `TEST_METHOD_ATTRIBUTE`를 정의합니다.

```cpp
TEST_WORKITEM(workitem)
```

이름 `WorkItem` 및 특성 값 *workItem*을 사용하여 `TEST_METHOD_ATTRIBUTE`를 정의합니다.

```cpp
TEST_IGNORE()
```

이름 `Ignore` 및 특성 값 `true`를 사용하여 `TEST_METHOD_ATTRIBUTE`를 정의합니다.

## <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general_asserts"></a> 일반 어설션

#### <a name="general_are_equal"></a> AreEqual
두 개체가 같은지 확인합니다.

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

두 double이 같은지 확인합니다.

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

두 부동이 같은지 확인합니다.

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

두 char* 문자열이 같은지 확인합니다.

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

두 w_char* 문자열이 같은지 확인합니다.

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_equal"></a> AreNotEqual
두 double이 같지 않은지 확인합니다.

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

두 부동이 같지 않은지 확인합니다.

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

두 char* 문자열이 같지 않은지 확인합니다.

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

두 w_char* 문자열이 같지 않은지 확인합니다.

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

operator==를 기준으로 하여 두 참조가 같지 않은지 확인합니다.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_same"></a> AreSame
두 참조가 같은 개체 인스턴스(ID)를 참조하는지 확인합니다.

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_same"></a> AreNotSame
두 참조가 같은 개체 인스턴스(ID)를 참조하지 않는지 확인합니다.

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_null"></a> IsNull
포인터가 NULL인지 확인합니다.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_not_null"></a> IsNotNull
포인터가 NULL이 아닌지 확인합니다.

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_True"></a> IsTrue
조건이 true인지 확인합니다.

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_false"></a> IsFalse
조건이 false인지 확인합니다.

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_Fail"></a> Fail
테스트 사례가 실패한 것으로 강제 지정합니다.

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="winrt_asserts"></a> Windows 런타임 어설션

#### <a name="winrt_are_equal"></a> AreEqual
두 Windows 런타임 포인터가 같은지 확인합니다.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

두 Platform::String^ 문자열이 같은지 확인합니다.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_same"></a> AreSame
두 Windows 런타임 참조가 같은 개체를 참조하는지 확인합니다.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_equal"></a> AreNotEqual
두 Windows 런타임 포인터가 같지 않은지 확인합니다.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

두 Platform::String^ 문자열이 같지 않은지 확인합니다.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_same"></a> AreNotSame
두 Windows 런타임 참조가 같은 개체를 참조하지 않는지 확인합니다.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_null"></a> IsNull
Windows 런타임 포인터가 nullptr인지 확인합니다.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_not_null"></a> IsNotNull
Windows 런타임 포인터가 nullptr이 아닌지 확인합니다.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception_asserts"></a> 예외 어설션

#### <a name="expect_exception"></a> EXPECTEXCEPTION
함수에서 예외가 발생하는지 확인합니다.

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

함수에서 예외가 발생하는지 확인합니다.

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

### <a name="logger"></a> Logger
Logger 클래스는 **출력 창**에 작성하는 정적 메서드를 포함합니다.

### <a name="write_message"></a> 메시지 작성
**출력 창**에 문자열 작성

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a> 예
이 코드는 VSCppUnit 사용 예입니다. 여기에는 특성 메타데이터, 장치, 어셜션 포함 단위 테스트, 사용자 지정 로깅이 포함됩니다.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>참조

- [코드 단위 테스트](../test/unit-test-your-code.md)
- [C/C++에 대한 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)
