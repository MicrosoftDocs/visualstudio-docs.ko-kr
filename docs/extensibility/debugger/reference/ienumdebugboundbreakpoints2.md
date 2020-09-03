---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717448"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
이 인터페이스는 보류 중인 중단점 또는 중단점 바인딩 이벤트와 연결 된 바인딩된 중단점을 열거 합니다.

## <a name="syntax"></a>Syntax

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 중단점에 대 한 지원의 일부로이 인터페이스를 구현 합니다. 중단점이 지원 되는 경우이 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 Visual Studio는 다음을 호출 합니다.

- 트리거된 [중단점](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) -트리거된 모든 중단점 목록을 나타내는이 인터페이스를 가져옵니다.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 는 바인딩된 모든 중단점 목록을 나타내는이 인터페이스를 가져옵니다.

- 보류 중인 중단점에 바인딩된 모든 중단점 목록을 나타내는이 인터페이스를 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) .

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugBoundBreakpoints2` .

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|열거형 시퀀스에서 지정 된 수의 바인딩된 중단점을 검색 합니다.|
|[skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|열거형 시퀀스에서 지정 된 수의 바인딩된 중단점을 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|열거자의 바인딩된 중단점 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는이 인터페이스로 표시 되는 바인딩된 중단점을 사용 하 여 IDE의 중단점 표시를 업데이트 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
