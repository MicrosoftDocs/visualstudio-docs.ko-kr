---
title: IDebugProcess3:실행 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723676"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
중지된 상태에서 이 프로세스를 계속 실행합니다. 이전 실행 상태(예: 단계)가 지워지고 프로세스가 다시 실행됩니다.

> [!NOTE]
> 이 메서드는 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)대신 사용 해야 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
【인】 실행할 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 사용자가 다른 프로세스의 스레드에서 중지된 상태에서 실행을 시작하면 이 메서드가 이 프로세스에서 호출됩니다. 이 메서드는 사용자가 IDE의 **디버그** 메뉴에서 **시작** 명령을 선택할 때도 호출됩니다. 이 메서드의 구현은 프로세스의 현재 스레드에서 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드를 호출하는 것만큼 간단할 수 있습니다.

> [!WARNING]
> 이 호출을 처리하는 동안 중지 이벤트 또는 즉각적인(동기식) 이벤트를 [Event에](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 보내지 마십시오. 그렇지 않으면 디버거가 멈출 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [다시 시작](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
