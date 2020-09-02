---
title: 'IDebugProgram2:: Execute | Microsoft Docs'
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
ms.openlocfilehash: af4650b5523595350543ac549ac162247563e418
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386747"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
중지 된 상태에서이 프로그램을 계속 실행 합니다. 모든 이전 실행 상태 (예: 단계)는 지워지고 프로그램의 실행이 다시 시작 됩니다.

> [!NOTE]
> 이 메서드는 더 이상 사용되지 않습니다. 대신 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) 메서드를 사용 해야 합니다.

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
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 사용자가 다른 프로그램의 스레드에서 중지 된 상태에서 실행을 시작 하면이 메서드가이 프로그램에서 호출 됩니다. 이 메서드는 사용자가 IDE의 **디버그** 메뉴에서 **시작** 명령을 선택 하는 경우에도 호출 됩니다. 이 메서드의 구현은 프로그램의 현재 스레드에서 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드를 호출 하는 것 처럼 간단할 수 있습니다.

> [!WARNING]
> 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [재개](../../../extensibility/debugger/reference/idebugthread2-resume.md)
