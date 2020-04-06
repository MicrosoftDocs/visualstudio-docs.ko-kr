---
title: 중단점 타격 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738571"
---
# <a name="hit-a-breakpoint"></a>중단점 도달
다음 섹션에서는 DE(디버그 엔진)가 실행 중이거나 스테핑하는 동안 중단점에 도달한 프로세스에 대해 설명합니다.

## <a name="troubleshoot-a-hit-breakpoint"></a>적중 중단점 문제 해결

1. DE는 [iDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 인터페이스를 **EVENT_SYNC_STOP**보냅니다.

2. 세션 디버그 관리자(SDM)는 [IDebugBreakpointEvent2:::EnumBreakpoint를](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 호출하여 적중된 중단점을 가져옵니다.

## <a name="see-also"></a>참조
- [호출 디버거 이벤트](../../extensibility/debugger/calling-debugger-events.md)
