---
title: 할당 후크 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f684c6c66448fdab2ee7607a81ff7ed769a5e607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745815"
---
# <a name="allocation-hook-functions"></a>할당 후크 함수
[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)를 사용하여 설치된 할당 후크 함수는 메모리를 할당, 다시 할당 또는 해제할 때마다 호출됩니다. 이 유형의 후크는 다양한 용도로 사용할 수 있습니다. 이를 사용하여 응용 프로그램에서 할당 패턴을 검사하거나 나중에 분석할 수 있도록 로그 할당 정보를 처리하는 등의 메모리 부족 상황을 처리하는 방법을 테스트합니다.

> [!NOTE]
> [할당 후크 및 C 런타임 메모리 할당](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)을 참조하여 할당 후크 함수에서 C 런타임 라이브러리 함수를 사용하는 방법에 대한 제한 사항에 대해 잘 알아두세요.

 할당 후크 함수에는 다음 예제와 같은 프로토타입이 있어야 합니다.

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)에 전달한 포인터는 CRTDBG.H에 정의된 대로 **_CRT_ALLOC_HOOK** 형식입니다.

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 런타임 라이브러리가 후크를 호출할 때 *Nalloctype* 인수는 수행할 할당 작업( **_HOOK_ALLOC**, **_HOOK_REALLOC** 또는 **_HOOK_FREE**)을 나타냅니다. 해제 또는 재할당에서 `pvData`에는 해제할 블록의 사용자 문서에 대한 포인터가 있습니다. 그러나 할당의 경우에는 할당이 발생하지 않았기 때문에 이 포인터는 null입니다. 나머지 인수에는 해당 할당의 크기, 해당 블록 형식, 관련된 순차적인 요청 번호 및 파일 이름에 대한 포인터가 포함됩니다. 사용 가능한 경우 인수에는 할당이 수행된 줄 번호도 포함됩니다. 후크 함수는 지정된 모든 분석과 작업을 수행한 다음, 할당 작업을 계속할 수 있음을 나타내는 **TRUE** 또는 작업을 중지해야 함을 나타내는 **FALSE**를 반환해야 합니다. 이 간단한 형식의 후크는 이제까지 할당된 메모리 양을 확인하고, 그 양이 한계를 약간이라도 초과하는 경우에는 **FALSE**를 반환할 수 있습니다. 그러면 사용할 수 있는 메모리가 부족한 경우에만 주로 발생하는 할당 오류가 애플리케이션에 발생합니다. 좀 더 복잡한 후크는 할당 패턴을 추적하거나 메모리 사용을 분석하거나 특정 상황이 발생하는 때를 보고할 수 있습니다.

## <a name="see-also"></a>참조

- [할당 후크 및 C 런타임 메모리 할당](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [디버그 후크 함수 작성](../debugger/debug-hook-function-writing.md)
