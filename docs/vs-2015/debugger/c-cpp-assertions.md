---
title: C-C + + 어설션 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c26cc17d00881a72928806089a4c2880fdbce2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702337"
---
# <a name="cc-assertions"></a>C/C++ 어설션
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

어설션 문은 프로그램의 특정 지점에서 true로 간주되는 조건을 지정합니다. 지정한 조건이 true가 아니면 어설션이 실패하고 프로그램 실행이 중단되며 [ 어설션 실패 대화 상자](../debugger/assertion-failed-dialog-box.md)가 나타납니다.  

 Visual C++는 다음 구문을 기반으로 하는 어설션 문을 지원 합니다.  

- MFC 프로그램의 MFC 어설션  

- ATL을 사용하는 프로그램의 [ATLASSERT](https://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3)  

- C 런타임 라이브러리를 사용하는 프로그램의 CRT 어설션  

- 기타 C/C++ 프로그램의 ANSI [assert 함수](https://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40)  

  어설션을 사용하여 논리 오류를 포착하고 작업 결과를 확인하며 처리해야 하는 오류 조건을 테스트할 수 있습니다.  

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용  
 [어설션 작동 방식](#BKMK_How_assertions_work)  

 [디버그 및 릴리스 빌드의 어설션](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [어설션 사용의 부작용](#BKMK_Side_effects_of_using_assertions)  

 [CRT 어설션](#BKMK_CRT_assertions)  

 [MFC 어설션](#BKMK_MFC_assertions)  

- [MFC ASSERT_VALID 및 CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [AssertValid 제한 사항](#BKMK_Limitations_of_AssertValid)  

  [어설션 사용](#BKMK_Using_assertions)  

- [논리 오류 포착](#BKMK_Catching_logic_errors)  

- [결과 확인](#BKMK_Checking_results_)  

- [처리되지 않은 오류 찾기](#BKMK_Testing_error_conditions_)  

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> 어설션 작동 방식  
 MFC 또는 C 런타임 라이브러리 어설션으로 인해 디버거가 중지된 경우 소스를 사용할 수 있으면 디버거는 소스 파일에서 어설션이 발생한 지점으로 이동합니다. 어설션 메시지는 [출력 창](../ide/reference/output-window.md)과 **어설션 실패** 대화 상자 모두에 나타납니다. 어설션 메시지를 나중에 참조할 수 있도록 저장하려면 **출력** 창에서 텍스트 창으로 복사하면 됩니다. **출력** 창에는 다른 오류 메시지도 포함될 수 있습니다. 이러한 메시지는 어설션 실패의 원인에 대한 단서를 제공하기 때문에 주의 깊게 검토합니다.  

 어설션을 사용하여 개발 중에 오류를 감지합니다. 대체로, 가정마다 하나의 어설션을 사용합니다. 예를 들어, 인수가 NULL이 아니라고 가정하면 이 가정을 테스트하는 하나의 어설션을 사용합니다.  

 [항목 내용](#BKMK_In_this_topic)  

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> 디버그 및 릴리스 빌드의 어설션  
 어설션 문은 `_DEBUG`가 정의된 경우에만 컴파일됩니다. 그렇지 않으면 컴파일러가 어설션을 Null 문으로 간주합니다. 따라서 어설션 문은 최종 릴리스 프로그램에서 오버헤드나 성능 비용을 부과하지 않으며 `#ifdef` 지시문을 사용하지 않아도 됩니다.  

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> 어설션 사용의 부작용  
 코드에 어설션을 추가하는 경우에는 어설션에 부작용이 없는지 확인합니다. 예를 들어, `nM` 값을 수정하는 다음과 같은 어설션이 있습니다.  

```  
ASSERT(nM++ > 0); // Don't do this!  

```  

 `ASSERT` 식은 프로그램 릴리스 버전에서 계산되지 않기 때문에 `nM` 값이 디버그 버전과 릴리스 버전에서 다릅니다. MFC에서 이런 문제를 피하기 위해 `ASSERT` 대신 [VERIFY](https://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) 매크로를 사용할 수 있습니다.  `VERIFY`는 모든 버전에서 식을 계산하지만 릴리스 버전에서는 결과를 확인하지 않습니다.  

 어설션 문에서 함수 호출을 사용할 때는 특히 주의해야 합니다. 함수를 계산하면 예기치 않은 부작용이 발생할 수 있기 때문입니다.  

```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY`는 디버그 및 릴리스 버전 모두에서 `myFnctn`을 호출하기 때문에 사용할 수 있습니다. 하지만 `VERIFY`를 사용하면 릴리스 버전에서 불필요한 함수 호출의 오버헤드가 발생합니다.  

 [항목 내용](#BKMK_In_this_topic)  

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> CRT 어설션  
 CRTDBG.H 헤더 파일은 어설션 검사를 위한 [_ASSERT 및 _ASSERTE 매크로](https://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36)를 정의합니다.  

|   매크로    |                                             결과                                              |
|------------|-------------------------------------------------------------------------------------------------|
| `_ASSERT`  | 지정된 식이 FALSE로 평가되는 경우 `_ASSERT`의 파일 이름 및 줄 번호입니다. |
| `_ASSERTE` |      `_ASSERT`와 동일하며, 어설션된 식의 문자열 표현이 추가된 것입니다.       |

 `_ASSERTE`는 FALSE로 판명된 어설션된 식을 보고하기 때문에 더욱 강력합니다. 소스 코드를 참조하지 않고 문제를 식별하기에 충분할 수 있습니다. 하지만 애플리케이션의 디버그 버전에 `_ASSERTE`를 사용하여 어설션된 각 식에 대한 문자열 상수가 포함됩니다. 많은 `_ASSERTE` 매크로를 사용하면 이러한 문자열 식이 상당한 양의 메모리를 차지합니다. 이것이 문제로 판명되면 `_ASSERT`를 사용하여 메모리를 절약합니다.  

 `_DEBUG`가 정의되면 `_ASSERTE` 매크로는 다음과 같이 정의됩니다.  

```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 어설션된 식이 FALSE로 평가되면 [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)가 호출되어 어설션 실패를 보고합니다(기본적으로 메시지 대화 상자를 사용). 메시지 대화 상자에서 **다시 시도**를 선택하면 `_CrtDbgReport`는 1을 반환하고 `_CrtDbgBreak`는 `DebugBreak`를 통해 디버거를 호출합니다.  

### <a name="checking-for-heap-corruption"></a>힙 손상 여부 확인  
 다음 예제는 [_CrtCheckMemory](https://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765)를 사용하여 힙 손상 여부를 검사합니다.  

```  
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>포인터 유효성 검사  
 다음 예제는 [_CrtIsValidPointer](https://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa)를 사용하여 지정된 메모리 범위가 읽기 또는 쓰기에 유효한지 확인합니다.  

```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 다음 예제는 [_CrtIsValidHeapPointer](https://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5)를 사용하여 포인터가 로컬 힙의 메모리를 가리키는지 확인합니다. (C 런타임 라이브러리 인스턴스로 생성 및 관리되는 힙 — DLL은 라이브러리의 자체 인스턴스를 포함할 수 있으므로 애플리케이션 힙 외부에 자체 힙을 포함할 수 있습니다.) 이 어설션은 Null 또는 범위를 벗어난 주소뿐만 아니라 정적 변수, 스택 변수 및 기타 비로컬 메모리에 대한 포인터도 포착합니다.  

```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>메모리 블록 확인  
 다음 예제는 [_CrtIsMemoryBlock](https://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273)을 사용하여 메모리 블록이 로컬 힙에 있고 유효한 블록 유형을 사용하는지 확인합니다.  

```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [항목 내용](#BKMK_In_this_topic)  

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> MFC 어설션  
 MFC는 어설션 검사를 위한 [ASSERT](https://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) 매크로를 정의합니다. 또한 `CObject` 파생 개체의 내부 상태를 확인하는 `MFC ASSERT_VALID` 및 `CObject::AssertValid` 메서드를 정의합니다.  

 MFC `ASSERT` 매크로의 인수가 0 또는 false로 평가되면 매크로는 프로그램 실행을 중지하고 사용자에게 경고합니다. 그렇지 않으면 실행이 계속됩니다.  

 어설션이 실패하면 메시지 대화 상자에 소스 파일의 이름과 어설션의 줄 번호가 표시됩니다. 대화 상자에서 다시 시도를 선택하면 [AfxDebugBreak](https://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30)가 호출되어 실행이 디버거에서 중단됩니다. 이 지점에서 호출 스택을 검사하고 다른 디버거 기능을 사용하여 어설션이 실패한 이유를 확인할 수 있습니다. [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)을 활성화했는데 디버거가 아직 실행되지 않은 경우 대화 상자에서 디버거를 시작할 수 있습니다.  

 다음 예제는 `ASSERT`를 사용하여 함수의 반환 값을 확인하는 방법을 보여줍니다.  

```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 ASSERT를 [IsKindOf](https://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6) 함수와 함께 사용하여 함수 인수에 대한 유형 검사를 제공할 수 있습니다.  

```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 `ASSERT` 매크로는 릴리스 버전에서 코드를 생성하지 않습니다. 릴리스 버전에서 식을 평가해야 하는 경우 ASSERT 대신 [VERIFY](https://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) 매크로를 사용합니다.  

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID 및 CObject::AssertValid  
 [CObject::AssertValid](https://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157) 메서드는 개체의 내부 상태에 대한 런타임 검사를 제공합니다. `CObject`에서 클래스를 파생시킬 때 `AssertValid`를 재정의할 필요는 없지만 이렇게 하면 클래스를 더욱 안정적으로 만들 수 있습니다. `AssertValid`는 모든 개체의 멤버 변수에 대해 어설션을 수행하여 유효한 값이 포함되어 있는지 확인해야 합니다. 예를 들어, 포인터 멤버 변수가 NULL이 아닌 것을 확인해야 합니다.  

 다음 예제에서는 `AssertValid` 함수를 선언하는 방법을 보여줍니다.  

```  
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

 `AssertValid`를 재정의하는 경우 자체 검사를 수행하기 전에 `AssertValid`의 기본 클래스 버전을 호출합니다. 그런 다음, ASSERT 매크로를 사용하여 파생 클래스에 고유한 멤버를 확인합니다(아래 참조).  

```  
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

 멤버 변수가 개체를 저장하는 경우 `ASSERT_VALID` 매크로를 사용하여 내부 유효성을 테스트할 수 있습니다(클래스가 `AssertValid`를 재정의하는 경우).  

 예를 들어, 멤버 변수 중 하나에 [CObList](https://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca)를 저장하는 `CMyData` 클래스가 있습니다. `CObList` 변수, `m_DataList`는 `CPerson` 개체 컬렉션을 저장합니다. `CMyData`의 약식 선언은 다음과 같습니다.  

```  
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

 `CMyData`의 `AssertValid` 재정의는 다음과 같습니다.  

```  
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

 `CMyData`는 `AssertValid` 메커니즘을 사용하여 해당 데이터 멤버에 저장된 개체의 유효성을 테스트합니다. `CMyData`의 `AssertValid` 재정의는 자체 m_pDataList 멤버 변수에 대해 `ASSERT_VALID` 매크로를 호출합니다.  

 `CObList` 클래스도 `AssertValid`를 재정의하기 때문에 유효성 테스트는 이 수준에서 중지되지 않습니다. 이 재정의는 목록의 내부 상태에 대해 추가 유효성 테스트를 수행합니다. 따라서 `CMyData` 개체에 대한 유효성 테스트는 저장된 `CObList` 목록 개체의 내부 상태에 대한 추가 유효성 테스트로 이어집니다.  

 몇 가지 추가 작업으로, 목록에 저장된 `CPerson` 개체에 대한 유효성 테스트를 추가할 수도 있습니다. `CObList`에서 `CPersonList` 클래스를 파생시키고 `AssertValid`를 재정의할 수 있습니다. 재정의에서는 `CObject::AssertValid`를 호출한 다음, 목록에 저장된 각 `CPerson` 개체에서 `AssertValid`를 호출하여 목록에서 반복합니다. 이 문서의 시작 부분에 표시된 `CPerson` 클래스는 이미 `AssertValid`를 재정의합니다.  

 이 메커니즘은 디버깅을 위해 빌드할 때 강력합니다. 이후 릴리스를 위해 빌드할 때는 메커니즘이 자동으로 꺼집니다.  

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> AssertValid 제한 사항  
 트리거된 어설션은 개체가 명확히 잘못되었고 실행이 중지됨을 나타냅니다. 하지만 어설션이 부족하면 문제가 발견되지 않았다는 것 뿐이며 개체가 양호하다는 보장은 아닙니다.  

 [항목 내용](#BKMK_In_this_topic)  

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> 어설션 사용  

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> 논리 오류 포착  
 프로그램의 논리에 따라 true여야 하는 조건에 대한 어설션을 설정할 수 있습니다. 논리 오류가 발생하지 않으면 어설션이 적용되지 않습니다.  

 예를 들어, 컨테이너에서 가스 분자를 시뮬레이션하고 `numMols` 변수는 총 분자 수를 나타낸다고 가정합니다. 이 숫자는 0보다 작을 수 없으므로 MFC 어설션 문을 다음과 같이 포함할 수 있습니다.  

```  
ASSERT(numMols >= 0);  

```  

 또는 CRT 어설션을 다음과 같이 포함할 수 있습니다.  

```  
_ASSERT(numMols >= 0);  
```  

 프로그램이 제대로 작동하면 이 명령문은 아무 작업도 수행하지 않습니다. 논리 오류로 인해 `numMols`가 0보다 작으면 어설션이 프로그램 실행을 중지하고 [어설션 실패 대화 상자](../debugger/assertion-failed-dialog-box.md)를 표시합니다.  

 [항목 내용](#BKMK_In_this_topic)  

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> 결과 확인  
 어설션은 빠른 육안 검사로 결과가 명확하지 않은 작업을 테스트하는 데 유용합니다.  

 예를 들어, 다음 코드는 `mols`가 가리키는 링크된 목록의 콘텐츠를 기반으로 `iMols` 변수를 업데이트합니다.  

```  
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

 `iMols`로 계산된 분자 수는 총 분자 수인 `numMols`보다 항상 작거나 같아야 합니다. 루프를 육안으로 검사하면 반드시 참이라는 확신이 없기 때문에 루프 뒤에 어설션 문을 사용하여 이 조건을 테스트합니다.  

 [항목 내용](#BKMK_In_this_topic)  

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> 처리되지 않은 오류 찾기  
 어설션을 사용하여 오류를 처리해야 하는 코드의 지점에서 오류 조건을 테스트할 수 있습니다. 다음 예제에서 그래픽 루틴은 오류 코드를 반환하거나 성공에 대해 0을 반환합니다.  

```  
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 오류 처리 코드가 제대로 작동하면 어설션에 도달하기 전에 오류가 처리되고 `myErr`가 0으로 초기화되어야 합니다. `myErr`에 다른 값이 있으면 어설션이 실패하고 프로그램이 중지되고 [어설션 실패 대화 상자](../debugger/assertion-failed-dialog-box.md)가 나타납니다.  

 어설션 문이 오류 처리 코드를 대체하지는 않습니다. 다음 예제는 최종 릴리스 코드에서 문제를 일으킬 수 있는 어설션 문을 보여줍니다.  

```  
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 이 코드는 어설션 문을 사용하여 오류 조건을 처리합니다. 따라서 `myGraphRoutine`에서 반환된 오류 코드가 있으면 최종 릴리스 코드에서 처리되지 않습니다.  

 [항목 내용](#BKMK_In_this_topic)  

## <a name="see-also"></a>관련 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [네이티브 코드 디버깅](../debugger/debugging-native-code.md)   
 [관리 코드에 어설션 사용](../debugger/assertions-in-managed-code.md)
