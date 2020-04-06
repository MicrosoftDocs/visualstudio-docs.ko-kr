---
title: IDebugProgram2::계속 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723069"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
중지된 상태에서 이 프로그램을 계속 실행합니다. 이전 실행 상태(예: 단계)가 유지되고 프로그램이 다시 실행하기 시작합니다.

> [!NOTE]
> 이 메서드는 더 이상 사용되지 않습니다. 대신 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드를 사용합니다.

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
`pThread`【인】 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 디버깅 중인 프로그램 수 또는 중지 이벤트를 생성한 프로그램에 관계없이 이 프로그램에서 호출됩니다. 구현은 이전 실행 상태(예: 단계)를 유지하고 이전 실행을 완료하기 전에 중지한 적이 없는 것처럼 실행을 계속해야 합니다. 즉, 이 프로그램의 스레드가 스텝오버 작업을 수행하고 있고 다른 프로그램이 중지되어 중지된 다음 이 메서드가 호출된 경우 프로그램이 원래 단계별 작업을 완료해야 합니다.

> [!WARNING]
> 이 호출을 처리하는 동안 중지 이벤트 또는 즉각적인(동기식) 이벤트를 [Event에](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 보내지 마십시오. 그렇지 않으면 디버거가 멈출 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
