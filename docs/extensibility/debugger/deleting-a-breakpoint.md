---
title: 중단점 삭제 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738945"
---
# <a name="deleting-a-breakpoint"></a>중단점 삭제
다음은 보류 중인 중단점을 삭제할 때의 프로세스에 대해 설명합니다.

## <a name="deletion-process"></a>삭제 프로세스
 세션 디버그 관리자(SDM)는 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 메서드를 호출하여 보류 중인 중단점과 바인딩된 모든 바인딩된 중단점을 제거합니다.

> [!NOTE]
> [IDebugBoundBreakpoint2::Delete에](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)대한 호출로 단일 바인딩중단점을 삭제할 수도 있습니다.

## <a name="see-also"></a>참조
- [호출 디버거 이벤트](../../extensibility/debugger/calling-debugger-events.md)
