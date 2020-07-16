---
title: 실행 제어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c885c0c983e6fafd69d55b3d68f8ed6e8ff2628c
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387267"
---
# <a name="control-of-execution"></a>실행 제어
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 (DE)은 일반적으로 다음 이벤트 중 하나를 마지막 시작 이벤트로 보냅니다.  
  
- 진입점 이벤트는 새로 시작 된 프로그램에 연결 하는 경우  
  
- 이미 실행 중인 프로그램에 연결 하는 경우의 load complete 이벤트입니다.  
  
  이러한 두 이벤트는 모두 이벤트를 중지 하는 것입니다. 즉, DE는 IDE를 통해 사용자의 응답을 대기 합니다. 자세한 내용은 [운영 모드](../../extensibility/debugger/operational-modes.md)를 참조 하세요.  
  
## <a name="stopping-event"></a>이벤트 중지  
 중지 이벤트가 디버그 세션으로 전송 되는 경우:  
  
1. 현재 명령 포인터를 포함 하는 프로그램 및 스레드를 이벤트 인터페이스에서 가져올 수 있습니다.  
  
2. IDE는 현재 소스 코드 파일 및 위치를 확인 합니다 .이 파일은 편집기에 강조 표시 되어 있습니다.  
  
3. 디버그 세션은 일반적으로 프로그램의 **Continue** 메서드를 호출 하 여이 첫 번째 중지 이벤트에 응답 합니다.  
  
4. 그런 다음 중단점에 도달 하는 것과 같은 중지 조건이 발생할 때까지 프로그램이 실행 됩니다 .이 경우 DE는 중단점 이벤트를 디버그 세션으로 보냅니다. 중단점 이벤트는 중지 이벤트이 고 DE는 사용자 응답을 다시 기다립니다.  
  
5. 사용자가 함수를 한 단계씩 코드 실행, 프로시저 단위 실행 또는 외부로 이동 하는 경우, IDE는 프로그램의 메서드를 호출 하 여 단계 `Step` 단위 (명령, 문 또는 줄)와 단계 종류 (즉, 함수를 한 단계씩 실행 하거나 프로시저 단위로 실행 하는지 여부)를 전달 하는 디버그 세션을 요청 합니다. 단계가 완료 되 면 DE는 중지 이벤트 인 디버그 세션에 step complete 이벤트를 보냅니다.  
  
    또는  
  
    사용자가 현재 명령 포인터에서 계속 실행 하는 경우 IDE는 프로그램의 **Execute** 메서드를 호출 하는 디버그 세션을 요청 합니다. 프로그램은 다음 중지 조건이 발생할 때까지 실행을 다시 시작 합니다.  
  
    또는  
  
    디버그 세션에서 특정 중지 이벤트를 무시 하는 경우 디버그 세션은 프로그램의 **Continue** 메서드를 호출 합니다. 프로그램이 중지 조건이 발생 했을 때 함수를 한 단계씩 실행 하거나 함수를 실행 한 후에는 해당 단계를 계속 합니다.  
  
   프로그래밍 방식으로 중단 조건이 발생 하면 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 또는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 와 같은 중지 이벤트를 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스를 통해 세션 디버그 관리자 (SDM)로 보냅니다. DE는 프로그램을 나타내는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 및 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 인터페이스와 현재 명령 포인터를 포함 하는 스레드를 전달 합니다. SDM은 [IDebugThread2:: Enum프레임 정보](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 를 호출 하 여 상위 스택 프레임을 가져오고 [IDebugStackFrame2:: getdocumentcontext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 를 호출 하 여 현재 명령 포인터와 연결 된 문서 컨텍스트를 가져옵니다. 이 문서 컨텍스트는 일반적으로 소스 코드 파일 이름, 줄 및 열 번호입니다. IDE는이를 사용 하 여 현재 명령 포인터를 포함 하는 소스 코드를 강조 표시 합니다.  
  
   일반적으로 SDM은 [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)를 호출 하 여이 첫 번째 중지 이벤트에 응답 합니다. 그런 다음 중단점에 도달 하는 것과 같은 중지 조건이 발생할 때까지 프로그램이 실행 됩니다 .이 경우 DE가 [IDebugBreakpointEvent2 인터페이스](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 를 SDM으로 보냅니다. 중단점 이벤트는 중지 이벤트이 고 DE는 사용자 응답을 다시 기다립니다.  
  
   사용자가 함수를 한 단계씩 코드 실행, 프로시저 단위 실행 또는 외부로 이동 하는 경우 IDE에서는 [IDebugProgram2:: step](../../extensibility/debugger/reference/idebugprogram2-step.md)을 호출 하 여 [stunit](../../extensibility/debugger/reference/stepunit.md) (명령, 문 또는 줄)과 [stkind](../../extensibility/debugger/reference/stepkind.md), 즉 함수를 한 단계씩 실행 하거나 프로시저를 프로시저 단위로 전달 하는지 여부를 전달 합니다. 단계가 완료 되 면 DE는 중지 이벤트 인 SDM에 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 인터페이스를 보냅니다.  
  
   사용자가 현재 명령 포인터에서 계속 실행 하는 경우 IDE는 SDM에 [IDebugProgram2:: Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)를 호출 하도록 요청 합니다. 프로그램은 다음 중지 조건이 발생할 때까지 실행을 다시 시작 합니다.  
  
   디버그 패키지에서 특정 중지 이벤트를 무시 하는 경우 디버그 패키지는 [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)를 호출 하는 SDM를 호출 합니다. 프로그램이 중지 조건이 발생 했을 때 함수를 한 단계씩 실행 하거나 함수를 실행 한 후에는 해당 단계를 계속 합니다. 이는 프로그램에서 단계별 상태를 유지 하 여 계속 하는 방법을 알 수 있음을 의미 합니다.  
  
   SDM에서 수행 하 `Step` 고 **실행**하 고 **계속** 하는 호출은 비동기적입니다. 즉, sdm에서 호출이 빠르게 반환 될 것으로 예상 합니다. DE가 SDM을 이전, 실행 또는 계속 반환 되기 전에 동일한 스레드에서 중지 이벤트를 보내면 `Step` sdm의 응답이 중지 됩니다. **Execute** **Continue**  
  
## <a name="see-also"></a>참고 항목  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
