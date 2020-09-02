---
title: 'IDebugProcess3:: Step | Microsoft Docs'
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
ms.openlocfilehash: 054cfc305400e3916ed7ba796a74370dfc2c77a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386695"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
프로세스에서 하나의 명령 또는 문을 단계별로 실행 합니다.

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
진행 단계별 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

`sk`\
진행 [Stkind](../../../extensibility/debugger/reference/stepkind.md) 값 중 하나입니다.

`step`\
진행 [Stunit](../../../extensibility/debugger/reference/stepunit.md) 값 중 하나입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 스레드 동기화 또는 스레드 간 통신이 있는 경우 특정 스레드가 단계별로 실행 될 때 프로세스의 다른 스레드를 실행 해야 합니다.

 **경고** 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
