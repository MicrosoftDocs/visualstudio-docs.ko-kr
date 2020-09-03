---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725643"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
이 인터페이스는 코드 위치에 바인딩할 준비가 된 중단점을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 중단점에 대 한 지원의 일부로이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 에 대 한 호출은 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 인터페이스에서 보류 중인 중단점을 만듭니다. [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 를 호출 하면 `IDebugBreakpoint2` 프로그램에서 바인딩된 중단점을 나타내는 인터페이스가 만들어집니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPendingBreakpoint2` .

|메서드|설명|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|보류 중인이 중단점을 코드 위치에 바인딩할 수 있는지 여부를 확인 합니다.|
|[바인딩하며](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|이 보류 중인 중단점을 하나 이상의 코드 위치에 바인딩합니다.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|이 보류 중인 중단점의 상태를 가져옵니다.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|이 보류 중인 중단점을 만드는 데 사용 된 중단점 요청을 가져옵니다.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|이 보류 중인 중단점의 가상화 된 상태를 전환 합니다.|
|[사용](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|보류 중인이 중단점의 활성화 상태를 설정/해제 합니다.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|이 보류 중인 중단점과 연결 된 조건을 설정 하거나 변경 합니다.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|이 보류 중인 중단점과 연결 된 패스 수를 설정 하거나 변경 합니다.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|이 보류 중인 중단점에서 바인딩된 모든 중단점을 열거 합니다.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|이 보류 중인 중단점에서 발생 한 모든 오류 중단점을 열거 합니다.|
|[Delete](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|보류 중인이 중단점과이 중단점에서 바인딩된 모든 중단점을 삭제 합니다.|

## <a name="remarks"></a>설명
 `IDebugPendingBreakpoint2` 는 하나 이상의 프로그램에 적용 될 수 있는 코드에 중단점을 바인딩하는 데 필요한 모든 정보를 제공 하는 것으로 간주할 수 있습니다.

 보류 중인 중단점에는 두 개 이상의 바인딩된 중단점이 생성 될 수 있습니다. 예를 들어 c + + 스타일 템플릿의 중단점은 해당 템플릿의 각 고유 인스턴스에 대해 바인딩된 중단점을 생성할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
