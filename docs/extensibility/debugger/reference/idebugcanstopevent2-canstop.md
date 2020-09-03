---
title: 'IDebugCanStopEvent2:: CanStop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734598"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
현재 코드 위치에서 중지할지 아니면 실행을 계속할지를 디버그 엔진에 알립니다 (DE).

## <a name="syntax"></a>구문

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>매개 변수
`fCanStop`\
진행 `TRUE`현재 코드 위치에서 DE를 중지 해야 하면 0이 아니고, 그렇지 않으면 0 () `FALSE` 입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 일반적으로이 이벤트의 수신자는 [Getreason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 메서드를 호출 하 여 DE를 중지 하는 이유를 확인 한 다음 `IDebugCanStopEvent2::CanStop` 적절 한 응답을 사용 하 여 메서드를 호출 합니다.

 DE가 중지 되 면 중지 이유를 설명 하는 이벤트를 보냅니다. 일반적으로 전송 되는 이벤트 두 개, [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 인터페이스로 표시 되는 사용자 또는 신호 중단, [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 인터페이스로 표시 되는 중단점 이벤트 등이 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
