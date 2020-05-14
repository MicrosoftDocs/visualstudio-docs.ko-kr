---
title: IDebugProcess3:계속 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723774"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
중지된 상태에서 이 프로세스를 계속 실행합니다. 이전 실행 상태(예: 단계)는 유지되고 프로세스가 다시 실행하기 시작합니다.

> [!NOTE]
> 이 메서드는 [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md)하지 않고 사용 해야 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Continue(
   IDebugThread2* pThread
);
```

```csharp
int Continue(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
【인】 계속할 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 디버깅 중인 프로세스 수 또는 중지 이벤트를 생성한 프로세스에 관계없이 이 프로세스에서 호출됩니다. 구현은 이전 실행 상태(예: 단계)를 유지하고 이전 실행을 완료하기 전에 중지한 적이 없는 것처럼 실행을 계속해야 합니다. 즉, 이 프로세스의 스레드가 스텝오버 작업을 수행하고 있고 다른 프로세스가 중지되었기 `Continue` 때문에 중지된 경우 지정된 스레드가 원래 스텝오버 작업을 완료해야 합니다.

 **경고 메시지** 이 호출을 처리하는 동안 중지 이벤트 또는 즉각적인(동기식) 이벤트를 [Event에](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 보내지 마십시오. 그렇지 않으면 디버거가 멈출 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
