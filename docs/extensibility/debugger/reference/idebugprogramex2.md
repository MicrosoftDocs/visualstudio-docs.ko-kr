---
title: 아이디버그프로그램Ex2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722336"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
이 인터페이스를 사용하면 세션 디버그 관리자(SDM)가 프로그램에 연결하고 프로그램과 연결된 프로그램 노드를 얻을 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 SDM이 프로그램에 연결하는 동시에 포트 공급자가 프로그램에 연결된 모든 세션을 추적할 수 있도록 하기 위해 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스와 동일한 개체에 이 인터페이스를 구현합니다. 사용자 지정 포트 공급자가 선택한 경우 이 인터페이스를 구현할 수 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 SDM은 `IDebugProgram2` 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출하여 이 인터페이스를 사용하여 프로그램에 연결된 세션을 추적합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProgramEx2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[연결](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|프로그램을 세션에 연결합니다.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|프로그램과 연결된 프로그램 노드를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 SDM과 프로그램 간에 비공개입니다.

## <a name="requirements"></a>요구 사항
 헤더: 포트프리브.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
