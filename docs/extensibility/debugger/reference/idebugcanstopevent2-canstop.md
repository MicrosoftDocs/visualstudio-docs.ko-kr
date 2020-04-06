---
title: IDebugCanStopEvent2::캔스탑 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734598"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
디버그 엔진(DE)은 현재 코드 위치에서 중지할지 아니면 실행을 계속할지 여부를 지정합니다.

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
【인】 0이 아닌`TRUE`( ) DE가 현재 코드 위치에서 중지되어야 하는 경우; 그렇지 않으면`FALSE`0 ()입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 이벤트의 수신자는 일반적으로 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 메서드를 호출하여 DE가 중지하려는 `IDebugCanStopEvent2::CanStop` 이유를 결정한 다음 적절한 응답으로 메서드를 호출합니다.

 DE가 중지되면 중지 이유를 설명하는 이벤트를 보냅니다. 일반적으로 전송되는 두 개의 이벤트, [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 인터페이스로 표시되는 사용자 또는 신호 나누기 및 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 인터페이스로 표시되는 중단점 이벤트가 있습니다.

## <a name="see-also"></a>참조
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
