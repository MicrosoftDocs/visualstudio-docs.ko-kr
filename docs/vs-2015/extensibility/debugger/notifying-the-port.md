---
title: 포트에 알림 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cf3969dda783882f24d02a748f345cdb66fe413
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842159"
---
# <a name="notifying-the-port"></a>포트에 알림
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그램을 시작한 후 다음과 같이 포트에 알림이 표시 되어야 합니다.  
  
1. 포트가 새 프로그램 노드를 수신 하면 프로그램 생성 이벤트를 디버그 세션으로 다시 보냅니다. 이벤트는 프로그램을 나타내는 인터페이스와 함께 전달 됩니다.  
  
2. 디버그 세션은 프로그램에서에 연결할 수 있는 디버그 엔진 (DE)의 식별자를 쿼리 합니다.  
  
3. 디버그 세션은 해당 프로그램에 대해 허용 되는 DEs 목록에 DE가 있는지 확인 합니다. 디버그 세션은 솔루션의 활성 프로그램 설정에서이 목록을 가져와 원래 디버그 패키지에 의해 전달 됩니다.  
  
    DE는 허용 목록에 있어야 합니다. 그렇지 않으면 DE는 프로그램에 연결 되지 않습니다.  
  
   프로그래밍 방식으로 포트는 새 프로그램 노드를 받을 때 프로그램을 나타내는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 만듭니다.  
  
> [!NOTE]
> 이는 `IDebugProgram2` 나중에 디버그 엔진 (DE)에서 만든 인터페이스와 혼동 해서는 안 됩니다.  
  
 이 포트는 COM 인터페이스를 통해 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 프로그램 생성 이벤트를 다시 SDM (세션 디버그 관리자)로 보냅니다 `IConnectionPoint` .  
  
> [!NOTE]
> 이 `IDebugProgramCreateEvent2` 인터페이스는 나중에 DE에서 전송 하는 인터페이스와 혼동 해서는 안 됩니다.  
  
 포트는 이벤트 인터페이스 자체와 함께 포트, 프로세스 및 프로그램을 각각 나타내는 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)및 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 보냅니다. SDM은 [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) 를 호출 하 여 프로그램을 디버그할 수 있는 DE의 GUID를 가져옵니다. GUID는 원래 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스에서 가져왔습니다.  
  
 SDM이 허용 되는 DEs 목록에 있는지 확인 합니다. SDM은 원래 디버그 패키지에 의해 전달 된 솔루션의 활성 프로그램 설정에서이 목록을 가져옵니다. DE는 허용 목록에 있어야 합니다. 그렇지 않으면 프로그램에 연결 되지 않습니다.  
  
 DE의 id를 알고 있으면 SDM에서 프로그램에 연결할 준비가 된 것입니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로그램 시작](../../extensibility/debugger/launching-a-program.md)   
 [시작 후 연결](../../extensibility/debugger/attaching-after-a-launch.md)   
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
