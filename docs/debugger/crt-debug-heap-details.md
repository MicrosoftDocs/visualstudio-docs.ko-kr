---
title: CRT 디버그 힙 세부 정보 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d09319e412d693fc9df95d9ae9b9773f0869afc3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745621"
---
# <a name="crt-debug-heap-details"></a>CRT 디버그 힙 정보
이 항목에서는 CRT 디버그 힙에 대해 자세히 설명합니다.

## <a name="BKMK_Contents"></a> 목차
[디버그 힙을 사용하여 버퍼 오버런 찾기](#BKMK_Find_buffer_overruns_with_debug_heap)

[디버그 힙의 블록 형식](#BKMK_Types_of_blocks_on_the_debug_heap)

[힙 무결성 및 메모리 누수 확인](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[디버그 힙 구성](#BKMK_Configure_the_debug_heap)

[C++ 디버그 힙의 new, delete 및 _CLIENT_BLOCK](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[힙 상태 보고 함수](#BKMK_Heap_State_Reporting_Functions)

[힙 할당 요청 추적](#BKMK_Track_Heap_Allocation_Requests)

## <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> 디버그 힙을 사용하여 버퍼 오버런 찾기
프로그래머가 직면 하는 가장 일반적인 문제 중 두 가지는 할당 된 버퍼 및 메모리 누수의 끝을 덮어쓰는 것입니다 (더 이상 필요 하지 않은 할당을 해제 하지 못함). 디버그 힙을 사용하여 이러한 메모리 할당 문제를 효과적으로 해결할 수 있습니다.

힙 함수의 디버그 버전은 릴리스 빌드에서 사용하는 표준 또는 기본 버전을 호출합니다. 메모리 블록을 요청하면 디버그 힙 관리자는 요청한 것 보다 약간 더 큰 메모리 블록을 기본 힙에서 할당하고 블록의 해당 부분에 대한 포인터를 반환합니다. 예를 들어 애플리케이션에 `malloc( 10 )` 호출이 있을 경우, 릴리스 빌드에서 [malloc](/cpp/c-runtime-library/reference/malloc) 는 10 바이트의 할당을 요청 하는 기본 힙 할당 루틴을 호출 합니다. 그러나 `malloc`은 디버그 빌드에서는 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)를 호출하여 10 바이트 할당 및 약 36 바이트의 추가 메모리를 요청 하는 기본 힙 할당 루틴을 호출 합니다. 디버그 힙의 모든 결과 메모리 블록은 할당된 순서에 따라 하나의 연결 리스트로 연결됩니다.

디버그 힙 루틴이 할당한 추가 메모리는 할당된 영역의 덮어 쓰기를 찾기 위해 부기 정보, 디버그 메모리 블록을 연결하는 포인터, 데이터 양쪽에 있는 작은 버퍼 등에 사용됩니다.

현재 디버그 힙의 부기 정보를 저장하는 데 사용된 블록 헤더 구조체는 DBGINT.H 헤더 파일에서 다음과 같이 선언됩니다.

```cpp
typedef struct _CrtMemBlockHeader
{
// Pointer to the block allocated just before this one:
    struct _CrtMemBlockHeader *pBlockHeaderNext;
// Pointer to the block allocated just after this one:
    struct _CrtMemBlockHeader *pBlockHeaderPrev;
    char *szFileName;    // File name
    int nLine;           // Line number
    size_t nDataSize;    // Size of user block
    int nBlockUse;       // Type of block
    long lRequest;       // Allocation number
// Buffer just before (lower than) the user's memory:
    unsigned char gap[nNoMansLandSize];
} _CrtMemBlockHeader;

/* In an actual memory block in the debug heap,
 * this structure is followed by:
 *   unsigned char data[nDataSize];
 *   unsigned char anotherGap[nNoMansLandSize];
 */
```

블록의 사용자 데이터 양 영역의 `NoMansLand` 버퍼 크기는 현재 4바이트이며, 사용자의 메모리 블록 한계를 덮어쓰지 않았다는 것을 확인하기 위해 디버그 힙 루틴이 사용하는 알려진 바이트 값으로 채워져 있습니다. 디버그 힙은 또한 새로운 메모리 블록을 알려진 값으로 채웁니다. 아래에서 설명한 대로 힙의 연결 리스트에 빈 블록을 유지하도록 선택하면 이러한 빈 블록도 알려진 값으로 채워집니다. 현재 실제 사용된 바이트 값은 다음과 같습니다.

NoMansLand (0xFD) 응용 프로그램에서 사용 하는 메모리의 양쪽에 있는 "NoMansLand" 버퍼는 현재 0xFD로 채워져 있습니다.

해제 된 블록 (0xDD) `_CRTDBG_DELAY_FREE_MEM_DF` 플래그를 설정 하는 경우 디버그 힙의 연결 된 목록에서 사용 되지 않은 상태로 유지 되는 현재 0xDD로 채워져 있습니다.

새 개체 (0xCD) 새 개체는 할당 될 때 0xCD로 채워집니다.

![최상위](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)로 돌아가기

## <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> 디버그 힙의 블록 형식
디버그 힙의 모든 메모리 블록은 다섯 가지 할당 형식 중 하나에 지정됩니다. 누수 탐지와 상태 보고 등의 목적에 따라 이러한 형식을 다르게 추적하고 보고합니다. [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)와 같은 디버그 힙 할당 함수 중 하나를 직접 호출하여 블록을 할당하면 블록의 형식을 지정할 수 있습니다. 디버그 힙에 있는 메모리 블록 형식( **_CrtMemBlockHeader** 구조체의 **nBlockUse** 멤버에 설정) 다섯 가지는 다음과 같습니다.

**_NORMAL_BLOCK** [malloc](/cpp/c-runtime-library/reference/malloc) 또는 [calloc](/cpp/c-runtime-library/reference/calloc)을 호출하면 일반 블록이 생성됩니다. 표준 블록만 사용하고 클라이언트 블록은 사용하지 않으려면 모든 힙 할당 호출을 디버그 빌드의 해당 디버그 부분에 매핑시키는 [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)을 정의해야 합니다. 그러면 각 할당 호출에 대한 파일 이름과 줄 번호 정보가 해당 블록 헤더에 저장됩니다.

`_CRT_BLOCK` 여러 런타임 라이브러리 함수에 의해 내부적으로 할당된 메모리 블록은 CRT 블록으로 표시되어 별도로 처리할 수 있습니다. 결과적으로 누수 탐지나 다른 작업들이 런타임 라이브러리 함수의 영향을 받지 않습니다. 할당은 CRT 형식의 어떠한 블록도 할당하거나 할당 취소하거나 해제할 수 없습니다.

`_CLIENT_BLOCK` 애플리케이션은 지정한 할당 그룹을 이 형식의 메모리 블록으로 할당함으로써 디버깅을 위해 이 할당 그룹을 특별히 추적하여 디버그 힙 함수를 명시적으로 호출할 수 있습니다. 예를 들어, MFC는 모든 **CObjects**를 클라이언트 블록으로 할당하며, 다른 애플리케이션은 클라이언트 블록에 여러 메모리 개체를 가질 수 있습니다. 또한 보다 정교하게 추적하도록 클라이언트 블록의 하위 형식을 지정할 수 있습니다. 클라이언트 블록의 하위 형식을 지정하려면 16비트로 남긴 숫자를 변환하고 `OR`으로 `_CLIENT_BLOCK`연산을 실행하십시오. 예를 들면,

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

클라이언트 블록에 저장된 개체를 덤프하기 위해 [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)를 사용하여 클라이언트 제공 후크 함수를 설치할 수 있으며, 설치 후 디버그 함수가 클라이언트 블록을 덤프할 때마다 호출됩니다. 또한 [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects)를 사용하여 디버그 힙에 있는 모든 클라이언트 블록에 대해 애플리케이션이 제공하는 지정한 함수를 호출할 수 있습니다.

**_FREE_BLOCK** 일반적으로 해제 된 블록은 목록에서 제거 됩니다. 빈 블록을 Free로 표시하고 알려진 바이트 값(현재 0xDD)으로 채워 연결 리스트에 보관하여, 빈 메모리가 아직 작성되지 않았는지 확인하거나 낮은 메모리 조건을 시뮬레이션할 수 있습니다.

**_IGNORE_BLOCK** 일정 기간 동안 디버그 힙 작업을 해제할 수 있습니다. 그 동안 메모리 블록은 리스트에 보관되지만 무시 블록으로 표시됩니다.

지정한 블록의 형식 및 하위 형식을 확인하려면 함수 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)과 매크로 **_BLOCK_TYPE** 및 **_BLOCK_SUBTYPE**을 사용합니다. 매크로는 crtdbg.h에서 다음과 같이 정의됩니다.

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![최상위](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)로 돌아가기

## <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> 힙 무결성 및 메모리 누수 확인
디버그 힙의 기능 중 상당수는 코드 안에서 액세스해야 합니다. 다음 단원에서는 이러한 기능과 사용 방법에 대해 설명합니다.

`_CrtCheckMemory` 예를 들어 [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)를 호출하여 어떤 지점에서든 해당 힙의 무결성을 확인할 수 있습니다. 이 함수는 힙의 모든 메모리 블록을 검사하고, 메모리 블록 헤더 정보가 올바른지 그리고 버퍼가 수정되었는지 확인합니다.

`_CrtSetDbgFlag` [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) 함수를 사용해 읽고 설정할 수 있는 내부 플래그 [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag)를 사용하여 디버그 힙이 할당을 추적하는 방법을 제어할 수 있습니다. 이 플래그를 변경하면 프로그램이 종료된 다음 탐지한 누수를 모두 보고할 때, 디버그 힙이 메모리 누수를 확인하도록 지시할 수 있습니다. 마찬가지로 빈 메모리 블록이 연결 리스트에서 제거되지 않도록 지정하여 메모리 부족 상태를 시뮬레이션할 수 있습니다. 힙을 확인할 때 이 빈 블록 전체를 조사하여 방해받지 않았는지 확인합니다.

**_crtDbgFlag** 플래그에는 다음과 같은 비트 필드가 포함되어 있습니다.

|비트 필드|기본<br /><br /> 값|설명|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|켜기|디버그 할당을 사용합니다. 이 비트를 해제하면 할당은 함께 연결되어 있지만 블록 형식은 **_IGNORE_BLOCK**입니다.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|끄기|부족한 메모리 조건을 시뮬레이션하는 것과 관련해서 메모리가 실제로 해제되는 것을 방지합니다. 이 비트를 설정하면, 해제된 블록이 디버그 힙의 연결 리스트에 보관되지만 **_FREE_BLOCK**으로 표시되고 특별한 바이트 값으로 채워 집니다.|
|**_CRTDBG_CHECK_ALWAYS_DF**|끄기|모든 할당 및 할당 취소에서 **_CrtCheckMemory**가 호출되게 합니다. 실행 속도는 지연되지만 오류를 신속하게 찾아 냅니다.|
|**_CRTDBG_CHECK_CRT_DF**|끄기|**_CRT_BLOCK** 형식으로 표시된 블록이 누수 탐지 및 상태 차이 작업에 포함되게 합니다. 비트를 해제하면 위와 같은 작업을 하는 동안 런타임 라이브러리가 내부적으로 사용하는 메모리를 무시합니다.|
|**_CRTDBG_LEAK_CHECK_DF**|끄기|**_CrtDumpMemoryLeaks**를 호출하여 프로그램을 종료할 때 누수 검사를 수행합니다. 애플리케이션이 할당한 모든 메모리를 해제하는 데 실패하면 오류 보고서가 생성됩니다.|

![최상위](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)로 돌아가기

## <a name="BKMK_Configure_the_debug_heap"></a> 디버그 힙 구성
`malloc`, `free`, `calloc`, `realloc`, `new` 및 `delete` 등의 힙 함수에 대한 모든 호출은 디버그 힙에서 작동하는 해당 함수의 디버그 버전으로 확인됩니다. 메모리 블록을 해제할 경우, 디버그 힙은 자동으로 할당 영역 양쪽에 있는 버퍼의 무결성을 확인하며 덮어쓰기가 발생하면 오류 보고서를 만듭니다.

**디버그 힙을 사용하려면**

- C 런타임 라이브러리의 디버그 버전을 사용하여 애플리케이션의 디버그 빌드를 연결합니다.

  **_crtDbgFlag 비트 필드를 하나 이상 변경하고 플래그에 새로운 상태를 만들려면**

1. 현재 `_CrtSetDbgFlag` 상태를 가져오기 위해 `newFlag` 매개 변수를 `_CRTDBG_REPORT_FLAG`로 설정한 상태로 `_crtDbgFlag`를 호출하고 반환된 값을 임시 변수에 저장합니다.

2. 해당 비트 마스크 (응용 프로그램 코드에서 매니페스트 상수로 &#124; 표시)로 임시 변수를 `OR` 연산 (비트 기호) 하 여 모든 비트를 설정 합니다.

3. 적절 한 비트 마스크의 `NOT` (비트 ~ 기호)를 사용 하 여 변수를 `AND` 연산 (비트 & 기호) 하 여 다른 비트를 해제 합니다.

4. `_CrtSetDbgFlag`에 대해 새로운 상태를 만들기 위해 임시 변수로 저장한 값에 설정한 `newFlag` 매개 변수를 사용하여 `_crtDbgFlag`를 호출합니다.

   예를 들어, 다음 코드의 줄에서는 자동 누수 탐지를 설정하고 `_CRT_BLOCK` 형식의 블록 확인을 해제합니다.

```cpp
// Get current flag
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn on leak-checking bit.
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;

// Turn off CRT block checking bit.
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;

// Set flag to the new value.
_CrtSetDbgFlag( tmpFlag );
```

![최상위](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)로 돌아가기

## <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> C++ 디버그 힙의 new, delete 및 _CLIENT_BLOCK
C 런타임 라이브러리의 디버그 버전은 C++ `new` 및 `delete` 연산자의 디버그 버전을 포함합니다. `_CLIENT_BLOCK` 할당 형식을 사용하는 경우 다음 예제와 같이 `new` 연산자의 디버그 버전을 직접 호출하거나 디버그 모드에서 `new` 연산자를 대체하는 매크로를 만들어야 합니다.

```cpp
/* MyDbgNew.h
 Defines global operator new to allocate from
 client blocks
*/

#ifdef _DEBUG
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)
#else
   #define DEBUG_CLIENTBLOCK
#endif // _DEBUG

/* MyApp.cpp
        Use a default workspace for a Console Application to
 *      build a Debug version of this code
*/

#include "crtdbg.h"
#include "mydbgnew.h"

#ifdef _DEBUG
#define new DEBUG_CLIENTBLOCK
#endif

int main( )   {
    char *p1;
    p1 =  new char[40];
    _CrtMemDumpAllObjectsSince( NULL );
}
```

`delete` 연산자의 디버그 버전은 모든 블록 형식에 대해 작동하며, 릴리스 버전을 컴파일할 때 프로그램을 변경할 필요가 없습니다.

![최상위](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)로 돌아가기

## <a name="BKMK_Heap_State_Reporting_Functions"></a> 힙 상태 보고 함수
 **_CrtMemState**

 지정한 순간에 힙 상태의 요약 스냅샷을 캡처하려면 CRTDBG.H에 정의된 _CrtMemState 구조체를 사용하십시오.

```cpp
typedef struct _CrtMemState
{
    // Pointer to the most recently allocated block:
    struct _CrtMemBlockHeader * pBlockHeader;
    // A counter for each of the 5 types of block:
    size_t lCounts[_MAX_BLOCKS];
    // Total bytes allocated in each block type:
    size_t lSizes[_MAX_BLOCKS];
    // The most bytes allocated at a time up to now:
    size_t lHighWaterCount;
    // The total bytes allocated at present:
    size_t lTotalCount;
} _CrtMemState;
```

이 구조체는 가장 최근에 할당된 첫 번째 블록에 대한 포인터를 디버그 힙의 연결 리스트에 저장합니다. 그런 다음 두 배열에서 목록에 있는 _NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK 등의 각 메모리 블록 형식의 개수와 각 블록 형식에 할당된 바이트 수를 기록합니다. 마지막으로 해당 포인트까지 전체적으로 힙에서 할당된 가장 큰 바이트 수와 현재 할당된 바이트 수를 기록합니다.

**기타 CRT 보고 함수**

다음 함수는 힙의 상태와 내용을 보고하며 그 정보를 사용하여 메모리 누수 등의 문제를 탐지합니다.

|기능|설명|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|힙의 스냅샷을 애플리케이션에서 제공하는 **_CrtMemState** 구조체에 저장합니다.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|두 메모리 상태 구조체를 비교하고 세 번째 상태 구조체에 그 차이를 저장하며, 두 상태가 다른 경우 TRUE를 반환합니다.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|지정한 **_CrtMemState** 구조체를 덤프합니다. 구조체에는 지정한 순간의 디버그 힙 상태 스냅샷이나 두 스냅샷의 차이점이 포함될 수 있습니다.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|지정한 스냅샷이 힙의 스냅샷이거나 실행을 시작할 때 만들어진 스냅샷이기 때문에 할당된 모든 개체 정보를 덤프합니다. **_CrtSetDumpClient**를 사용하여 **_CLIENT_BLOCK** 블록을 설치한 경우, 이 블록을 덤프할 때마다 애플리케이션의 후크 함수를 호출합니다.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|프로그램 실행을 시작한 이후로 메모리 누수가 발생했는지 확인하고, 메모리 누수를 탐지한 경우 할당된 개체를 모두 덤프합니다. **_CrtSetDumpClient**를 사용하여 **_CLIENT_BLOCK** 블록을 설치한 경우, **_CrtDumpMemoryLeaks**가 이 블록을 덤프할 때마다 애플리케이션의 후크 함수를 호출합니다.|

![최상위](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)로 돌아가기

## <a name="BKMK_Track_Heap_Allocation_Requests"></a> 힙 할당 요청 추적
어설션 매크로나 보고서 매크로를 실행하는 소스 파일 이름과 줄 번호를 식별하는 것은 문제의 원인을 찾는 데 유용하지만 힙 할당 함수에서는 다릅니다. 애플리케이션 논리 트리에서는 적절한 지점에 매크로를 삽입할 수 있지만, 할당은 서로 다른 시간에 여러 위치에서 호출되는 특별한 루틴에 숨겨지는 경우도 있습니다. 대개의 경우 코드의 어느 줄이 잘못된 할당을 만들었는지가 아니라 잘못된 할당이 어느 것이고 원인이 무엇인지가 문제입니다.

**고유한 할당 요청 번호 및 _crtBreakAlloc**

디버그 힙에 있는 각 블록에 연결된 고유한 할당 요청 번호를 이용하면 잘못된 특정 힙 할당 호출을 가장 쉽게 식별할 수 있습니다. 덤프 함수 중 하나가 블록에 대한 정보를 보고하면 이 할당 요청 번호는 중괄호로 묶어 표시합니다(예: "{36}").

잘못 할당된 블록의 할당 요청 번호를 알면 이 번호를 [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc)에 전달하여 중단점을 만들 수 있습니다. 블록을 할당하기 직전에 실행이 중단되면 역추적하여 잘못된 호출에 관련된 루틴이 어느 것인지 확인할 수 있습니다. 원하는 할당 요청 번호에 **_crtBreakAlloc**을 설정하여 디버거에서 같은 작업을 수행하면 다시 컴파일하지 않아도 됩니다.

**할당 루틴의 디버그 버전 만들기**

다소 복잡한 방법이지만 [heap allocation functions](../debugger/debug-versions-of-heap-allocation-functions.md)의 **_dbg** 버전과 비교하여 할당 루틴의 디버그 버전을 만드는 방법도 있습니다. 그런 다음 내부 힙 할당 루틴에 소스 파일과 줄 번호 인수를 전달하면 잘못된 할당이 발생한 위치를 즉시 알 수 있습니다.

예를 들어, 애플리케이션에 다음과 같이 주로 사용되는 루틴이 있다고 가정합니다.

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

헤더 파일에서 다음과 같은 코드를 추가할 수 있습니다.

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

그런 다음 다음과 같이 레코드 작성 루틴에서 할당을 변경할 수 있습니다.

```cpp
int addNewRecord(struct RecStruct *prevRecord,
                int recType, int recAccess
#ifdef _DEBUG
               , const char *srcFile, int srcLine
#endif
    )
{
    /* ... code omitted through actual allocation ... */
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,
            srcFile, scrLine)) == NULL)
    /* ... rest of routine omitted too ... */
}
```

이제 `addNewRecord`를 호출한 소스 파일 이름과 줄 번호는 디버그 힙에 할당된 각 결과 블록에 저장되며 해당 블록을 검사할 때 보고됩니다.

![최상위](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)로 돌아가기

## <a name="see-also"></a>참조
[네이티브 코드 디버그](../debugger/debugging-native-code.md)
