---
title: IDebugMemoryBytes2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727510"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
이 인터페이스는 바이트의 메모리를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 메모리의 바이트를 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
- [Getmemorybytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 는 시스템 메모리에 대 한 액세스를 제공 하기 위해이 인터페이스를 반환 합니다. [Getmemorybytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 및 [getmemorybytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) 는 개체의 바이트에 대 한 액세스를 제공 하기 위해이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugMemoryBytes2` .

|메서드|설명|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|지정 된 위치에서 시작 하 여 바이트 시퀀스를 읽습니다.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|`dwCount`에서 시작 하 여 바이트를 씁니다 `pStartContext` .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|이 인터페이스로 표시 되는 메모리의 크기 (바이트)를 가져옵니다.|

## <a name="remarks"></a>설명
 속성의 경우 배열을 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스는 `IDebugMemoryBytes2` 해당 배열의 값에 액세스 하는 인터페이스를 제공 합니다.

 Visual Studio의 **메모리 뷰** 는 [getmemorybytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 를 호출 하 여 `IDebugMemoryBytes2` 시스템 메모리 액세스를 위한 인터페이스를 검색 합니다. 액세스할 주소는 주소로 입력 한 식을 메모리 뷰에 구문 분석 한 다음 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 를 사용 하 여 구문 분석 된 식을 평가 하 여 인터페이스를 가져오는 방법으로 가져옵니다 `IDebugProperty2` . [Getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 를 호출 하면 메모리 주소를 설명 하는 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 이 반환 됩니다. 그런 다음이 메모리 컨텍스트는 [readat](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 및 [writeat](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)에 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
