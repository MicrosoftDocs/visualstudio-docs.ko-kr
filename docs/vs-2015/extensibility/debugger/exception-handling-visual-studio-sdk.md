---
title: 예외 처리 (Visual Studio SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e646f032a12de48bbfb55b089462c7f8a4dd26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152802"
---
# <a name="exception-handling-visual-studio-sdk"></a>예외 처리(Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음에서는 예외가 throw 될 때 발생 하는 프로세스에 대해 설명 합니다.  
  
## <a name="exception-handling-process"></a>예외 처리 프로세스  
  
1. 예외가 처음 throw 될 때 디버깅 중인 프로그램의 예외 처리기에서 처리 되기 전에 디버그 엔진 (DE)은 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 를 세션 디버그 관리자 (SDM)에 게 중지 이벤트로 보냅니다. `IDebugExceptionEvent2`예외에 대 한 설정 (디버그 패키지의 예외 대화 상자에서 지정)만 사용자가 첫 번째 예외 알림에 대해 중지 하도록 지정 하는 경우이 전송 됩니다.  
  
2. SDM은 [IDebugExceptionEvent2:: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) 을 호출 하 여 예외의 속성을 가져옵니다.  
  
3. 디버그 패키지는 [IDebugExceptionEvent2:: Can Sto디버기](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 를 호출 하 여 사용자에 게 표시할 옵션을 결정 합니다.  
  
4. 디버그 패키지는 첫 번째 예외 대화 상자를 열어 예외를 처리 하는 방법을 사용자에 게 요청 합니다.  
  
5. 사용자가 계속 하도록 선택 하는 경우 SDM은 [IDebugExceptionEvent2:: Can Sto디버기](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)를 호출 합니다.  
  
    - 메서드가 S_OK 반환 하는 경우 [IDebugExceptionEvent2::P assToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)를 호출 합니다.  
  
         또는  
  
         메서드가 S_FALSE 반환 하는 경우 디버깅 중인 프로그램에 예외를 처리할 수 있는 두 번째 기회가 제공 됩니다.  
  
6. 디버깅 중인 프로그램에 두 번째 예외에 대 한 처리기가 없는 경우 DE는 `IDebugExceptionEvent2` **EVENT_SYNC_STOP**로 SDM에를 보냅니다.  
  
7. 디버그 패키지는 첫 번째 예외 대화 상자를 열어 예외를 처리 하는 방법을 사용자에 게 요청 합니다.  
  
8. 디버그 패키지는 [IDebugExceptionEvent2:: Can Sto디버기](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 를 호출 하 여 사용자에 게 표시할 옵션을 결정 합니다.  
  
9. 디버그 패키지는 두 번째 예외 대화 상자를 열어 예외를 처리 하는 방법을 사용자에 게 요청 합니다.  
  
10. 메서드가 S_OK 반환 하는 경우는를 호출 `IDebugExceptionEvent2::PassToDebuggee` 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
