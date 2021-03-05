---
description: 이 메서드는 포트에서 프로세스 및 프로그램을 만들고 소멸 시키는 이벤트를 전송 합니다.
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc975c2f48c560d0f15f08a6cc957c67ecc13808
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142910"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
이 메서드는 포트에서 프로세스 및 프로그램을 만들고 소멸 시키는 이벤트를 전송 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>매개 변수
`pMachine`\
진행 이벤트가 발생 한 디버그 서버 (의 모든 인스턴스에 대해 하나씩)를 나타내는 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 개체입니다 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

`pPort`\
진행 이벤트가 발생 한 포트를 나타내는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 개체입니다.

`pProcess`\
진행 이벤트가 발생 한 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체입니다.

`pProgram`\
진행 이벤트가 발생 한 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`pEvent`\
진행 이벤트를 식별 하는 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 개체입니다. 가능한 이벤트는 다음과 같습니다.

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
진행 이벤트의 GUID입니다. 이 메서드를 호출 하기 전에 이벤트를 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 로 캐스팅 하기 때문에이 식별자를 사용 하면 전송 되는 이벤트를 보다 쉽게 확인할 수 있습니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
