---
description: 디버그 엔진 (DE)을 중지 하려는 이유를 가져옵니다.
title: 'IDebugCanStopEvent2:: GetReason | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66b783044b8342de26aec831d9d41f8bccd7df92
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173526"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
디버그 엔진 (DE)을 중지 하려는 이유를 가져옵니다.

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
제한이 이 이벤트의 이유를 설명 하는 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 열거형의 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 일반적으로 [Canstop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 메서드 이전에 호출 되므로 호출자가 0이 아닌 ()을 메서드에 전달할지 여부를 결정할 수 있습니다 `TRUE` `IDebugCanStopEvent2::CanStop` .

 를 중지 하는 이유는이 될 수 있습니다 `CANSTOP_ENTRYPOINT` . 즉, de가 진입점에 도달 했거나 함수를 단계별로 실행할 수 있음을 의미 합니다 `CANSTOP_STEPIN` .

## <a name="see-also"></a>참고 항목
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
