---
title: CRT 라이브러리를 사용 하 여 메모리 누수 찾기 | Microsoft Docs
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
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 831cae8d83bc26e05b80d6948a3168a6e6a387c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682431"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>CRT 라이브러리를 사용하여 메모리 누수 찾기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이전에 할당한 메모리를 올바르게 할당 해제하지 못한 상태로 정의되는 메모리 누수는 C/C++ 애플리케이션에서 가장 미묘하고 찾아 내기 어려운 버그입니다. 소량의 메모리 누수는 처음에는 알아차리지 못하는 경우가 많지만 시간이 지나면서 누적된 메모리 누수량이 많아지면 성능 저하에서부터 메모리 고갈로 인한 애플리케이션 충돌에 이르기까지 다양한 증상이 발생할 수 있습니다. 더 심한 경우 누수 애플리케이션이 사용 가능한 메모리를 모두 소진하여 다른 애플리케이션에서도 충돌이 발생하면 문제의 원인이 되는 애플리케이션을 파악하기가 어려워질 수 있습니다. 메모리 누수는 겉으로는 심각해 보이지 않더라도 반드시 해결해야 하는 다른 문제의 전조 증상인 경우도 있습니다.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버거와 CRT(C 런타임) 라이브러리에서는 메모리 누수를 탐지하고 식별할 수 있는 효과적인 수단을 제공합니다.  
  
## <a name="enabling-memory-leak-detection"></a>메모리 누수 탐지 기능 사용  
 메모리 누수를 탐지하는 데 사용하는 기본 도구는 디버거와 CRT(C 런타임 라이브러리) 디버그 힙 함수입니다.  
  
 디버그 힙 함수를 사용하려면 다음 문이 프로그램에 포함되어 있어야 합니다.  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 CRT 함수가 제대로 작동하려면 `#include` 문이 여기에 표시된 순서를 따라야 합니다.  
  
 crtdbg.h를 포함하면 `malloc` 및 [free](https://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) 함수가 해당 디버그 버전인 [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) 및 `free`에 매핑되어 메모리 할당 및 할당 해제를 추적할 수 있습니다. 이 매핑은 `_DEBUG`가 있는 디버그 빌드에서만 발생합니다. 릴리스 빌드에서는 일반적인 `malloc` 함수와 `free` 함수가 사용됩니다.  
  
 `#define` 문은 CRT 힙 함수의 기본 버전을 해당 디버그 버전에 매핑합니다. `#define` 문을 생략하면 메모리 누수 덤프가 덜 자세하게 표시됩니다.  
  
 이러한 문을 사용하여 디버그 힙 함수를 사용하도록 설정한 후에는 애플리케이션 종료 지점 앞에 `_CrtDumpMemoryLeaks` 호출을 추가하여 애플리케이션이 종료될 때 메모리 누수 보고서를 표시할 수 있습니다.  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 애플리케이션의 종료 지점이 여러 개인 경우 각 종료 지점마다 [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) 호출을 수동으로 추가할 필요는 없습니다. 애플리케이션의 시작 부분에 있는 `_CrtSetDbgFlag` 호출로 인해 각 종료 지점마다 `_CrtDumpMemoryLeaks` 가 자동으로 호출되기 때문입니다. 다음과 같이 두 개의 비트 필드를 설정해야 합니다.  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 기본적으로 `_CrtDumpMemoryLeaks` 는 **출력** 창의 **디버그** 창에 메모리 누수 보고서를 출력합니다. `_CrtSetReportMode` 를 사용하여 이 보고서를 다른 위치로 리디렉션할 수도 있습니다.  
  
 라이브러리를 사용할 경우에는 라이브러리에 의해 출력이 다른 위치로 다시 설정될 수도 있습니다. 이 경우 다음과 같이 출력 위치를 **출력** 창으로 다시 설정할 수 있습니다.  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>메모리 누수 보고서 해석  
 애플리케이션에 `_CRTDBG_MAP_ALLOC`이 정의되지 않은 경우 [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) 는 다음과 같은 메모리 누수 보고서를 표시합니다.  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 애플리케이션에 `_CRTDBG_MAP_ALLOC`이 정의된 경우에는 메모리 누수 보고서가 다음과 같이 표시됩니다.  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 두 번째 보고서에는 누수된 메모리가 처음 할당된 파일 이름 및 줄 번호가 표시된다는 차이점이 있습니다.  
  
 `_CRTDBG_MAP_ALLOC` 의 정의 여부에 관계없이 메모리 누수 보고서에 항상 표시되는 정보는 다음과 같습니다.  
  
- 메모리 할당 번호(이 예제의 경우 `18` )  
  
- [블록 형식](https://msdn.microsoft.com/e2f42faf-0687-49e7-aa1f-916038354f97)(이 예제의 경우 `normal` )  
  
- 16진수 메모리 위치(이 예제의 경우 `0x00780E80` )  
  
- 블록 크기(이 예제의 경우 `64 bytes` )  
  
- 블록 내 데이터의 처음 16바이트(16진수 형식)  
  
  메모리 누수 보고서에서는 메모리 블록을 표준 블록(normal block), 클라이언트 블록(client block) 또는 CRT 블록(CRT block)으로 식별합니다. *표준 블록* 은 프로그램이 할당한 보통 메모리입니다. *클라이언트 블록* 은 MFC 프로그램이 소멸자를 필요로 하는 개체에 대해 사용하는 특별한 메모리 블록 형식입니다. MFC `new` 연산자는 표준 블록 또는 클라이언트 블록 중 생성되는 개체에 적합한 블록을 만듭니다. *CRT 블록* 은 CRT 라이브러리가 자체 용도에 맞게 할당한 메모리 블록입니다. 이러한 블록의 할당 해제는 CRT 라이브러리에서는 처리됩니다. 따라서 CRT 라이브러리 손상 같은 중대한 문제가 발생하지 않는 한 메모리 누수 보고서에 이 블록이 표시되는 경우는 거의 없습니다.  
  
  그 외에도 메모리 누수 보고서에 표시되지 않는 두 가지 메모리 블록 형식이 있습니다. *빈 블록* 은 해제된 메모리로, 정의에 따라 누수되지 않은 메모리를 나타냅니다. *무시 블록* 은 메모리 누수 보고서에서 제외하도록 사용자가 명시적으로 지정한 메모리입니다.  
  
  이러한 기술은 표준 CRT `malloc` 함수를 사용하여 할당된 메모리에 대해 작동합니다. 그러나 프로그램에서 c + + 연산자를 사용 하 여 메모리를 할당 하는 경우 `new` `operator new` `_malloc_dbg` 메모리 누수 보고서에서 전역 호출의 구현이 파일 및 줄 번호를 볼 수 있습니다. 이 동작은 그다지 유용 하지 않기 때문에 다음과 같은 매크로를 사용 하 여 할당 한 줄을 보고 하도록 변경할 수 있습니다. 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
이제 코드에서 `DBG_NEW` 매크로를 사용하여 `new` 연산자를 바꿀 수 있습니다. 디버그 빌드에서는 `operator new` 블록 형식, 파일 및 줄 번호에 대 한 추가 매개 변수를 사용 하는 global의 오버 로드를 사용 합니다. `new` `_malloc_dbg` 추가 정보를 기록 하는 호출의이 오버 로드입니다. 를 사용 하는 경우 `DBG_NEW` 메모리 누수 보고서에는 누수 된 개체가 할당 된 파일 이름 및 줄 번호가 표시 됩니다. 정품 빌드에서는 기본값을 사용 `new` 합니다. (라는 전처리기 매크로 또는 다른 언어 키워드를 만들지 않는 것이 좋습니다 `new` .) 다음은이 방법의 예입니다.  
  
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
  
Visual Studio의 디버거에서이 코드를 실행 하는 경우에 대 한 호출은 `_CrtDumpMemoryLeaks` **출력** 창에 다음과 비슷한 보고서를 생성 합니다.  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
이는 debug_new의 20 번째 줄에 유출 된 할당이 있음을 나타냅니다.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>메모리 할당 번호에 중단점 설정  
 메모리 할당 번호는 누수된 메모리 블록이 할당된 시기를 알려 줍니다. 예를 들어 메모리 할당 번호가 18인 블록은 애플리케이션 실행 도중 18번째로 할당된 메모리 블록입니다. CRT 보고서에서는 실행 중의 모든 메모리 블록 할당 횟수를 계산합니다. 여기에는 CRT 라이브러리와 MFC 등의 다른 라이브러리에 의한 할당이 포함됩니다. 따라서 메모리 할당 번호가 18인 블록은 코드에서 18번째로 할당된 메모리 블록이 아닐 수도 있습니다. 대개는 이 경우에 해당됩니다.  
  
 할당 번호를 사용하여 메모리 할당에 중단점을 설정할 수 있습니다.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>조사식 창을 사용하여 메모리 할당 중단점을 설정하려면  
  
1. 애플리케이션의 시작 부분에 중단점을 설정하고 애플리케이션을 시작합니다.  
  
2. 애플리케이션이 중단점에서 중단되면 **조사식** 창을 실행합니다.  
  
3. **조사식** 창에서 **이름** 열에 `_crtBreakAlloc`를 입력합니다.  
  
    CRT 라이브러리의 다중 스레드 DLL 버전을 사용할 경우(/MD 옵션) `{,,ucrtbased.dll}_crtBreakAlloc`과 같이 컨텍스트 연산자를 포함해야 합니다.  
  
4. **RETURN**키를 누릅니다.  
  
    디버거에서 호출이 실행되고 결과가 **값** 열에 표시됩니다. 메모리를 할당할 때 중단점을 설정하지 않은 경우에는 이 값이 –1입니다.  
  
5. **값** 열에서 표시된 값을 중단할 메모리 할당의 할당 번호로 대체합니다.  
  
   메모리 할당 번호에 중단점을 설정한 후 디버깅을 계속할 수 있습니다. 이전과 같은 조건에서 프로그램을 실행하려면 메모리 할당 순서가 변경되지 않도록 주의하세요. 지정된 메모리 할당에서 프로그램이 중단되면 **호출 스택** 창과 다른 디버거 정보를 사용하여 메모리가 할당된 조건을 확인할 수 있습니다. 그런 다음 실행을 계속하여 개체에 발생한 상황을 살펴보고 메모리가 올바르게 할당 해제되지 않은 원인을 확인할 수 있습니다.  
  
   개체에 데이터 중단점을 설정하는 것도 유용합니다. 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md)을 참조 하세요.  
  
   코드에서 메모리 할당 중단점을 설정할 수도 있습니다. 이때 다음과 같은 두 가지 방법을 사용할 수 있습니다.  
  
```  
_crtBreakAlloc = 18;  
```  
  
 또는:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>메모리 상태 비교  
 주요 지점에서 애플리케이션의 메모리 상태 스냅샷을 보고 메모리 누수를 찾을 수도 있습니다. 특정 지점의 메모리 상태 스냅샷을 만들려면 **_CrtMemState** 구조체를 만들어 `_CrtMemCheckpoint` 함수에 전달합니다. 이 함수는 다음과 같이 구조체를 현재 메모리 상태의 스냅샷으로 채웁니다.  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` 는 다음과 같이 구조체를 현재 메모리 상태의 스냅샷으로 채웁니다.  
  
 **_CrtMemState** 구조체의 내용을 출력하려면 다음과 같이 `_ CrtMemDumpStatistics` 함수에 구조체를 전달합니다.  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` 는 다음과 같이 메모리 상태 덤프를 출력합니다.  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 코드의 한 섹션에서 메모리 누수가 발생했는지 확인하려면 해당 섹션 앞뒤에서 메모리 상태 스냅샷을 만든 다음 `_ CrtMemDifference` 를 사용하여 두 상태를 비교합니다.  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` 는 메모리 상태 `s1` 과 `s2` 를 비교하고,`s3`과 `s1` 의 차이를 나타내는 결과를 `s2`에 반환합니다.  
  
 메모리 누수를 찾는 한 가지 기술은 애플리케이션의 처음과 마지막에 `_CrtMemCheckpoint` 호출을 배치한 다음 `_CrtMemDifference` 를 사용하여 결과를 비교하는 작업으로 시작됩니다. `_CrtMemDifference` 가 메모리 누수를 표시하는 경우, `_CrtMemCheckpoint` 호출을 추가하여 누수 원인을 확인할 때까지 이진 검색을 통해 프로그램을 나눌 수 있습니다.  
  
## <a name="false-positives"></a>가양성(false positive)  
 간혹 `_CrtDumpMemoryLeaks` 가 메모리 누수를 잘못 표시하는 경우도 있습니다. 이러한 오류는 내부 할당을 `_CRT_BLOCK`이나 `_CLIENT_BLOCK`대신 _NORMAL_BLOCK으로 표시하는 라이브러리를 사용할 때 발생할 수 있습니다. 이 경우 `_CrtDumpMemoryLeaks` 가 사용자 할당과 내부 라이브러리 할당을 구별할 수 없게 됩니다. `_CrtDumpMemoryLeaks`를 호출한 이후에 라이브러리 할당을 위한 전역 소멸자가 실행되면 모든 내부 라이브러리 할당이 메모리 누수로 보고됩니다. Visual Studio .NET 이전 버전의 표준 템플릿 라이브러리에서는 `_CrtDumpMemoryLeaks` 가 이러한 가양성(false positive)을 보고했지만, 최신 릴리스에서는 이 문제가 해결되었습니다.  
  
## <a name="see-also"></a>관련 항목  
 [CRT 디버그 힙 정보](../debugger/crt-debug-heap-details.md)   
 [디버거 보안](../debugger/debugger-security.md)   
 [네이티브 코드 디버그](../debugger/debugging-native-code.md)
