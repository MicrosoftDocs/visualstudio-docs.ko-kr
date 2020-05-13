---
title: 아이디버그이벤트콜백2::이벤트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729900"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
디버그 이벤트에 대한 알림을 보냅니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>매개 변수
`pEngine`\
【인】 이 이벤트를 보내는 DE(디버그 엔진)를 나타내는 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 개체입니다. 이 매개 변수를 작성하려면 DE가 필요합니다.

`pProcess`\
【인】 이벤트가 발생하는 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체입니다. 이 매개 변수는 세션 디버그 관리자(SDM)에 의해 채워져 있습니다. DE는 항상 이 매개 변수에 대한 null 값을 전달합니다.

`pProgram`\
【인】 이 이벤트가 발생하는 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다. 대부분의 이벤트에서 이 매개 변수는 null 값이 아닙니다.

`pThread`\
【인】 이 이벤트가 발생하는 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다. 이벤트를 중지하는 경우 이 매개 변수는 이 매개 변수에서 스택 프레임을 가져오므로 null 값이 될 수 없습니다.

`pEvent`\
【인】 디버그 이벤트를 나타내는 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 개체입니다.

`riidEvent`\
【인】 매개 변수에서 가져올 이벤트 인터페이스를 `pEvent` 식별하는 GUID입니다.

`dwAttrib`\
【인】 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 열거형의 플래그 조합입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드를 호출할 때 매개 변수는 매개 변수에 `dwAttrib` 전달 된 event 개체에 호출 된 [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) 메서드에서 반환 된 값일치 해야 `pEvent` 합니다.

 이벤트 자체가 비동기인지 여부에 관계없이 모든 디버그 이벤트는 비동기적으로 게시됩니다. DE가 이 메서드를 호출할 때 반환 값은 이벤트가 처리되었는지 여부를 나타내지 않으며 이벤트가 수신되었는지 여부만 나타냅니다. 실제로 대부분의 경우 이 메서드가 반환될 때 이벤트가 처리되지 않았습니다.

## <a name="see-also"></a>참조
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
