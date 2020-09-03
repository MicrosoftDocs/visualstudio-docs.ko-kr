---
title: 중단점이 바인딩 또는 바인딩 해제 되는 경우 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3253841778fe5a07e00b644423495b8ceee1a335
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712341"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>중단점이 바인딩 또는 바인딩 해제 되는 경우
[IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 메서드를 호출 하는 시점에 중단점을 바인딩할 수 없는 경우 중단점의 바인딩 시간과 생성 시간이 다릅니다.

## <a name="methods-called"></a>메서드 호출
 세션 디버그 관리자 (SDM)는 다음 메서드를 호출 합니다.

1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). DE는 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)을 반환 합니다.

2. [IDebugPendingBreakpoint2:: Enable을 사용](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)합니다.

3. [IDebugPendingBreakpoint2:: 가상화](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. [IDebugPendingBreakpoint2:: Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 메서드 및는 S_OK를 반환 합니다. DE는 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 또는 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)를 보냅니다.

5. [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 메서드는 바인딩된 중단점을 확인 하 고 가져옵니다.

## <a name="see-also"></a>추가 정보
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
