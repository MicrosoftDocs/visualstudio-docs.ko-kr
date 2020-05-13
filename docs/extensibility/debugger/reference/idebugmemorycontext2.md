---
title: 아이데버그메모리컨텍스트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727434"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
이 인터페이스는 디버깅 중인 프로그램을 실행하는 컴퓨터의 주소 공간에 있는 위치를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 이 인터페이스를 구현하여 메모리의 주소를 나타냅니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 또는 [GetMemoryContext에](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) 대한 호출은 이 인터페이스를 반환합니다. 또한 적절한 산술 연산이 적용된 후 [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) 및 [빼기](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) 호출이 이 인터페이스의 새 복사본을 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugMemoryContext2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|이 컨텍스트에 대해 사용자가 표시할 수 있는 이름을 가져옵니다.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|이 컨텍스트를 설명하는 정보를 가져옵니다.|
|[추가](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|현재 컨텍스트의 주소에 지정된 값을 추가하여 새 컨텍스트를 만듭니다.|
|[빼기](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|현재 컨텍스트의 주소에서 지정된 값을 빼서 새 컨텍스트를 만듭니다.|
|[비교](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|비교 플래그로 표시된 방식으로 두 컨텍스트를 비교합니다.|

## <a name="remarks"></a>설명
 Visual Studio의 **메모리** 창은 [GetMemoryContext를](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 호출하여 메모리 주소에 `IDebugMemoryContext2` 사용되는 평가된 식이 포함된 인터페이스를 가져옵니다. 그런 다음 이 컨텍스트를 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 및 [WriteAt로](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) 전달하여 읽거나 쓸 주소를 지정합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
