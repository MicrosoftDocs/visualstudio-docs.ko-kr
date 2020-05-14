---
title: IDebugCanStopEvent2::GetReason | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734527"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
DE(디버그 엔진)가 중지하려는 이유를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>매개 변수
`pcr`\
【아웃】 이 이벤트의 이유를 설명하는 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 열거형의 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 일반적으로 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 메서드 전에 호출되므로 호출자는 0이`TRUE`아닌 `IDebugCanStopEvent2::CanStop` () 메서드를 전달할지 여부를 결정할 수 있습니다.

 중지 `CANSTOP_ENTRYPOINT`이유는 DE가 진입점에 도달했거나 `CANSTOP_STEPIN`DE가 함수에 들어갔다는 것을 의미합니다.

## <a name="see-also"></a>참조
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
