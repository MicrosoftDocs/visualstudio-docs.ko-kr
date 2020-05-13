---
title: C/C++ 어설션 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f7ac27b46252582b3982082a2a9a90a09223574f
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911616"
---
# <a name="cc-assertions"></a>C/C++ 어설션
어설션 문은 프로그램의 특정 지점에서 true로 간주되는 조건을 지정합니다. 해당 조건이 true가 아니면 어설션이 실패하고, 프로그램 실행이 중단되며, [어설션 실패 대화 상자](../debugger/assertion-failed-dialog-box.md)가 나타납니다.

Visual Studio는 C++ 다음 구문을 기반으로 하는 어설션 문을 지원 합니다.

- MFC 프로그램의 MFC 어설션

- ATL을 사용하는 프로그램에 대한 [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert).

- C 런타임 라이브러리를 사용하는 프로그램에 대한 CRT 어설션.

- 다른 C/C++ 프로그램에 대한 ANSI [assert 함수](/cpp/c-runtime-library/reference/assert-macro-assert-wassert).

   어설션을 사용하여 논리 오류를 catch하고, 작업의 결과를 확인하고, 처리해야 하는 오류 조건을 테스트할 수 있습니다.

## <a name="BKMK_In_this_topic"></a> 항목 내용
[어설션 작동 방법](#BKMK_How_assertions_work)

[디버그 및 릴리스 빌드의 어설션](#BKMK_Assertions_in_Debug_and_Release_builds)

[어설션을 사용할 경우의 부작용](#BKMK_Side_effects_of_using_assertions)

[CRT 어설션](#BKMK_CRT_assertions)

[MFC 어설션](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID 및 CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [AssertValid의 제한 사항](#BKMK_Limitations_of_AssertValid)

  [어설션 사용](#BKMK_Using_assertions)

- [논리 오류 catch](#BKMK_Catching_logic_errors)

- [결과 확인](#BKMK_Checking_results_)

- [처리 되지 않은 오류 찾기](#BKMK_Testing_error_conditions_)

## <a name="BKMK_How_assertions_work"></a>어설션 작동 방법
MFC 또는 C 런타임 라이브러리 어설션으로 인해 디버거가 중단되면 소스를 사용할 수 있는 경우 디버거는 어설션이 발생한 소스 파일의 지점으로 이동합니다. 어설션 메시지는 [출력 창](../ide/reference/output-window.md)과 **어설션 실패** 대화 상자에 모두 나타납니다. 나중에 참조할 수 있도록 저장하려면 **출력** 창에서 텍스트 창으로 어설션 메시지를 복사할 수 있습니다. **출력** 창에는 다른 오류 메시지도 포함될 수 있습니다. 이러한 메시지는 어설션 실패의 원인에 대한 단서를 제공하므로 신중하게 검토합니다.

어설션을 사용하여 개발 중에 오류를 검색합니다. 규칙으로 가정마다 하나의 어설션을 사용합니다. 예를 들어 인수가 NULL이 아닌 것으로 가정하는 경우 어설션을 사용하여 해당 가정을 테스트합니다.

[항목 내용](#BKMK_In_this_topic)

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>디버그 및 릴리스 빌드의 어설션
`_DEBUG`가 정의된 경우에만 어설션 문이 컴파일됩니다. 그렇지 않으면 컴파일러는 어설션을 null 문으로 처리합니다. 따라서 어설션 문은 최종 릴리스 프로그램에서 오버헤드나 성능 비용을 부과하지 않으며 `#ifdef` 지시문 사용을 피할 수 있습니다.

## <a name="BKMK_Side_effects_of_using_assertions"></a>어설션을 사용할 경우의 부작용
코드에 어설션을 추가하는 경우 어설션에 부작용이 없는지 확인합니다. 예를 들어 `nM` 값을 수정하는 다음 어설션을 고려해 보세요.

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

`ASSERT` 식은 프로그램의 릴리스 버전에서 계산 되지 않기 때문에 디버그 및 릴리스 버전에는 `nM` 값이 다릅니다. MFC에서이 문제를 방지 하기 위해 `ASSERT` 대신 [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) 매크로를 사용할 수 있습니다. `VERIFY`는 모든 버전의 식을 계산 하지만 릴리스 버전의 결과를 확인 하지는 않습니다.

함수를 계산할 때 예기치 않은 부작용이 발생할 수 있으므로 어설션 문에서 함수 호출을 사용하는 데 특히 주의해야 합니다.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY`는 디버그 버전과 릴리스 버전 모두에서 `myFnctn`를 호출하여 사용할 수 있습니다. 그러나 `VERIFY`를 사용하면 릴리스 버전에서 불필요한 함수 호출의 오버헤드가 발생합니다.

[항목 내용](#BKMK_In_this_topic)

## <a name="BKMK_CRT_assertions"></a>CRT 어설션
CRTDBG.H 헤더 파일은 어설션 검사를 위한 [_ASSERT 및 _ASSERTE 매크로](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros)를 정의합니다.

| 매크로 | 결과 |
|------------| - |
| `_ASSERT` | 지정 된 식이 FALSE 이면 `_ASSERT`파일 이름과 줄 번호를 반환 합니다. |
| `_ASSERTE` | `_ASSERT`와 같으며 어설션된 식의 문자열 표현을 포함 합니다. |

`_ASSERTE`는 FALSE로 판명된 어설션된 식을 보고하므로 더 강력합니다. 이는 소스 코드를 참조하지 않고 문제를 식별하는 데 충분할 수 있습니다. 그러나 응용 프로그램의 디버그 버전에는 `_ASSERTE`를 사용하여 어설션된 각 식에 대한 문자열 상수가 포함됩니다. 많은 `_ASSERTE` 매크로를 사용하는 경우 이러한 문자열 식은 많은 양의 메모리를 차지합니다. 이로 인해 문제가 발생하는 경우 `_ASSERT`를 사용하여 메모리를 절약합니다.

`_DEBUG` 정의 된 경우 `_ASSERTE` 매크로는 다음과 같이 정의 됩니다.

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

어설션된 식이 FALSE로 평가되면 [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)가 호출되어 어설션 오류를 보고합니다(기본적으로 메시지 대화 상자 사용). 메시지 대화 상자에서 **다시 시도**를 선택하는 경우 `_CrtDbgReport`는 1을 반환하고 `_CrtDbgBreak`는 `DebugBreak`를 통해 디버거를 호출합니다.

### <a name="checking-for-heap-corruption"></a>힙 손상 확인
다음 예제에서는 [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)를 사용하여 힙이 손상되었는지 확인합니다.

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>포인터 유효성 검사
다음 예제에서는 [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer)를 사용하여 지정된 메모리 범위가 읽기 또는 쓰기에 유효한지 확인합니다.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

다음 예제에서는 [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer)를 사용하여 로컬 힙의 메모리를 가리키는 포인터를 확인합니다. (이는 C 런타임 라이브러리의 이 인스턴스에 의해 생성 및 관리되는 힙입니다. DLL에는 자체 라이브러리 인스턴스가 포함될 수 있으며, 그에 따라 응용 프로그램 힙 외부에 고유한 힙이 있습니다.) 이 어설션은 null 또는 범위를 벗어난 주소 뿐만 아니라 정적 변수, 스택 변수 및 기타 비로컬 메모리에 대한 포인터를 catch합니다.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>메모리 블록 확인
다음 예제에서는 [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock)를 사용하여 메모리 블록이 로컬 힙에 있고 올바른 블록 형식을 사용하는지 확인합니다.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[항목 내용](#BKMK_In_this_topic)

## <a name="BKMK_MFC_assertions"></a>MFC 어설션
MFC는 어설션 검사를 위한 [ASSERT](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) 매크로를 정의 합니다. 또한 `CObject`파생 개체의 내부 상태를 확인 하는 `MFC ASSERT_VALID` 및 `CObject::AssertValid` 메서드를 정의 합니다.

MFC `ASSERT` 매크로의 인수가 0 또는 false로 평가되는 경우 매크로는 프로그램 실행을 중단하고 사용자에 게 경고합니다. 그렇지 않으면 실행이 계속됩니다.


어설션이 실패하면 메시지 대화 상자에 소스 파일의 이름과 어설션의 줄 번호가 표시됩니다. 대화 상자에서 다시 시도를 선택하면 [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak)에 대한 호출로 인해 실행이 디버거로 중단됩니다. 이 시점에서 호출 스택을 검사하고 다른 디버거 기능을 사용하여 어설션이 실패한 이유를 확인할 수 있습니다. [Just-in-time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)을 사용하도록 설정하고 디버거가 아직 실행되지 않은 경우 대화 상자에서 디버거를 시작할 수 있습니다.

다음 예에서는 `ASSERT`를 사용하여 함수의 반환 값을 확인하는 방법을 보여줍니다.

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

[IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) 함수와 함께 ASSERT를 사용하여 함수 인수에 대한 형식 검사를 제공할 수 있습니다.

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

`ASSERT` 매크로는 릴리스 버전에서 코드를 생성 하지 않습니다. 릴리스 버전에서 식을 평가 해야 하는 경우 ASSERT 대신 [VERIFY](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) 매크로를 사용 합니다.

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID 및 CObject:: AssertValid
[CObject:: AssertValid](/cpp/mfc/reference/cobject-class#assertvalid) 메서드는 개체의 내부 상태에 대한 런타임 검사를 제공합니다. `CObject`에서 클래스를 파생시킬 때 `AssertValid`를 재정의할 필요는 없지만, 이를 통해 클래스를 더욱 안정적으로 만들 수 있습니다. `AssertValid`는 모든 개체의 멤버 변수에 대해 어설션을 수행하여 유효한 값이 포함되어 있는지 확인해야 합니다. 예를 들어 포인터 멤버 변수가 NULL이 아닌 것을 확인해야 합니다.

다음 예제에서는 `AssertValid` 함수를 선언 하는 방법을 보여 줍니다.

```cpp
class CPerson : public CObject
{
protected:
    CString m_strName;
    float   m_salary;
public:
#ifdef _DEBUG
    // Override
    virtual void AssertValid() const;
#endif
    // ...
};
```

`AssertValid`를 재정의하는 경우 고유한 검사를 수행하기 전에 `AssertValid`의 기본 클래스 버전을 호출합니다. 그런 다음 ASSERT 매크로를 사용하여 다음과 같이 파생 클래스에 고유한 멤버를 확인합니다.

```cpp
#ifdef _DEBUG
void CPerson::AssertValid() const
{
    // Call inherited AssertValid first.
    CObject::AssertValid();

    // Check CPerson members...
    // Must have a name.
    ASSERT( !m_strName.IsEmpty());
    // Must have an income.
    ASSERT( m_salary > 0 );
}
#endif
```

멤버 변수에 개체를 저장하는 경우 `ASSERT_VALID` 매크로를 사용하여 해당 클래스가 `AssertValid`를 재정의하는 경우 내부 유효성을 테스트할 수 있습니다.

예를 들어 [CObList](/cpp/mfc/reference/coblist-class) 를 해당 멤버 변수 중 하나에 저장 하는 클래스 `CMyData`를 생각해 보겠습니다. `CObList` 변수 `m_DataList`는 `CPerson` 개체의 컬렉션을 저장 합니다. `CMyData`의 약식 선언은 다음과 같습니다.

```cpp
class CMyData : public CObject
{
    // Constructor and other members ...
    protected:
        CObList* m_pDataList;
    // Other declarations ...
    public:
#ifdef _DEBUG
        // Override:
        virtual void AssertValid( ) const;
#endif
    // And so on ...
};
```

`CMyData`에서 `AssertValid` 재정의는 다음과 같습니다.

```cpp
#ifdef _DEBUG
void CMyData::AssertValid( ) const
{
    // Call inherited AssertValid.
    CObject::AssertValid( );
    // Check validity of CMyData members.
    ASSERT_VALID( m_pDataList );
    // ...
}
#endif
```

`CMyData`는 `AssertValid` 메커니즘을 사용하여 데이터 멤버에 저장된 개체의 유효성을 테스트합니다. `CMyData`의 재정의 `AssertValid`는 자체 m_pDataList 멤버 변수에 대해 `ASSERT_VALID` 매크로를 호출합니다.

클래스 `CObList`도 `AssertValid`를 재정의하므로 유효성 테스트는 이 수준에서 중지되지 않습니다. 이 재정의는 목록의 내부 상태에서 추가 유효성 테스트를 수행합니다. 따라서 `CMyData` 개체에 대한 유효성 테스트는 저장된 `CObList` 목록 개체의 내부 상태에 대한 추가 유효성 테스트를 발생시킵니다.

몇 가지 추가 작업을 통해 목록에 저장된 `CPerson` 개체에 대한 유효성 테스트를 추가할 수도 있습니다. `CObList`에서 `CPersonList` 클래스를 파생시키고 `AssertValid`를 재정의할 수 있습니다. 재정의에서 `CObject::AssertValid`를 호출한 다음 목록 전체를 반복하여 목록에 저장된 각 `CPerson` 개체의 `AssertValid`를 호출합니다. 이 항목의 시작 부분에 표시된 `CPerson` 클래스는 이미 `AssertValid`를 재정의합니다.

이는 디버깅을 위해 빌드할 때 강력한 메커니즘입니다. 이후에 릴리스를 빌드할 때 메커니즘이 자동으로 꺼집니다.

### <a name="BKMK_Limitations_of_AssertValid"></a>AssertValid의 제한 사항
트리거된 어설션은 개체가 명확히 잘못되었음을, 그리고 실행이 중지될 것임을 나타냅니다. 그러나 어설션이 없다는 것은 발견된 문제가 없음을 나타내지만 개체는 양호하지 않을 수 있습니다.

[항목 내용](#BKMK_In_this_topic)

## <a name="BKMK_Using_assertions"></a>어설션 사용

### <a name="BKMK_Catching_logic_errors"></a>논리 오류 catch
프로그램의 논리에 따라 true여야 하는 조건에 대한 어설션을 설정할 수 있습니다. 논리 오류가 발생하지 않으면 어설션이 적용되지 않습니다.

예를 들어, 컨테이너에서 가스 분자를 시뮬레이션하고 `numMols` 변수는 총 분자 수를 나타냅니다. 이 숫자는 0보다 작지 않으므로 다음과 같은 MFC 어설션 문을 포함할 수 있습니다.

```cpp
ASSERT(numMols >= 0);
```

또는 다음과 같은 CRT 어설션을 포함할 수 있습니다.

```cpp
_ASSERT(numMols >= 0);
```

이러한 문은 프로그램이 제대로 작동하는 경우 아무 작업도 수행하지 않습니다. 논리 오류로 인해 `numMols`가 0보다 작은 경우 어설션이 프로그램 실행을 중단하고 [어설션 실패 대화 상자](../debugger/assertion-failed-dialog-box.md)를 표시합니다.

[항목 내용](#BKMK_In_this_topic)

### <a name="BKMK_Checking_results_"></a>결과 확인
어설션은 빠른 시각적 검사에서 결과가 명확 하지 않은 작업을 테스트 하는 데 유용 합니다.

예를 들어 다음 코드를 고려 하 여 `mols`에서 가리키는 연결 된 목록의 내용을 기반으로 `iMols` 변수를 업데이트 합니다.

```cpp
/* This code assumes that type has overloaded the != operator
 with const char *
It also assumes that H2O is somewhere in that linked list.
Otherwise we'll get an access violation... */
while (mols->type != "H2O")
{
    iMols += mols->num;
    mols = mols->next;
}
ASSERT(iMols<=numMols); // MFC version
_ASSERT(iMols<=numMols); // CRT version
```

`iMols`에서 계산 되는 molecules의 수는 항상 `numMols`총 molecules 수보다 작거나 같아야 합니다. 루프를 시각적으로 검사 하는 경우에는 반드시 필요한 것으로 표시 되지 않으므로 루프에서 해당 조건을 테스트할 때 어설션 문이 사용 됩니다.

[항목 내용](#BKMK_In_this_topic)

### <a name="BKMK_Testing_error_conditions_"></a>처리 되지 않은 오류 찾기
어설션을 사용하여 오류를 처리해야 하는 코드의 특정 지점에서 오류 조건을 테스트할 수 있습니다. 다음 예에서는 그래픽 루틴이 성공에 대해 오류 코드 또는 0을 반환합니다.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

오류 처리 코드가 제대로 작동하는 경우 오류를 처리하고 어설션에 도달하기 전에 `myErr`이 0으로 다시 설정됩니다. `myErr`에 다른 값이 있으면 어설션이 실패하고 프로그램이 중단되며 [어설션 실패 대화 상자](../debugger/assertion-failed-dialog-box.md)가 나타납니다.

그러나 어설션 문은 오류 처리 코드를 대체 하지 않습니다. 다음 예에서는 최종 릴리스 코드의 문제를 일으킬 수 있는 어설션 문을 보여 줍니다.

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

이 코드는 어설션 문을 사용하여 오류 조건을 처리합니다. 따라서 `myGraphRoutine`에서 반환되는 오류 코드는 최종 릴리스 코드에서 처리되지 않습니다.

[항목 내용](#BKMK_In_this_topic)

## <a name="see-also"></a>참조

- [디버거 보안](../debugger/debugger-security.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
- [관리 코드에 어설션 사용](../debugger/assertions-in-managed-code.md)
