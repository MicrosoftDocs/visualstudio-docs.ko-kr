---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework 사용 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c561555df40bc02c3c9f3090ee1de4c0f329bcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657179"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 `Microsoft::VisualStudio::CppUnitTestFramework` 네임스페이스의 public 구성원 목록을 제공합니다.

 헤더 파일은  _VisualStudio2012 [x86] installfolder_**\VC\UnitTest\include** 폴더에 있습니다.

 Lib 파일은  _VisualStudio2012 [x86] installfolder_**\VC\UnitTest\lib** 폴더에 있습니다.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용
 [CppUnitTest.h](#BKMK_CppUnitTest_h)

- [테스트 클래스와 메서드 만들기](#BKMK_Create_test_classes_and_methods)

- [초기화 및 정리](#BKMK_Initialize_and_cleanup)

  - [테스트 메서드](#BKMK_Test_methods)

  - [테스트 클래스](#BKMK_Test_classes)

  - [테스트 모듈](#BKMK_Test_modules)

- [테스트 특성 만들기](#BKMK_Create_test_attributes)

  - [테스트 메서드 특성](#BKMK_Test_method_attributes)

  - [테스트 클래스 특성](#BKMK_Test_class_attributes)

  - [테스트 모듈 특성](#BKMK_Test_module_attributes)

  - [미리 정의된 특성](#BKMK_Pre_defined_attributes)

    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)

  - [일반 어설션](#BKMK_General_Asserts)

    - [AreEqual](#BKMK_General_Are_Equal)

    - [AreNotEqual](#BKMK_General_Are_Not_Equal)

    - [AreSame](#BKMK_General_Are_Same)

    - [AreNotSame](#BKMK_General_Are_Not_Same)

    - [IsNull](#BKMK_General_Is_Null)

    - [IsNotNull](#BKMK_General_Is_Not_Null)

    - [IsTrue](#BKMK_General_Is_True)

    - [IsFalse](#BKMK_General_Is_False)

    - [Fail](#BKMK_General_Fail)

  - [Windows 런타임 어설션](#BKMK_WinRT_Asserts)

    - [AreEqual](#BKMK_WinRT_Are_Equal)

    - [AreSame](#BKMK_WinRT_Are_Same)

    - [AreNotEqual](#BKMK_WinRT_Are_Not_Equal)

    - [AreNotSame](#BKMK_WinRT_Are_Not_Same)

    - [IsNull](#BKMK_WinRT_Is_Null)

    - [IsNotNull](#BKMK_WinRT_Is_Not_Null)

  - [예외 어설션](#BKMK_Exception_Asserts)

    - [EXPECTEXCEPTION](#BKMK_Expect_Exception)

      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)

    - [Logger](#BKMK_Logger)

    - [메시지 작성](#BKMK_Write_Message)

## <a name="cppunittesth"></a><a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="BKMK_Create_test_classes_and_methods"></a> 테스트 클래스와 메서드 만들기

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

### <a name="initialize-and-cleanup"></a><a name="BKMK_Initialize_and_cleanup"></a> 초기화 및 정리

#### <a name="test-methods"></a><a name="BKMK_Test_methods"></a> 테스트 메서드

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 각 테스트 메서드를 실행하기 전에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_METHOD_INITIALIZE`는 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스에서 정의해야 합니다.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 각 테스트 메서드를 실행한 후에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_METHOD_CLEANUP`는 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스의 범위에서 정의해야 합니다.

#### <a name="test-classes"></a><a name="BKMK_Test_classes"></a> 테스트 클래스

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}

```

 각 테스트 클래스를 만든 후에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_CLASS_INITIALIZE`은 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스의 범위에서 정의해야 합니다.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}

```

 각 테스트 클래스를 만든 후에 실행되는 메서드로 *methodName*을 정의합니다. `TEST_CLASS_CLEANUP`은 테스트 클래스에서 한 번만 정의할 수 있으며 테스트 클래스의 범위에서 정의해야 합니다.

#### <a name="test-modules"></a><a name="BKMK_Test_modules"></a> 테스트 모듈

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

### <a name="create-test-attributes"></a><a name="BKMK_Create_test_attributes"></a> 테스트 특성 만들기

#### <a name="test-method-attributes"></a><a name="BKMK_Test_method_attributes"></a> 테스트 메서드 특성

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 하나 이상의 `TEST_METHOD_ATTRIBUTE` 매크로로 정의된 특성을 테스트 메서드 *testClassName*에 추가합니다.

 `TEST_METHOD_ATTRIBUTE` 매크로는 이름 *attributeName* 및 값 *attributeValue*를 사용하여 특성을 정의합니다.

#### <a name="test-class-attributes"></a><a name="BKMK_Test_class_attributes"></a> 테스트 클래스 특성

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 하나 이상의 `TEST_CLASS_ATTRIBUTE` 매크로로 정의된 특성을 테스트 클래스 *testClassName*에 추가합니다.

 `TEST_CLASS_ATTRIBUTE` 매크로는 이름 *attributeName* 및 값 *attributeValue*를 사용하여 특성을 정의합니다.

#### <a name="test-module-attributes"></a><a name="BKMK_Test_module_attributes"></a> 테스트 모듈 특성

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 하나 이상의 `TEST_MODULE_ATTRIBUTE` 매크로로 정의된 특성을 테스트 모듈 *testModuleName*에 추가합니다.

 `TEST_MODULE_ATTRIBUTE` 매크로는 이름 *attributeName* 및 값 *attributeValue*를 사용하여 특성을 정의합니다.

#### <a name="pre-defined-attributes"></a><a name="BKMK_Pre_defined_attributes"></a> 미리 정의된 특성
 위에서 설명한 매크로 `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` 또는 `TEST_MODULE_ATTRIBUTE` 매크로를 이러한 미리 정의된 특성 매크로로 대체할 수 있습니다.

```cpp
TEST_OWNER(ownerAlias)
```

 이름 `Owner` 및 특성 값 *ownerAlias*를 사용하여 특성을 정의합니다.

```cpp
TEST_DESCRIPTION(description)
```

 이름 `Description` 및 특성 값 *description*을 사용하여 특성을 정의합니다.

```cpp
TEST_PRIORITY(priority)
```

 이름 `Priority` 및 특성 값 *priority*를 사용하여 특성을 정의합니다.

```cpp
TEST_WORKITEM(workitem)
```

 이름 `WorkItem` 및 특성 값 *workItem*을 사용하여 특성을 정의합니다.

```cpp
TEST_IGNORE()
```

 이름 `Ignore` 및 특성 값 `true`를 사용하여 특성을 정의합니다.

## <a name="cppunittestasserth"></a><a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general-asserts"></a><a name="BKMK_General_Asserts"></a> 일반 어설션

#### <a name="are-equal"></a><a name="BKMK_General_Are_Equal"></a> AreEqual
 두 개체가 같은지 확인합니다.

```cpp
template<typename T>
static void AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 두 double이 같은지 확인합니다.

```cpp
static void AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 두 부동이 같은지 확인합니다.

```cpp
static void AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 두 char* 문자열이 같은지 확인합니다.

```cpp
static void AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 두 w_char* 문자열이 같은지 확인합니다.

```cpp
static void AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="BKMK_General_Are_Not_Equal"></a> AreNotEqual
 두 double이 같지 않은지 확인합니다.

```cpp
static void AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 두 부동이 같지 않은지 확인합니다.

```cpp
static void AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 두 char* 문자열이 같지 않은지 확인합니다.

```cpp
static void AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 두 w_char* 문자열이 같지 않은지 확인합니다.

```cpp
static void AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 operator==를 기준으로 하여 두 참조가 같지 않은지 확인합니다.

```cpp
template<typename T>
static void AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="BKMK_General_Are_Same"></a> AreSame
 두 참조가 같은 개체 인스턴스(ID)를 참조하는지 확인합니다.

```cpp
template<typename T>
static void AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="BKMK_General_Are_Not_Same"></a> AreNotSame
 두 참조가 같은 개체 인스턴스(ID)를 참조하지 않는지 확인합니다.

```cpp
template<typename T>
static void AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="BKMK_General_Is_Null"></a> IsNull
 포인터가 NULL인지 확인합니다.

```cpp
template<typename T>
static void IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="BKMK_General_Is_Not_Null"></a> IsNotNull
 포인터가 NULL이 아닌지 확인합니다.

```cpp
template<typename T>
static void IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="BKMK_General_Is_True"></a> IsTrue
 조건이 true인지 확인합니다.

```cpp
static void IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="BKMK_General_Is_False"></a> IsFalse
 조건이 false인지 확인합니다.

```cpp
static void IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="BKMK_General_Fail"></a> Fail
 테스트 사례가 실패한 것으로 강제 지정합니다.

```cpp
static void Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="BKMK_WinRT_Asserts"></a> Windows 런타임 어설션

#### <a name="are-equal"></a><a name="BKMK_WinRT_Are_Equal"></a> AreEqual
 두 Windows 런타임 포인터가 같은지 확인합니다.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 두 Platform::String^ 문자열이 같은지 확인합니다.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="BKMK_WinRT_Are_Same"></a> AreSame
 두 Windows 런타임 참조가 같은 개체를 참조하는지 확인합니다.

```
template<typename T>
static void AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="BKMK_WinRT_Are_Not_Equal"></a> AreNotEqual
 두 Windows 런타임 포인터가 같지 않은지 확인합니다.

```
template<typename T>
static void AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 두 Platform::String^ 문자열이 같지 않은지 확인합니다.

```
static void AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="BKMK_WinRT_Are_Not_Same"></a> AreNotSame
 두 Windows 런타임 참조가 같은 개체를 참조하지 않는지 확인합니다.

```
template<typename T>
static void AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="BKMK_WinRT_Is_Null"></a> IsNull
 Windows 런타임 포인터가 nullptr인지 확인합니다.

```
template<typename T>
static void IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="BKMK_WinRT_Is_Not_Null"></a> IsNotNull
 Windows 런타임 포인터가 nullptr이 아닌지 확인합니다.

```
template<typename T>
static void IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="BKMK_Exception_Asserts"></a> 예외 어설션

#### <a name="expect-exception"></a><a name="BKMK_Expect_Exception"></a> EXPECTEXCEPTION
 함수에서 예외가 발생하는지 확인합니다.

```
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 함수에서 예외가 발생하는지 확인합니다.

```
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h

### <a name="logger"></a><a name="BKMK_Logger"></a> Logger
 Logger 클래스는 기록 대상 정적 메서드를 포함합니다.

```
class Logger
```

### <a name="write-message"></a><a name="BKMK_Write_Message"></a> 메시지 작성

```
static void
Logger::WriteMessage(const wchar_t* message)
```

```
static void
Logger::WriteMessage(const char* message)
```

## <a name="example"></a>예
 아래 코드는 이 문서에서 설명한 VSCppUnit 사용법의 예입니다.

```
////////////////////////////////////////////////////////////
/* USAGE EXAMPLE
// The following is an example of VSCppUnit usage.
// It includes examples of attribute metadata, fixtures,
// unit tests with assertions, and custom logging.

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

## <a name="see-also"></a>관련 항목
 [코드 단위 테스트](../test/unit-test-your-code.md) [테스트 탐색기를 사용 하 여 네이티브 코드 테스트](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c) [기존 c + + 응용 프로그램에 단위 테스트 추가](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
