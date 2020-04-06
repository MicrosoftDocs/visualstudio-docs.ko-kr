---
title: 중단점이 바인딩되거나 언바운드되는 경우 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712341"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>중단점이 바인딩되거나 언바운드되는 경우
[IDebugPendingBreakpoint2:CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 메서드에 대한 호출이 수행될 때 중단점을 바인딩할 수 없는 경우 바인딩 시간 및 중단점 만들기 시간이 다릅니다.

## <a name="methods-called"></a>메서드라는
 세션 디버그 관리자(SDM)는 다음 메서드를 호출합니다.

1. [IDebugEngine2:만들기보류 중단점](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). DE는 [IDebugPending중단지점2를](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)반환합니다.

2. [IDebugPending중단점2::사용](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPending중단점2:가상화](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. [IDebugPending중단점2:바인딩](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 메서드및 S_OK 반환합니다. DE는 [IDebugBreakpoint바운드이벤트2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 또는 [IDebugBreakpointErrorEvent2를](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)보냅니다.

5. [IDebugBreakpoint바운드이벤트2:GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 및 [IDebugBreakpoint바운드Event2::EnumBoundBreak포인트](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 메서드를 확인 하 고 바인딩된 중단점을 가져옵니다.

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
