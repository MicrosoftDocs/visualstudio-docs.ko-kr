---
title: 중단점 적중 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738571"
---
# <a name="hit-a-breakpoint"></a>중단점 도달
다음 섹션에서는 실행 중이거나 단계별로 실행 하는 동안 디버그 엔진 (DE)이 중단점에 도달 하는 경우의 프로세스에 대해 설명 합니다.

## <a name="troubleshoot-a-hit-breakpoint"></a>적중 중단점 문제 해결

1. DE는 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 인터페이스를 **EVENT_SYNC_STOP**보냅니다.

2. 세션 디버그 관리자 (SDM)는 적중 된 중단점을 가져오기 위해 [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 를 호출 합니다.

## <a name="see-also"></a>추가 정보
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
