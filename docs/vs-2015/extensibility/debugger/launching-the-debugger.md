---
title: 디버거 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e9c57079246dd52bd7fb44371999d0c3747dad40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149121"
---
# <a name="launching-the-debugger"></a>디버거 시작
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거를 시작 하려면 적절 한 특성과 함께 올바른 메서드 및 이벤트 시퀀스를 전송 해야 합니다.  
  
## <a name="sequences-of-methods-and-events"></a>메서드 및 이벤트 시퀀스  
  
1. **디버그** 메뉴를 선택 하 고 **시작**을 선택 하 여 세션 디버그 관리자 (SDM)를 호출 합니다. 자세한 내용은 [프로그램 시작을](../../extensibility/debugger/launching-a-program.md) 참조 하세요.  
  
2. SDM은 [Onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출 합니다.  
  
3. 디버그 엔진 (DE) 프로세스 모델을 기반으로 메서드는 다음 메서드 중 하나를 반환 하 여 다음에 발생 하는 `IDebugProgramNodeAttach2::OnAttach` 작업을 결정 합니다.  
  
     `S_FALSE`가 반환 되 면 디버그 엔진 (DE)이 가상 컴퓨터의 프로세스에 로드 됩니다.  
  
     또는  
  
     `S_OK`가 반환 되 면 DE는 SDM의 in-process로 로드 됩니다. 그러면 SDM에서 다음 작업을 수행 합니다.  
  
    1. [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 를 호출 하 여 DE의 엔진 정보를 가져옵니다.  
  
    2. DE를 공동 만듭니다.  
  
    3. [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)를 호출 합니다.  
  
4. DE는 특성을 사용 하 여 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC` .  
  
5. DE는 특성을 사용 하 여 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC` .  
  
6. DE는 특성을 사용 하 여 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC` .  
  
7. DE는 특성을 사용 하 여 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC` .  
  
8. DE는 특성을 사용 하 여 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 을 SDM으로 보냅니다 `EVENT_SYNC` .  
  
## <a name="see-also"></a>관련 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)   
 [프로그램 시작](../../extensibility/debugger/launching-a-program.md)
