---
title: 예외 처리(비주얼 스튜디오 SDK) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738768"
---
# <a name="exception-handling-visual-studio-sdk"></a>예외 처리(비주얼 스튜디오 SDK)
다음은 예외가 throw될 때 발생하는 프로세스에 대해 설명합니다.

## <a name="exception-handling-process"></a>예외 처리 프로세스

1. 예외가 처음 throw되지만 디버깅 중인 프로그램의 예외 처리기에 의해 처리되기 전에 DEBug Engine(DE)은 세션 디버그 관리자(SDM)에 [IDebugExceptionEventEvent2를](../../extensibility/debugger/reference/idebugexceptionevent2.md) 중지 이벤트로 보냅니다. 예외에 대한 설정(디버그 패키지의 Exception 대화 상자에 지정)만 사용자가 첫 번째 예외 알림에서 중지하도록 지정하면 전송됩니다. `IDebugExceptionEvent2`

2. SDM은 예외의 속성을 얻기 위해 [IDebugExceptionEvent2:GetException을](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) 호출합니다.

3. 디버그 패키지호출 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 는 사용자에게 어떤 옵션을 표시할지 결정합니다.

4. 디버그 패키지는 첫 번째 기회 예외 대화 상자를 열어 예외를 처리하는 방법을 사용자에게 묻습니다.

5. 사용자가 계속하도록 선택하면 SDM에서 [IDebugExceptionEvent2:CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)를 호출합니다.

    - 메서드가 S_OK 반환하는 경우 [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)를 호출합니다.

         또는

         메서드가 S_FALSE 반환하는 경우 디버깅 중인 프로그램에 예외를 처리할 수 있는 두 번째 기회가 주어집니다.

6. 디버깅 중인 프로그램에 두 번째 예외에 대한 처리기가 없는 `IDebugExceptionEvent2` 경우 DE는 sDM을 **EVENT_SYNC_STOP**.

7. 디버그 패키지는 첫 번째 기회 예외 대화 상자를 열어 예외를 처리하는 방법을 사용자에게 묻습니다.

8. 디버그 패키지호출 [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 는 사용자에게 어떤 옵션을 표시할지 결정합니다.

9. 디버그 패키지는 두 번째 예외 대화 상자를 열어 예외를 처리하는 방법을 사용자에게 묻습니다.

10. 메서드가 S_OK 반환하는 `IDebugExceptionEvent2::PassToDebuggee`경우 를 호출합니다.

## <a name="see-also"></a>참조
- [호출 디버거 이벤트](../../extensibility/debugger/calling-debugger-events.md)
