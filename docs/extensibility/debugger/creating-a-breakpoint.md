---
title: 중단점 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d252f1310c3e251c44525cd94c4d9a2943d8171d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739048"
---
# <a name="create-a-breakpoint"></a>중단점 만들기
다음은 중단점을 만드는 프로세스에 대해 설명합니다.

## <a name="methods-in-breakpoint-creation"></a>중단점 생성의 메서드
 중단점을 바인딩하는 데 필요한 모듈이 로드되면 세션 디버그 관리자(SDM)는 다음 메서드를 호출합니다.

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind는** 사용자가 **중단점** 창에서 중단점을 만들 때만 호출됩니다.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>참조
- [호출 디버거 이벤트](../../extensibility/debugger/calling-debugger-events.md)
