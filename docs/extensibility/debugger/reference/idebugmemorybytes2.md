---
title: 아이데버그메모리바이트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727510"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
이 인터페이스는 바이트의 메모리를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE버그 엔진(DE)은 이 인터페이스를 구현하여 메모리의 바이트를 나타냅니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 시스템 메모리에 대 한 액세스를 제공 하기 위해이 인터페이스를 반환 합니다. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 및 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) 개체의 바이트에 대 한 액세스를 제공 하기 위해이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugMemoryBytes2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|지정된 위치에서 시작하여 일련의 바이트를 읽습니다.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|에서 `dwCount` 시작하여 바이트를 `pStartContext`씁니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|이 인터페이스로 표시되는 메모리의 크기를 바이트로 가져옵니다.|

## <a name="remarks"></a>설명
 속성의 경우 배열을 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스는 해당 배열의 `IDebugMemoryBytes2` 값에 액세스하는 인터페이스를 제공합니다.

 Visual Studio의 **메모리 뷰는** [GetMemoryBytes를](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 호출하여 시스템 메모리에 액세스하기 위한 `IDebugMemoryBytes2` 인터페이스를 검색합니다. 액세스할 주소는 메모리 뷰에 주소로 입력된 식을 구문 분석한 다음 [EvaluateSync를](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 사용하여 구문 분석된 `IDebugProperty2` 식을 평가하여 인터페이스를 가져옵니다. [GetMemoryContext에](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 대 한 호출 메모리 주소를 설명 하는 [IDebugMemoryContext2반환](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 합니다. 그런 다음 이 메모리 컨텍스트를 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 및 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)로 전달합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
