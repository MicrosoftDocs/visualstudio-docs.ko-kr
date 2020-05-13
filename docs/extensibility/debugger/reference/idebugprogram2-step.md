---
title: IDebugProgram2::스텝 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722763"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
단계를 수행합니다.

> [!NOTE]
> 이 메서드는 더 이상 사용되지 않습니다. 대신 [단계](../../../extensibility/debugger/reference/idebugprocess3-step.md) 메서드를 사용합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
【인】 단계별 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

`sk`\
【인】 단계의 종류를 지정하는 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 열거형의 값입니다.

`step`\
【인】 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 열거형의 값으로 단계 단위를 지정합니다(예: 명령또는 명령).

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 스레드 간에 스레드 동기화 또는 통신이 있는 경우 특정 스레드가 스테핑될 때 프로그램의 다른 스레드가 실행되어야 합니다.

> [!WARNING]
> 이 호출을 처리하는 동안 중지 이벤트 또는 즉각적인(동기식) 이벤트를 [Event에](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 보내지 마십시오. 그렇지 않으면 디버거가 멈출 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
