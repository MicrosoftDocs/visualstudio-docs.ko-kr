---
title: IDebugProgram2::실행 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722977"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
중지된 상태에서 이 프로그램을 계속 실행합니다. 이전 실행 상태(예: 단계)가 지워지고 프로그램이 다시 실행됩니다.

> [!NOTE]
> 이 메서드는 더 이상 사용되지 않습니다. 대신 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) 메서드를 사용합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 사용자가 다른 프로그램의 스레드에서 중지된 상태에서 실행을 시작하면 이 메서드가 이 프로그램에서 호출됩니다. 이 메서드는 사용자가 IDE의 **디버그** 메뉴에서 **시작** 명령을 선택할 때도 호출됩니다. 이 메서드의 구현은 프로그램의 현재 스레드에서 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드를 호출하는 것만큼 간단할 수 있습니다.

> [!WARNING]
> 이 호출을 처리하는 동안 중지 이벤트 또는 즉각적인(동기식) 이벤트를 [Event에](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 보내지 마십시오. 그렇지 않으면 디버거가 멈출 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [다시 시작](../../../extensibility/debugger/reference/idebugthread2-resume.md)
