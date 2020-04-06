---
title: 아이디버그포트이벤트2::이벤트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725238"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
이 메서드는 포트에서 프로세스 및 프로그램의 생성 및 소멸을 나타내는 이벤트를 보냅니다.

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
【인】 디버그 서버를 나타내는 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 개체(모든 인스턴스에 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]대해 하나씩 있음)는 이벤트가 발생했습니다.

`pPort`\
【인】 이벤트가 발생한 포트를 나타내는 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 개체입니다.

`pProcess`\
【인】 이벤트가 발생한 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체입니다.

`pProgram`\
【인】 이벤트가 발생한 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`pEvent`\
【인】 이벤트를 식별하는 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 개체입니다. 가능한 이벤트는 다음과 같습니다.

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
【인】 이벤트의 GUID입니다. 이 메서드를 호출하기 전에 이벤트가 [IDebugEvent2로](../../../extensibility/debugger/reference/idebugevent2.md) 캐스팅되므로 이 식별자를 사용하면 전송되는 이벤트를 쉽게 확인할 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
