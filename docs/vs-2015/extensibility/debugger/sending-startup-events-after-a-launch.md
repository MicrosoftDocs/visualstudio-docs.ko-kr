---
title: 시작 후 시작 이벤트 보내기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841739"
---
# <a name="sending-startup-events-after-a-launch"></a>시작 후 시작 이벤트 보내기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 (DE)이 프로그램에 연결 되 면 일련의 시작 이벤트를 다시 디버그 세션으로 보냅니다.  
  
 디버그 세션으로 다시 전송 되는 시작 이벤트는 다음과 같습니다.  
  
- 엔진 생성 이벤트입니다.  
  
- 프로그램 생성 이벤트입니다.  
  
- 스레드 만들기 및 모듈 로드 이벤트  
  
- 코드를 로드 하 고 실행할 준비가 되 면 코드가 실행 되기 전에 전송 되는 로드 완료 이벤트입니다.  
  
  > [!NOTE]
  > 이 이벤트가 계속 되 면 전역 변수가 초기화 되 고 시작 루틴이 실행 됩니다.  
  
- 다른 스레드 만들기 및 모듈 로드 이벤트를 사용할 수 있습니다.  
  
- 진입점 이벤트는 프로그램의 기본 진입점 (예: **main** 또는)에 도달 했음을 신호로 보냅니다 `WinMain` . 이 이벤트는 일반적으로 DE가 이미 실행 중인 프로그램에 연결 된 경우 전송 되지 않습니다.  
  
  프로그래밍 방식으로 DE는 먼저 엔진 생성 이벤트를 나타내는 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 인터페이스와 프로그램 생성 이벤트를 나타내는 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)을 차례로 전송 합니다.  
  
  이는 일반적으로 하나 이상의 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 스레드 만들기 이벤트와 [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 모듈 로드 이벤트가 차례로 발생 합니다.  
  
  코드를 로드 하 고 실행할 준비가 완료 된 후 코드를 실행 하기 전에 DE는 SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) load complete 이벤트를 보냅니다. 마지막으로 프로그램이 아직 실행 되 고 있지 않은 경우 DE는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 진입점 이벤트를 전송 합니다 .이 이벤트는 프로그램의 기본 진입점에 도달 하 여 디버그할 준비가 되었음을 신호로 보냅니다.  
  
## <a name="see-also"></a>참고 항목  
 [실행 제어](../../extensibility/debugger/control-of-execution.md)   
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
