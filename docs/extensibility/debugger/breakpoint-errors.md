---
title: 중단점 오류 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739221"
---
# <a name="breakpoint-errors"></a>중단점 오류
다음은 중단점이 코드에 바인딩하려고 시도했지만 실패하는 프로세스에 대해 설명합니다.

## <a name="troubleshoot-a-breakpoint-error"></a>중단점 오류 문제 해결

1. 디버그 엔진(DE)은 세션 디버그 관리자(SDM)에 [IDebugBreakpointErrorEvent2를](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 보냅니다.

2. SDM은 오류 중단점을 얻기 위해 [IDebugBreakpointErrorEvent2::GetErrorBreakpoint(IDebugErrorBreakpoint2**)를](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) `ppErrorBP`호출합니다.

3. SDM은 [IDebugErrorBreakpoint2::GetPending중단점을](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) 호출하여 오류 중단점이 시작된 보류 중인 중단점을 가져옵니다.

4. SDM은 [IDebugErrorBreakpoint2::GetBreakpointResolution을](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 호출하여 오류 중단점이 바인딩에 실패한 이유를 확인합니다.

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
