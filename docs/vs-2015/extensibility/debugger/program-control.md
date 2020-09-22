---
title: 프로그램 제어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8102bc488d5c74f751fb93584016aa6904fbe2d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841678"
---
# <a name="program-control"></a>프로그램 제어
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 디버깅에서는 다음의 단계별 실행 및 계속 루틴이 프로그램 수준에서 발생 합니다.  
  
- 다음 문을 설정 합니다. 즉, 특정 프레임 환경에서 실행 되는 다음 명령으로 컴퓨터를 설정 합니다.  
  
- 실행 중, 즉 단계별 모드 종료를 계속 종료 합니다.  
  
- 다음 명령을 실행 합니다.  
  
- 현재 스테핑 모드 계속  
  
- 프로그램에 포함 된 스레드 일시 중단  
  
- 프로그램에 포함 된 스레드를 다시 시작 합니다.  
  
> [!NOTE]
> 호출 스택 보기는 스레드 수준에서 구현 됩니다. 스레드에 대 한 호출 스택을 볼 때 프레임 정보를 열거 하려면 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스의 모든 메서드를 구현 해야 합니다.  
  
## <a name="methods-of-program-control"></a>Program 컨트롤의 메서드  
 다음 표에서는 최소 기능 디버그 엔진 (DE) 및 실행 제어를 위해 구현 해야 하는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 의 메서드를 보여 줍니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|프로그램에 포함 된 모든 스레드를 중지 된 상태로 계속 실행 합니다. 실행 제어에 필요 합니다.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|프로그램에 포함 된 모든 스레드를 중지 된 상태로 계속 실행 합니다. 실행 제어에 필요 합니다.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|지정 된 스레드에 대 한 단계를 수행 합니다. 프로그램에 포함 된 다른 모든 스레드를 계속 실행 합니다. 실행 제어에 필요 합니다.|  
  
 다중 스레드 프로그램의 경우 [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 메서드와 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) 인터페이스의 모든 메서드를 구현 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
