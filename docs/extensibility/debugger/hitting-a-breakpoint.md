---
title: 중단점 적중 | Microsoft Docs
description: 이 문서에서는 실행 중이거나 단계별로 실행 하는 동안 디버그 엔진이 중단점에 도달할 때 발생 하는 프로세스를 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e093437fcc8b3e1e2663c2a46ebb3b70d32efbec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059953"
---
# <a name="hit-a-breakpoint"></a>중단점 도달
다음 섹션에서는 실행 중이거나 단계별로 실행 하는 동안 디버그 엔진 (DE)이 중단점에 도달 하는 경우의 프로세스에 대해 설명 합니다.

## <a name="troubleshoot-a-hit-breakpoint"></a>적중 중단점 문제 해결

1. DE는 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 인터페이스를 **EVENT_SYNC_STOP** 보냅니다.

2. 세션 디버그 관리자 (SDM)는 적중 된 중단점을 가져오기 위해 [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 를 호출 합니다.

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
