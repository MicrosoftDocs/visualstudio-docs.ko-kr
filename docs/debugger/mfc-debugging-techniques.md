---
title: MFC 디버깅 기술 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd4a481a8d4f283204b99cfef4a07106d3e479cb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731285"
---
# <a name="mfc-debugging-techniques"></a>MFC 디버깅 기술
다음은 MFC 프로그램을 디버깅하는 데 유용한 디버깅 기술입니다.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[TRACE 매크로](#BKMK_The_TRACE_macro)

[MFC의 메모리 누수 탐지](#BKMK_Memory_leak_detection_in_MFC)

- [메모리 할당 추적](#BKMK_Tracking_memory_allocations)

- [메모리 진단 사용](#BKMK_Enabling_memory_diagnostics)

- [메모리 스냅샷 만들기](#BKMK_Taking_memory_snapshots)

- [메모리 통계 보기](#BKMK_Viewing_memory_statistics)

- [개체 덤프 수행](#BKMK_Taking_object_dumps)

  - [메모리 덤프 해석](#BKMK_Interpreting_memory_dumps)

  - [개체 덤프 사용자 지정](#BKMK_Customizing_object_dumps)

  - [MFC 디버그 빌드 크기 줄이기](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [선택한 모듈의 디버그 정보를 사용하여 MFC 응용 프로그램 빌드](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
MFC를 사용하면 소스 코드의 하드 코드 중단점에 특별한 [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) 함수를 사용할 수 있습니다.

```cpp
AfxDebugBreak( );
```

Intel 플랫폼에서 `AfxDebugBreak` 는 커널 코드가 아닌 소스 코드에서 중단되는 다음과 같은 코드를 생성합니다.

```cpp
_asm int 3
```

다른 플랫폼에서는 `AfxDebugBreak` 가 `DebugBreak`를 단순히 호출할 뿐입니다.

릴리스 빌드를 만들 때 `AfxDebugBreak` 문을 제거하거나 `#ifdef _DEBUG` 를 사용하여 이 문을 포함시키십시오.

[항목 내용](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> TRACE 매크로
디버거 [출력 창](../ide/reference/output-window.md)에 프로그램 메시지를 표시하기 위해 [ATLTRACE](https://msdn.microsoft.com/Library/c796baa5-e2b9-4814-a27d-d800590b102e) 매크로나 MFC [TRACE](https://msdn.microsoft.com/Library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) 매크로를 사용할 수 있습니다. [어설션](../debugger/c-cpp-assertions.md)과 마찬가지로 추적 매크로는 프로그램의 디버그 버전에서만 활성화되며 릴리스 버전에서 컴파일하면 사라집니다.

다음 예제에서는 **TRACE** 매크로 사용법을 몇 가지 보여 줍니다. `printf`와 같이 **TRACE** 매크로도 많은 인수를 처리할 수 있습니다.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

TRACE 매크로는 char\* 및 wchar_t\* 매개 변수를 적절히 처리합니다. 다음 예제에서는 TRACE 매크로와 다른 형식의 문자열 매개 변수를 함께 사용하는 방법을 보여 줍니다.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

**TRACE** 매크로에 대한 자세한 정보는 [Diagnostic Services](/cpp/mfc/reference/diagnostic-services)를 참조하십시오.

[항목 내용](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> MFC의 메모리 누수 탐지
MFC는 할당할 수는 있어도 할당을 취소할 수 없는 메모리를 탐지하는 클래스와 함수를 가지고 있습니다.

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> 메모리 할당 추적
MFC에서 [new](https://msdn.microsoft.com/Library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) 연산자 자리에 **DEBUG_NEW** 매크로를 사용하면 메모리 누수를 찾는 데 도움이 됩니다. 프로그램의 디버그 버전에서 `DEBUG_NEW` 는 할당된 각 개체의 파일 이름과 줄 번호를 추적합니다. 프로그램의 릴리스 버전을 컴파일할 경우 `DEBUG_NEW` 는 파일 이름과 줄 번호 정보 없이 간단한 **new** 연산자를 확인합니다. 따라서 프로그램의 릴리스 버전에서는 속도가 저하되지 않습니다.

`DEBUG_NEW` new **자리에**를 사용하기 위해 프로그램 전체를 다시 작성하는 대신, 다음과 같이 소스 파일에서 이 매크로를 정의할 수 있습니다.

```cpp
#define new DEBUG_NEW
```

[개체 덤프](#BKMK_Taking_object_dumps)를 수행하면 `DEBUG_NEW` 에서 할당된 개체가 할당된 파일과 줄 번호를 표시하여, 메모리 누수가 발생한 소스를 알 수 있습니다.

MFC 프레임워크의 디버그 버전은 자동으로 `DEBUG_NEW` 를 사용하지만 코드는 그렇지 않습니다. `DEBUG_NEW`를 효과적으로 사용하려면, 위와 같이 `DEBUG_NEW` 를 명시하거나 **#define new** 를 사용해야 합니다.

[항목 내용](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> 메모리 진단 사용
메모리 진단 기능을 사용하려면 진단 추적을 활성화해야 합니다.

**메모리 진단을 활성화하거나 비활성화하려면**

- 전역 함수 [AfxEnableMemoryTracking](https://msdn.microsoft.com/Library/0a40e0c4-855d-46e2-9577-a8f2346f47db) 을 호출하여 진단 메모리 할당자를 활성화하거나 비활성화합니다. 디버그 라이브러리에서는 메모리 진단이 기본적으로 활성화되어 있기 때문에 일반적으로 이 기능을 사용하여 일시적으로 비활성화하며 이는 프로그램 실행 속도를 높이고 진단 결과를 줄입니다.

  **afxMemDF로 특정 메모리 진단 기능을 선택하려면**

- 메모리 진단 기능을 보다 자세히 제어하려면 MFC 전역 함수 [afxMemDF](https://msdn.microsoft.com/Library/cf117501-5446-4fce-81b3-f7194bc95086)의 값을 설정하여 각 메모리 진단 기능 사용 여부를 지정할 수 있습니다. 이 변수는 열거 형식 **afxMemDF**가 지정한 대로 다음과 같은 값을 가질 수 있습니다.

  |값|설명|
  |-----------|-----------------|
  |**allocMemDF**|진단 메모리 할당자를 사용합니다(기본값).|
  |**delayFreeMemDF**|`delete` 또는 `free` 를 호출할 경우 프로그램이 종료될 때까지 메모리 해제를 지연시킵니다. 이렇게 하면 프로그램이 가능한 최대 메모리를 할당하게 됩니다.|
  |**checkAlwaysMemDF**|메모리를 할당하거나 해제할 때마다 [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) 를 호출합니다.|

  논리적 OR 연산을 수행하면 다음과 같이 이 값들을 조합하여 사용할 수 있습니다.

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [항목 내용](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> 메모리 스냅샷 만들기

1. [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) 개체를 만들고 [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) 멤버 함수를 호출합니다. 그러면 첫 번째 메모리 스냅샷이 만들어집니다.

2. 프로그램이 메모리 할당 작업과 할당 취소 작업을 수행하면 다른 `CMemoryState` 개체를 만들고 해당 개체에 대해 `Checkpoint` 를 호출합니다. 그러면 메모리 사용에 대한 두 번째 스냅샷이 만들어집니다.

3. 세 번째 `CMemoryState` 개체를 만들고 이전의 두 [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) 개체를 인수로 제공하여 `CMemoryState` 멤버 함수를 호출합니다. 두 메모리 상태가 서로 다르면 `Difference` 함수가 0이 아닌 값을 반환합니다. 이것은 할당이 취소되지 않은 메모리 블록이 있음을 나타냅니다.

    다음 예제는 해당 코드의 내용을 보여 줍니다.

    ```cpp
    // Declare the variables needed
    #ifdef _DEBUG
        CMemoryState oldMemState, newMemState, diffMemState;
        oldMemState.Checkpoint();
    #endif

        // Do your memory allocations and deallocations.
        CString s("This is a frame variable");
        // The next object is a heap object.
        CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );

    #ifdef _DEBUG
        newMemState.Checkpoint();
        if( diffMemState.Difference( oldMemState, newMemState ) )
        {
            TRACE( "Memory leaked!\n" );
        }
    #endif
    ```

    메모리를 검사하는 문은 프로그램의 디버그 버전에서만 컴파일되도록 **#ifdef _DEBUG / #endif** 블록으로 묶어야 합니다.

    이제 메모리 누수가 확인되었으므로 다른 멤버 함수인 [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) 를 사용하여 해당 위치를 찾을 수 있습니다.

    [항목 내용](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> 메모리 통계 보기
[CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) 함수는 두 메모리 상태 개체를 살펴 상태의 시작과 끝 사이의 힙에서 할당 취소되지 않은 모든 개체를 검색합니다. 메모리 스냅샷을 만들고 `CMemoryState::Difference`를 사용하여 스냅샷을 비교한 후 [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) 를 호출하여 할당이 취소되지 않은 개체에 대한 정보를 가져올 수 있습니다.

다음 예제를 참조하세요.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

다음 예제는 덤프 샘플을 보여 줍니다.

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

free 블록은 `afxMemDF` 가 `delayFreeMemDF`로 설정되면 할당 취소가 연기되는 블록입니다.

두 번째 줄에 표시된 보통 개체 블록은 계속 힙에 할당되어 있습니다.

비개체 블록에는 `new`로 할당된 배열 및 구조체가 포함됩니다. 이 경우 할당이 취소되지 않는 비개체 블록 네 개가 힙에 할당되어 있습니다.

`Largest number used` 를 사용하면 프로그램은 언제라도 최대 메모리를 사용할 수 있습니다.

`Total allocations` 를 사용하면 프로그램이 사용하는 총 메모리를 알 수 있습니다.

[항목 내용](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> 개체 덤프 수행
MFC 프로그램에서는 [CMemoryState::DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince)를 사용하여 힙에서 할당 취소되지 않은 모든 개체의 설명을 덤프할 수 있습니다. `DumpAllObjectsSince` 는 마지막 [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint)를 단순히 호출할 뿐입니다. `Checkpoint` 를 호출할 수 없는 경우 `DumpAllObjectsSince` 가 현재 메모리에 있는 모든 개체와 비개체를 덤프합니다.

> [!NOTE]
> MFC 개체를 덤프하려면 먼저 [진단 추적을 활성화](#BKMK_Enabling_memory_diagnostics)해야 합니다.

> [!NOTE]
> 프로그램을 종료할 때 MFC가 누수된 개체를 모두 자동으로 덤프하므로 해당 지점에서 개체를 덤프할 코드를 만들 필요가 없습니다.

다음 코드는 두 메모리 상태를 비교하여 메모리 누수를 테스트하고 누수가 탐지되면 모든 개체를 덤프합니다.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

덤프 내용은 다음과 같습니다.

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

대개의 경우 줄 맨 앞의 중괄호에 있는 번호는 개체가 할당된 순서를 나타냅니다. 가장 최근에 할당된 개체는 가장 큰 번호를 가지며 덤프 맨 위에 나타납니다.

개체 덤프에서 최대한의 정보를 얻기 위해 모든 `Dump` 파생 개체의 `CObject`멤버 함수를 재정의하여 개체 덤프를 사용자 지정할 수 있습니다.

전역 변수 `_afxBreakAlloc` 을 중괄호 안에 있는 번호에 설정하여 특정 메모리 할당에 중단점을 설정할 수 있습니다. 프로그램을 다시 실행하면 할당할 때 디버거가 실행을 중단합니다. 그러면 호출 스택에서 프로그램이 해당 지점에 도달한 방법을 알 수 있습니다.

C 런타임 라이브러리에는 C 런타임 할당에 사용할 수 있는 유사한 함수인 [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc)이 있습니다.

[항목 내용](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> 메모리 덤프 해석
이 개체 덤프를 자세히 살펴보면 다음과 같습니다.

```cmd
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

이 덤프를 생성한 프로그램에는 스택과 힙에 각각 하나씩 두 개의 명시적 할당이 있습니다.

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

`CPerson` 생성자는 `char`의 포인터가 되는 세 인수를 가지며, 이들 인수는 `CString` 멤버 변수를 초기화하는 데 사용됩니다. 메모리 덤프에서 `CPerson` 개체와 세 개의 비개체 블록(3, 4, 5)을 볼 수 있습니다. 이들은 `CString` 멤버 변수 문자를 가지고 있으며 `CPerson` 개체 소멸자를 호출할 때 삭제되지 않습니다.

블록 번호 2는 `CPerson` 개체 자신입니다. `$51A4` 는 블록 주소로서 다음에 개체 내용이 표시되며, 개체 내용은 `CPerson`DumpAllObjectsSince`Dump` 가 호출할 때 [::](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince)를 사용하여 출력됩니다.

블록 번호 1은 `CString` 프레임 변수와 연결되어 있다고 볼 수 있습니다. 해당 시퀀스 번호와 크기가 프레임 `CString` 변수에 있는 문자의 번호와 일치하기 때문입니다. 프레임이 범위를 벗어나면 프레임에 할당된 변수는 자동으로 할당 취소됩니다.

**프레임 변수**

프레임 변수가 범위를 벗어나면 할당이 자동으로 취소되기 때문에 프레임 변수와 연결된 힙 개체에 대해서는 신경쓸 필요가 없습니다. 메모리 진단 덤프의 혼란을 막으려면 `Checkpoint` 호출을 프레임 변수의 범위 밖에 배치해야 합니다. 예를 들어, 다음과 같이 이전 할당 코드를 범위 괄호로 묶어 주십시오.

```cpp
oldMemState.Checkpoint();
{
    // Do your memory allocations and deallocations ...
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
}
newMemState.Checkpoint();
```

범위 괄호를 추가하면 이 예제의 메모리 덤프가 다음과 같이 표시됩니다.

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215
```

**비개체 할당**

일부 할당은 `CPerson`과 같은 개체이며 일부는 비개체 할당입니다. "비개체 할당"이란 `CObject` 에서 파생되지 않은 개체의 할당이나 `char`, `int` 또는 `long`과 같은 기본 C 형식의 할당입니다. <strong>CObject</strong>파생 클래스가 내부 버퍼와 같은 추가 공간을 할당하는 경우 해당 개체는 개체 할당과 비개체 할당을 모두 표시합니다.

**메모리 누수 방지**

위 코드에서, `CString` 프레임 변수와 연결된 메모리 블록은 자동으로 할당 취소되어 메모리 누수로 표시되지 않습니다. 범위 지정 규칙과 관련된 자동 할당 취소는 프레임 변수와 연결된 대부분의 메모리 누수에 적용됩니다.

그러나 힙에 할당된 개체는 명시적으로 삭제하여 메모리 누수를 방지해야 합니다. 이전 예제의 마지막 메모리 누수를 해결하려면 힙에 할당된 `CPerson` 개체를 다음과 같이 삭제하십시오.

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[항목 내용](#BKMK_In_this_topic)

#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> 개체 덤프 사용자 지정
[CObject](/cpp/mfc/reference/cobject-class)에서 클래스를 파생시키는 경우 `Dump` DumpAllObjectsSince [를 사용하여](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) 출력 창 [으로 개체를 덤프할 때](../ide/reference/output-window.md)멤버 함수를 재정의하여 추가 정보를 제공할 수 있습니다.

`Dump` 함수는 덤프 컨텍스트([CDumpContext](/cpp/mfc/reference/cdumpcontext-class))에 개체 멤버 변수의 텍스트 표현을 작성합니다. 덤프 컨텍스트는 I/O 스트림과 유사합니다. 추가 연산자( **<<** )를 사용하여 `CDumpContext`를 단순히 호출할 뿐입니다.

`Dump` 함수를 재정의하려면 먼저 `Dump` 의 기본 클래스 버전을 호출하여 기본 클래스 개체의 내용을 덤프해야 합니다. 그런 다음 파생 클래스의 각 멤버 변수에 대한 텍스트 설명과 값을 출력하십시오.

`Dump` 함수 선언은 다음과 같습니다.

```cpp
class CPerson : public CObject
{
public:
#ifdef _DEBUG
    virtual void Dump( CDumpContext& dc ) const;
#endif

    CString m_firstName;
    CString m_lastName;
    // And so on...
};
```

개체 덤프는 프로그램을 디버깅할 때만 효과가 있으므로 `Dump` 함수 선언은 **#ifdef _DEBUG / #endif** 블록과 함께 대괄호로 묶습니다.

다음 예제에서는 `Dump` 함수가 먼저 기본 클래스의 `Dump` 함수를 호출합니다. 그런 다음 진단 스트림에 멤버 값과 함께 각 멤버 변수에 대한 간단한 설명을 씁니다.

```cpp
#ifdef _DEBUG
void CPerson::Dump( CDumpContext& dc ) const
{
    // Call the base class function first.
    CObject::Dump( dc );

    // Now do the stuff for our specific class.
    dc << "last name: " << m_lastName << "\n"
        << "first name: " << m_firstName << "\n";
}
#endif
```

`CDumpContext` 인수를 추가하여 어디로 덤프 출력할지 지정해야 합니다. MFC의 디버그 버전에서는 미리 정의된 `CDumpContext` 개체인 `afxDump` 를 사용하여 출력을 디버거로 보냅니다.

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[항목 내용](#BKMK_In_this_topic)

## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> MFC 디버그 빌드 크기 줄이기
대형 MFC 애플리케이션의 디버그 정보는 디스크 공간을 많이 차지할 수 있습니다. 다음 절차 중 하나를 사용하여 크기를 줄일 수 있습니다.

1. **/Z7** 대신 [/Z7, /Zi, /ZI(디버그 정보 형식)](/cpp/build/reference/z7-zi-zi-debug-information-format) 옵션을 사용하여 MFC 라이브러리를 다시 빌드합니다. 이 옵션은 전체 라이브러리의 디버그 정보가 있는 프로그램 데이터베이스(PDB) 파일 하나를 빌드하여 중복을 없애고 공간을 절약합니다.

2. 디버그 정보 없이 MFC 라이브러리를 다시 빌드합니다([/Z7, /Zi, /ZI(디버그 정보 형식)](/cpp/build/reference/z7-zi-zi-debug-information-format) 옵션 없음). 이 경우 디버그 정보가 부족하여 MFC 라이브러리 코드의 디버거 기능을 대부분 사용할 수 없지만 MFC 라이브러리는 이미 모두 디버깅된 상태이므로 문제가 되지 않습니다.

3. 아래에 설명된 대로 선택한 모듈의 디버그 정보로 사용자 고유의 애플리케이션을 빌드합니다.

    [항목 내용](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> 선택한 모듈의 디버그 정보를 사용하여 MFC 응용 프로그램 빌드
MFC 디버그 라이브러리를 사용하여 선택한 모듈을 빌드하면 이 모듈에서 단계별 실행 및 다른 디버그 기능을 사용할 수 있습니다. 이 프로시저는 프로젝트의 디버그 및 릴리스 구성을 둘 다 사용하기 때문에 다음 단계와 같이 변경해야 하며 전체 릴리스 빌드가 필요한 경우에는 “모두 다시 빌드”해야 합니다.

1. 솔루션 탐색기에서 프로젝트를 선택합니다.

2. **보기** 메뉴에서 **속성 페이지**를 선택합니다.

3. 먼저 새 프로젝트 구성을 만듭니다.

   1. **\<프로젝트> 속성 페이지** 대화 상자에서 **구성 관리자** 단추를 클릭합니다.

   2. [구성 관리자 대화 상자](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100))의 표에서 원하는 프로젝트를 찾습니다. **구성** 열에서 **\<새로 만들기...>** 를 선택합니다.

   3. [새 프로젝트 구성 대화 상자](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100))의 **새 프로젝트 구성** 상자에 새 구성의 이름을 ?부분 디버그?등과 같이 입력합니다.

   4. **다음에서 설정 복사** 목록에서 **릴리스**를 선택합니다.

   5. **확인**을 클릭하여 **새 프로젝트 구성** 대화 상자를 닫습니다.

   6. **구성 관리자** 대화 상자를 닫습니다.

4. 이제 전체 프로젝트의 옵션을 설정합니다.

   1. **속성 페이지** 대화 상자에서 **구성 속성** 폴더의 **일반** 범주를 선택합니다.

   2. 필요한 경우 프로젝트 설정 표에서 **프로젝트 기본값** 을 확장합니다.

   3. **프로젝트 기본값**에서 **MFC 사용**을 찾습니다. 현재 설정이 표의 오른쪽 열에 표시됩니다. 현재 설정을 클릭하여 **정적 라이브러리에서 MFC 사용**으로 변경합니다.

   4. **속성 페이지** 대화 상자의 왼쪽 창에서 **C/C++** 폴더를 열고 **전처리기**를 선택합니다. 속성 표에서 **전처리기 정의** 를 찾아 "NDEBUG"를 "_DEBUG"로 대체합니다.

   5. **속성 페이지** 대화 상자의 왼쪽 창에서 **링커** 폴더를 열고 **입력** 범주를 선택합니다. 속성 표에서 **추가 종속성**을 찾습니다. **추가 종속성** 설정에 "NAFXCWD.LIB" 및 "LIBCMT"를 입력합니다.

   6. **확인** 을 클릭하여 새 빌드 옵션을 저장하고 **속성 페이지** 대화 상자를 닫습니다.

5. **빌드** 메뉴에서 **다시 빌드**를 선택합니다. 그러면 모듈에서 모든 디버그 정보가 제거되지만 MFC 라이브러리에 영향을 주지는 않습니다.

6. 이제 애플리케이션의 선택한 모듈에 디버그 정보를 다시 추가해야 합니다. 디버그 정보로 컴파일한 모듈에서만 중단점을 설정하고 다른 디버거 기능을 사용할 수 있다는 점을 기억하십시오. 디버그 정보를 추가할 각 프로젝트 파일에 대해 다음 작업을 수행하십시오.

   1. 솔루션 탐색기 창에서 해당 프로젝트 아래의 **소스 파일** 폴더를 엽니다.

   2. 디버그 정보를 설정할 파일을 선택합니다.

   3. **보기** 메뉴에서 **속성 페이지**를 선택합니다.

   4. **속성 페이지** 대화 상자의 **구성 속성** 폴더에서 **C/C++** 폴더를 연 다음 **일반** 범주를 선택합니다.

   5. 속성 그리드에서 **디버그 정보 형식**을 찾습니다.

   6. **디버깅 정보 형식** 설정을 클릭하고 디버그 정보에 대해 원하는 옵션(대개 **/ZI**)을 선택합니다.

   7. 애플리케이션 마법사로 만든 애플리케이션을 사용하거나 헤더를 미리 컴파일한 경우, 다른 모듈을 컴파일하기 전에 미리 컴파일한 헤더를 사용하지 않도록 하거나 다시 컴파일해야 합니다. 그렇지 않으면 경고 C4650과 오류 메시지 C2855를 받게 됩니다. **\<프로젝트> 속성** 대화 상자(**구성 속성** 폴더, **C/C++** 하위 폴더, **미리 컴파일된 헤더** 범주)에서 **미리 컴파일된 헤더 만들기/사용** 설정을 변경하여 미리 컴파일된 헤더를 해제할 수 있습니다.

7. **빌드** 메뉴에서 **빌드** 를 선택하여 날짜가 지난 프로젝트 파일을 다시 빌드합니다.

   이 항목에서 설명한 기술 대신 외부 메이크파일을 사용하여 파일마다 개별적인 옵션을 정의할 수도 있습니다. 이 경우에 MFC 디버그 라이브러리와 링크하려면 각 모듈에 [_DEBUG](/cpp/c-runtime-library/debug) 플래그를 정의해야 합니다. MFC 릴리스 라이브러리를 사용하려면 NDEBUG를 정의해야 합니다. 외부 메이크파일 작성에 대한 자세한 내용은 [NMAKE 참조](/cpp/build/running-nmake)를 참조하십시오.

   [항목 내용](#BKMK_In_this_topic)

## <a name="see-also"></a>참조
[네이티브 코드 디버그](../debugger/debugging-native-code.md)
