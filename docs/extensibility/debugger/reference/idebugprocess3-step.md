---
title: IDebugProcess3::단계 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723557"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
프로세스가 한 단계의 명령이나 문을 단계별로 처리하게 합니다.

> [!NOTE]
> 이 메서드는 [단계](../../../extensibility/debugger/reference/idebugprogram2-step.md)대신 사용 해야 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
【인】 단계별 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

`sk`\
【인】 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 값 중 하나입니다.

`step`\
【인】 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 값 중 하나입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 스레드 간에 스레드 동기화 또는 통신이 있는 경우 특정 스레드가 스테핑될 때 프로세스의 다른 스레드가 실행되어야 합니다.

 **경고 메시지** 이 호출을 처리하는 동안 중지 이벤트 또는 즉각적인(동기식) 이벤트를 [Event에](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 보내지 마십시오. 그렇지 않으면 디버거가 멈출 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
