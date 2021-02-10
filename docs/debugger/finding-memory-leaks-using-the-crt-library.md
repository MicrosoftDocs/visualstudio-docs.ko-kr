---
title: CRT 라이브러리로 메모리 누수 찾기 | Microsoft Docs
description: C/C++ 디버거 및 CRT(C 런타임 라이브러리)를 통해 메모리 누수를 찾는 방법을 알아봅니다. 포함되는 기술로는 메모리 누수 보고서와 메모리 스냅샷 비교가 있습니다.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98bfb3aca5be844018c4c7d9736ab2fa74ebb71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870677"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>CRT 라이브러리로 메모리 누수 찾기

메모리 누수는 C/C++ 앱에서 가장 복잡하고 감지하기 어려운 버그 중 하나입니다. 이전에 할당된 메모리를 올바르게 할당 해제하지 못하면 메모리 누수가 발생합니다. 소량의 메모리 누수는 처음에는 알아차리지 못하지만 시간이 지남에 따라 앱의 메모리가 부족해지면 성능 저하에서 충돌에 이르기까지 다양한 증상이 발생할 수 있습니다. 누수 앱이 사용 가능한 메모리를 모두 소진하여 다른 앱에서 충돌이 발생하면 문제의 책임이 있는 앱을 파악하기가 어려워질 수 있습니다. 무해한 메모리 누수조차도 해결해야 하는 다른 문제를 나타낼 수 있습니다.

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 디버거와 CRT(C 런타임 라이브러리)를 사용하면 메모리 누수를 감지하고 식별할 수 있습니다.

## <a name="enable-memory-leak-detection"></a>메모리 누수 감지 기능 사용

메모리 누수를 감지하기 위한 기본 도구는 C/C++ 디버거와 CRT(C 런타임 라이브러리) 디버그 힙 함수입니다.

모든 디버그 힙 함수를 사용하려면 다음 순서대로 C++ 프로그램에 다음 명령문을 포함시킵니다.

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

`#define` 문은 CRT 힙 함수의 기본 버전을 해당 디버그 버전에 매핑합니다. `#define` 문을 생략하면 메모리 누수 덤프가 [덜 자세하게](#interpret-the-memory-leak-report) 표시됩니다.

*crtdbg.h* 를 포함하면 `malloc` 및 `free` 함수가 해당 디버그 버전인 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) 및 [_free_dbg](/cpp/c-runtime-library/reference/free-dbg)에 매핑되어 메모리 할당 및 할당 해제를 추적할 수 있습니다. 이 매핑은 `_DEBUG`가 있는 디버그 빌드에서만 발생합니다. 릴리스 빌드에서는 일반적인 `malloc` 함수와 `free` 함수가 사용됩니다.

위의 명령문을 사용하여 디버그 힙 함수를 사용하도록 설정한 후에는 앱 종료 지점 앞에 [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)를 호출하여 앱이 종료될 때 메모리 누수 보고서를 표시합니다.

```cpp
_CrtDumpMemoryLeaks();
```

앱이 여러 번 종료되는 경우 모든 종료 지점에 `_CrtDumpMemoryLeaks`를 수동으로 배치할 필요가 없습니다. 각 종료 지점에서 `_CrtDumpMemoryLeaks`를 자동 호출하려면 다음과 같이 표시된 비트 필드를 사용하여 앱의 시작 부분에 `_CrtSetDbgFlag`를 호출합니다.

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

기본적으로 `_CrtDumpMemoryLeaks` 는 **출력** 창의 **디버그** 창에 메모리 누수 보고서를 출력합니다. 라이브러리를 사용할 경우에는 라이브러리에 의해 출력이 다른 위치로 다시 설정될 수도 있습니다.

다음과 같이 표시된 것처럼 `_CrtSetReportMode`를 사용하여 보고서를 다른 위치로 리디렉션하거나 **출력** 창으로 다시 리디렉션할 수 있습니다.

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>메모리 누수 보고서 해석

앱에서 `_CRTDBG_MAP_ALLOC`를 정의하지 않으면 [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)는 다음과 같은 메모리 누수 보고서를 표시합니다.

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

앱에서 `_CRTDBG_MAP_ALLOC`를 정의하면 메모리 누수 보고서는 다음과 같이 표시됩니다.

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

두 번째 보고서에는 누수된 메모리가 처음 할당된 파일 이름 및 줄 번호가 표시됩니다.

`_CRTDBG_MAP_ALLOC`를 정의하는지 여부에 관계없이 메모리 누수 보고서는 다음과 같이 표시됩니다.

- 메모리 할당 번호(이 예제의 경우 `18`)
- 블록 형식(이 예제의 경우 `normal`).
- 16진수 메모리 위치(이 예제의 경우 `0x00780E80`).
- 블록 크기(이 예제의 경우 `64 bytes`).
- 블록 내 데이터의 처음 16바이트(16진수 형식)

메모리 블록 형식은 *일반*, *클라이언트* 또는 *CRT* 입니다. *표준 블록* 은 프로그램이 할당한 보통 메모리입니다. *클라이언트 블록* 은 MFC 프로그램이 소멸자를 필요로 하는 개체에 대해 사용하는 특별한 메모리 블록 형식입니다. MFC `new` 연산자는 표준 블록 또는 클라이언트 블록 중 생성되는 개체에 적합한 블록을 만듭니다.

*CRT 블록* 은 CRT 라이브러리가 자체 용도에 맞게 할당한 메모리 블록입니다. CRT 라이브러리는 이러한 블록의 할당 취소를 처리하므로 CRT 라이브러리에 심각한 문제가 없는 한 메모리 누수 보고서에 CRT 블록이 나타나지 않습니다.

그 외에도 메모리 누수 보고서에 표시되지 않는 두 가지 메모리 블록 형식이 있습니다. *빈 블록* 은 릴리스된 메모리이므로 정의에 따라 유출되지 않습니다. *무시 블록* 은 메모리 누수 보고서에서 제외하도록 사용자가 명시적으로 지정한 메모리입니다.

위의 기술은 표준 CRT `malloc` 함수를 사용하여 할당된 메모리의 메모리 누수를 식별합니다. 프로그램에서는 C++ `new` 연산자를 사용하여 메모리를 할당하지만, 메모리 누수 보고서에서 `operator new`가 `_malloc_dbg`를 호출하는 파일 이름 및 줄 번호만 볼 수 있습니다. 보다 유용한 메모리 누수 보고서를 만들기 위해 다음과 같은 매크로를 작성하여 할당한 줄을 보고할 수 있습니다.

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

이제 코드에서 `DBG_NEW` 매크로를 사용하여 `new` 연산자를 바꿀 수 있습니다. 디버그 빌드에서 `DBG_NEW`는 블록 형식, 파일 및 줄 번호에 대한 추가 매개 변수를 사용하는 글로벌 `operator new`의 오버로드를 사용합니다. `new`의 오버로드는 `_malloc_dbg`를 호출하여 추가 정보를 기록합니다. 메모리 누수 보고서에는 유출된 개체가 할당된 파일 이름 및 줄 번호가 표시됩니다. 릴리스 빌드는 여전히 기본 `new`를 사용합니다. 이 기술의 예는 다음과 같습니다.

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

Visual Studio 디버거에서 이 코드를 실행하면 `_CrtDumpMemoryLeaks`에 대한 호출은 다음과 유사한 **출력** 창에 보고서를 생성합니다.

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

이 출력은 유출된 할당이 *debug_new.cpp* 의 20번째 줄에 있음을 보고합니다.

>[!NOTE]
>`new`라는 전처리기 매크로 또는 다른 언어 키워드를 만들지 않는 것이 좋습니다.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>메모리 할당 번호에 중단점 설정

메모리 할당 번호는 누수된 메모리 블록이 할당된 시기를 알려 줍니다. 예를 들어 메모리 할당 번호가 18인 블록은 앱 실행 도중 18번째로 할당된 메모리 블록입니다. CRT 보고서는 CRT 라이브러리 및 MFC와 같은 다른 라이브러리에 의한 할당을 포함하여 실행 중에 모든 메모리 블록 할당을 계산합니다. 따라서 메모리 할당 블록 번호 18은 코드에서 18번째로 할당된 메모리 블록이 아닐 수도 있습니다.

할당 번호를 사용하여 메모리 할당에 중단점을 설정할 수 있습니다.

**조사식 창을 사용하여 메모리 할당 중단점을 설정하려면**

1. 앱의 시작 부분 근처에 중단점을 설정하고 디버깅을 시작합니다.

1. 앱이 중단점에서 일시 중지되면 **디버그** > **Windows** > **조사식 1**(또는 **조사식 2**, **조사식 3**, **조사식 4**)을 선택하여 **조사식** 창을 엽니다.

1. **조사식** 창에서 **이름** 열에 `_crtBreakAlloc`를 입력합니다.

   CRT 라이브러리의 다중 스레드 DLL 버전을 사용하는 경우(/MD 옵션) 컨텍스트 연산자(`{,,ucrtbased.dll}_crtBreakAlloc`)를 추가합니다.
   
   디버그 기호가 로드되었는지 확인합니다. 그렇지 않으면 `_crtBreakAlloc`는 *미확인* 으로 보고됩니다.

1. **Enter** 키를 누릅니다.

   디버거에서 호출이 실행되고 결과가 **값** 열에 표시됩니다. 메모리를 할당할 때 중단점을 설정하지 않은 경우에는 이 값이 **-1** 입니다.

1. **값** 열에서 디버거를 중단할 메모리 할당의 할당 번호로 값을 바꿉니다.

메모리 할당 번호에 중단점을 설정한 후 디버깅을 계속합니다. 메모리 할당 번호가 변경되지 않도록 동일한 조건으로 실행해야 합니다. 지정된 메모리 할당에서 프로그램이 중단되면 **호출 스택** 창과 다른 디버거 창을 사용하여 메모리가 할당된 조건을 확인합니다. 그런 다음, 실행을 계속하여 개체에 발생한 상황을 살펴보고 메모리가 올바르게 할당 해제되지 않은 원인을 확인할 수 있습니다.

개체에 데이터 중단점을 설정하는 것도 유용합니다. 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md)을 참조하세요.

코드에서 메모리 할당 중단점을 설정할 수도 있습니다. 다음과 같이 설정할 수 있습니다.

```cpp
_crtBreakAlloc = 18;
```

 또는

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>메모리 상태 비교

주요 지점에서 애플리케이션의 메모리 상태 스냅샷을 보고 메모리 누수를 찾을 수도 있습니다. 애플리케이션의 지정된 지점에서 메모리 상태 스냅샷을 만들려면 `_CrtMemState` 구조체를 만들어 `_CrtMemCheckpoint` 함수에 전달합니다.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

`_CrtMemCheckpoint` 함수는 구조체를 현재 메모리 상태의 스냅샷으로 채웁니다.

`_CrtMemState` 구조체의 내용을 출력하려면 다음과 같이 `_ CrtMemDumpStatistics` 함수에 구조체를 전달합니다.

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics`는 다음과 같이 메모리 상태 덤프를 출력합니다.

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

코드의 한 섹션에서 메모리 누수가 발생했는지 확인하려면 해당 섹션 앞뒤에서 메모리 상태 스냅샷을 만든 다음 `_ CrtMemDifference` 를 사용하여 두 상태를 비교합니다.

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference`는 메모리 상태 `s1`과 `s2`를 비교하고 `s1`과 `s2` 사이의 차이를 나타내는 결과를 `s3`에 반환합니다.

메모리 누수를 찾는 한 가지 기술은 앱의 처음과 마지막에 `_CrtMemCheckpoint` 호출을 배치한 다음, `_CrtMemDifference`를 사용하여 결과를 비교하는 작업으로 시작됩니다. `_CrtMemDifference`가 메모리 누수를 표시하는 경우, `_CrtMemCheckpoint` 호출을 추가하여 누수 원인을 확인할 때까지 이진 검색을 통해 프로그램을 나눌 수 있습니다.

## <a name="false-positives"></a>가양성(false positive)

 라이브러리에서 내부 할당을 CRT 블록 또는 클라이언트 블록 대신 일반 블록으로 표시하는 경우 `_CrtDumpMemoryLeaks`는 잘못된 메모리 누수 표시를 제공할 수 있습니다. 이 경우 `_CrtDumpMemoryLeaks` 가 사용자 할당과 내부 라이브러리 할당을 구별할 수 없게 됩니다. `_CrtDumpMemoryLeaks`를 호출한 이후에 라이브러리 할당을 위한 전역 소멸자가 실행되면 모든 내부 라이브러리 할당이 메모리 누수로 보고됩니다. Visual Studio .NET 이전 버전의 표준 템플릿 라이브러리에서는 `_CrtDumpMemoryLeaks`가 이러한 가양성(false positive)을 보고할 수 있습니다.

## <a name="see-also"></a>참조

- [CRT 디버그 힙 정보](../debugger/crt-debug-heap-details.md)
- [디버거 보안](../debugger/debugger-security.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
