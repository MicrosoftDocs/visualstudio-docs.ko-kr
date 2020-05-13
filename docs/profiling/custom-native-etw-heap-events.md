---
title: 사용자 지정 네이티브 ETW 힙 이벤트 | Microsoft 문서
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb6f906cbfb715d67f6e10ddcecf094bc25821f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552965"
---
# <a name="custom-native-etw-heap-events"></a>사용자 지정 네이티브 ETW 힙 이벤트

Visual Studio에는 네이티브 메모리 프로파일러를 비롯한 다양한 [프로파일링 및 진단 도구](../profiling/profiling-feature-tour.md)가 포함되어 있습니다.  이 프로파일러는 힙 공급자에서 [ETW 이벤트](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-)를 후크하고 메모리 할당 및 사용 방법을 분석합니다.  기본적으로 이 도구는 표준 Windows 힙에서 만든 할당만 분석할 수 있으므로 이 네이티브 힙 외부의 할당은 표시되지 않습니다.

사용자 지정 힙을 사용하여 표준 힙에서 할당 오버헤드를 방지할 수도 있습니다.  예를 들어 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)를 사용하여 앱 또는 게임을 시작할 때 대용량 메모리를 할당한 다음 해당 목록에서 자체 블록을 관리할 수 있습니다.  이 시나리오에서 메모리 프로파일러 도구는 초기 할당만 표시하고, 메모리 청크 내부에서 수행되는 사용자 지정 관리는 표시하지 않습니다.  사용자 지정 네이티브 힙 ETW 공급자를 사용하여 표준 힙 외부에서 수행하는 모든 할당을 도구에 알릴 수 있습니다.

예를 들어 `MemoryPool`이 사용자 지정 힙인 다음과 같은 프로젝트에는 Windows 힙에 단일 할당만 표시됩니다.

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

사용자 지정 힙을 추적하지 않는 [메모리 사용량](../profiling/memory-usage.md) 도구에서 만든 스냅샷에는 단일 8192바이트 할당만 표시되고, 풀에서 만든 사용자 지정 할당은 표시되지 않습니다.

![Windows 힙 할당](media/heap-example-windows-heap.png)

다음 단계를 수행하여 동일한 도구로 사용자 지정 힙의 메모리 사용량을 추적할 수 있습니다.

## <a name="how-to-use"></a>사용 방법

이 라이브러리는 C 및 C++에서 쉽게 사용할 수 있습니다.

1. 사용자 지정 힙 ETW 공급자에 대한 헤더를 포함합니다.

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. 포인터를 새로 할당된 힙 메모리로 반환하는 `__declspec(allocator)` 데코레이터를 사용자 지정 힙 관리자의 함수에 추가합니다.  이 데코레이터를 통해 도구에서 반환 중인 메모리의 형식을 올바르게 식별할 수 있습니다.  다음은 그 예입니다.

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > 이 데코레이터는 이 함수가 할당자에 대한 호출임을 컴파일러에 알려줍니다.  함수를 호출할 때마다 호출 사이트의 주소, 호출 명령의 크기, 새 개체의 형식 ID를 새 `S_HEAPALLOCSITE` 기호로 출력합니다.  콜백이 할당되면 Windows에서 이 정보를 사용하여 ETW 이벤트를 발생합니다.  메모리 프로파일러 도구는 `S_HEAPALLOCSITE` 기호와 일치하는 반환 주소를 조사하는 콜백을 안내하고 기호로 된 형식 ID 정보를 사용하여 할당의 런타임 형식을 표시합니다.
   >
   > 즉, `(B*)(A*)MyMalloc(sizeof(B))`와 같은 호출은 도구에 `B` 형식(`void` 또는 `A` 아님)으로 표시됩니다.

1. C++의 경우 힙에 대한 이름을 제공하여 `VSHeapTracker::CHeapTracker` 개체를 만듭니다. 이 이름이 프로파일링 도구에 표시됩니다.

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   C를 사용 중인 경우 `OpenHeapTracker` 함수를 대신 사용합니다.  이 함수는 다른 추적 함수를 호출할 때 사용할 핸들을 반환합니다.

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. 사용자 지정 함수를 사용하여 메모리를 할당할 경우 `AllocateEvent`(C++) 또는 `VSHeapTrackerAllocateEvent`(C) 메서드를 호출하고 메모리와 해당 크기에 포인터를 전달하여 할당을 추적합니다.

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   또는

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > 사용자 지정 할당자 함수에 앞에서 설명한 `__declspec(allocator)` 데코레이터로 태그 지정합니다.

1. 사용자 지정 함수를 사용하여 메모리를 할당 취소할 경우 `DeallocateEvent`(C++) 또는 `VSHeapTracerDeallocateEvent`(C) 함수를 호출하고 메모리에 포인터를 전달하여 할당 취소를 추적합니다.

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   또는:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. 사용자 지정 함수를 사용하여 메모리를 재할당할 경우 `ReallocateEvent`(C++) 또는 `VSHeapReallocateEvent`(C) 메서드를 호출하고 새 메모리, 할당 크기 및 이전 메모리에 포인터를 전달합니다.

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   또는:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. 마지막으로 C++에서 사용자 지정 힙 추적기를 닫고 정리하려면 `CHeapTracker` 소멸자를 수동으로 또는 표준 범위 지정 규칙 또는 C의 `CloseHeapTracker` 함수를 통해 사용합니다.

   ```cpp
   delete pHeapTracker;
   ```

   또는:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>메모리 사용량 추적
이제 이러한 호출을 적절히 배치하여 Visual Studio의 표준 **메모리 사용량** 도구를 통해 사용자 지정 힙 사용량을 추적할 수 있습니다.  이 도구를 사용하는 방법에 대한 자세한 내용은 [메모리 사용량](../profiling/memory-usage.md) 설명서를 참조하세요. 스냅샷을 사용하여 힙 프로파일링을 설정해야 합니다. 그러지 않으면 표시된 사용자 지정 힙 사용량이 나타나지 않습니다.

![힙 프로파일링 사용](media/heap-enable-heap.png)

사용자 지정 힙 추적을 보려면 **스냅샷** 창의 오른쪽 위에 있는 **힙** 드롭다운을 사용하여 뷰를 *NT 힙*에서 앞에서 이름을 지정한 사용자 힙으로 변경합니다.

![힙 선택](media/heap-example-custom-heap.png)

위의 코드 예제를 참조하여 `MemoryPool`에서 `VSHeapTracker::CHeapTracker` 개체를 만들고 자체 `allocate` 메서드로 `AllocateEvent` 메서드를 호출하면 사용자 지정 할당 결과를 확인할 수 있습니다. 모두 `Foo` 형식이고 총 24바이트인 세 개의 인스턴스가 표시됩니다.

기본 *NT 힙* 힙의 모양은 이전과 동일하지만 `CHeapTracker` 개체가 추가되었습니다.

![추적기가 있는 NT 힙](media/heap-example-windows-heap.png)

표준 Windows 힙과 마찬가지로 이 도구를 사용하여 스냅샷을 비교하고 사용자 지정 힙의 누수 및 손상을 확인할 수도 있습니다. 자세한 내용은 기본 [메모리 사용량](../profiling/memory-usage.md) 설명서를 참조하세요.

> [!TIP]
> Visual Studio의 **성능 프로파일링** 도구 집합에도 **메모리 사용량** 도구가 포함되어 있습니다. 이 도구 집합은 **디버그** > **성능 프로파일러** 메뉴 옵션 또는 **Alt**+**F2** 키보드 조합을 통해 활성화됩니다.  이 기능은 힙 추적을 포함하지 않으므로 여기서 설명하는 사용자 지정 힙을 표시하지 않습니다.  **진단 도구** 창(**디버그** > **Windows** > **진단 도구 표시** 메뉴 또는 **Ctrl**+**Alt**+**F2** 키보드 조합을 사용하여 설정 가능)에만 이 기능이 포함되어 있습니다.

## <a name="see-also"></a>참고 항목
[프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)
[메모리 사용량](../profiling/memory-usage.md)
