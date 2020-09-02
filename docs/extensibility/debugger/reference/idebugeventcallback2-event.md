---
title: 'IDebugEventCallback2:: Event | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729900"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
디버그 이벤트에 대 한 알림을 보냅니다.

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
진행 이 이벤트를 전송 하는 디버그 엔진 (DE)을 나타내는 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 개체입니다. 이 매개 변수를 작성 하려면 DE가 필요 합니다.

`pProcess`\
진행 이벤트가 발생 하는 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체입니다. 이 매개 변수는 세션 디버그 관리자 (SDM)에 의해 채워집니다. DE는 항상이 매개 변수에 null 값을 전달 합니다.

`pProgram`\
진행 이 이벤트가 발생 하는 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다. 대부분의 이벤트의 경우이 매개 변수는 null 값이 아닙니다.

`pThread`\
진행 이 이벤트가 발생 하는 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다. 이 매개 변수에서 스택 프레임을 가져올 때 이벤트를 중지 하는 경우이 매개 변수는 null 값일 수 없습니다.

`pEvent`\
진행 디버그 이벤트를 나타내는 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 개체입니다.

`riidEvent`\
진행 매개 변수에서 가져올 이벤트 인터페이스를 식별 하는 GUID입니다 `pEvent` .

`dwAttrib`\
진행 [Eventattributes](../../../extensibility/debugger/reference/eventattributes.md) 열거형의 플래그 조합입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드를 호출할 때 매개 변수는 `dwAttrib` 매개 변수에 전달 된 이벤트 개체에서 호출 되는 [getattributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) 메서드에서 반환 된 값과 일치 해야 합니다 `pEvent` .

 모든 디버그 이벤트는 이벤트 자체가 비동기 인지 여부에 관계 없이 비동기적으로 게시 됩니다. DE가이 메서드를 호출 하는 경우 반환 값은 이벤트가 처리 되었는지 여부는 이벤트를 받았는지 여부를 나타내지 않습니다. 실제로 대부분의 경우이 메서드가 반환 될 때 이벤트가 처리 되지 않습니다.

## <a name="see-also"></a>추가 정보
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
