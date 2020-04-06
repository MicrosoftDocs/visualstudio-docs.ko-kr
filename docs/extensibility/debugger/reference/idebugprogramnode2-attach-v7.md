---
title: IDebugProgramNode2::Attach_V7 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722133"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> 되지 않는. 사용하지 마십시오.

## <a name="syntax"></a>구문

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>매개 변수

`pMDMProgram`\
【인】 연결할 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스입니다.

`pCallback`\
【인】 디버그 이벤트를 SDM에 보내는 데 사용할 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스입니다.

`dwReason`\
【인】 첨부 이유를 지정하는 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 열거형의 값입니다.

## <a name="return-value"></a>Return Value

구현은 항상 `E_NOTIMPL`반환되어야 합니다.

## <a name="remarks"></a>설명

> [!WARNING]
> Visual Studio 2005에서 이 메서드는 더 이상 `E_NOTIMPL`사용되지 않으며 항상 반환해야 합니다. 프로그램 노드가 연결할 수 없음을 나타내야 하거나 프로그램 노드가 단순히 프로그램을 `GUID`설정하는 경우 다른 방법은 [IDebugProgramNodeNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스를 참조하십시오. 그렇지 않으면 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 구현합니다.

## <a name="prior-to-visual-studio-2005"></a>비주얼 스튜디오 2005 이전

이 메서드는 DE가 디버깅 중인 프로그램의 주소 공간에서 실행되는 경우에만 구현해야 합니다. 그렇지 않으면 이 `S_FALSE`메서드가 반환해야 합니다.

이 메서드를 호출 하는 경우 DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) 이벤트 개체를 보내야 합니다., [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스의이 인스턴스에 대 한 전송 되지 않은 경우 뿐만 아니라 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 및 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 이벤트 개체입니다. [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 이벤트 개체는 `dwReason` 매개 변수가 `ATTACH_REASON_LAUNCH`있는 경우 전송됩니다.

DE는 `IDebugProgram2` [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogram2.md) 이벤트 개체에서 제공하는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 개체에서 [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 호출해야 하며 DE에서 구현한 개체에 대한 인스턴스 데이터에 해당 프로그램의 GUID를 저장해야 합니다.

## <a name="see-also"></a>참조

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
