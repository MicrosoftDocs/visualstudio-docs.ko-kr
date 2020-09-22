---
title: 시작 후 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843324"
---
# <a name="attaching-after-a-launch"></a>시작 후 연결
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그램이 시작 된 후 디버그 세션은 디버그 엔진 (DE)을 프로그램에 연결할 준비가 된 것입니다.  
  
## <a name="design-decisions"></a>디자인 결정  
 공유 주소 공간 내에서의 통신은 더 쉽기 때문에 디버그 세션과 DE-DE 간의 통신을 용이 하 게 하는 것이 더 적합 한지 아니면 DE-DE와 프로그램 간에 통신 하는 데 더 적합 한지를 결정 해야 합니다. 다음 중에서 선택 합니다.  
  
- 디버그 세션과 DE 간의 통신을 용이 하 게 하는 것이 더 적합 한 경우 디버그 세션은 DE를 다시 만들고 프로그램에 연결 하도록 DE를 요청 합니다. 이렇게 하면 디버그 세션 및 DE-DE가 하나의 주소 공간으로 유지 되 고 런타임 환경과 프로그램은 함께 유지 됩니다.  
  
- DE와 프로그램 간의 통신을 용이 하 게 하는 데 더 적합 한 경우 런타임 환경에서 DE를 공동 만듭니다. 이렇게 하면 SDM이 하나의 주소 공간으로 유지 되 고, DE, 런타임 환경 및 프로그램은 서로 함께 유지 됩니다. 이것은 스크립트 언어를 실행 하기 위해 인터프리터를 사용 하 여 구현 되는 일반적인 DE입니다.  
  
    > [!NOTE]
    > 프로그램에 대 한 연결 해제는 구현에 따라 다릅니다. DE와 프로그램 간의 통신도 구현에 따라 달라 집니다.  
  
## <a name="implementation"></a>구현  
 프로그래밍 방식으로 실행 될 프로그램을 나타내는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 개체를 먼저 수신 하는 경우에는 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) 메서드를 호출 하 여 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 개체를 전달 합니다 .이 개체는 나중에 디버그 이벤트를 다시 SDM에 전달 하는 데 사용 됩니다. `IDebugProgram2::Attach`그런 다음 메서드는 [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출 합니다. SDM에서 인터페이스를 수신 하는 방법에 대 한 자세한 내용은 `IDebugProgram2` [포트에 알림](../../extensibility/debugger/notifying-the-port.md)을 참조 하세요.  
  
 디버그 중인 프로그램과 동일한 주소 공간에서 DE를 실행 해야 하는 경우 일반적으로 DE가 스크립트를 실행 하는 인터프리터의 일부 이기 때문에 메서드는 `IDebugProgramNodeAttach2::OnAttach` 을 반환 하 여 `S_FALSE` 연결 프로세스를 완료 했음을 나타냅니다.  
  
 반면에 DE가 SDM의 주소 공간에서 실행 되는 경우이 메서드는를 `IDebugProgramNodeAttach2::OnAttach` 반환 `S_OK` 하거나 디버깅 중인 프로그램에 연결 된 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 개체에 대해 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스가 구현 되지 않습니다. 이 경우 [attach 메서드를 호출 하 여 연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 작업을 완료 합니다.  
  
 후자의 경우에는 메서드에 전달 된 개체에서 [get프로그래밍할 id](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 호출 하 고 `IDebugProgram2` `IDebugEngine2::Attach` , `GUID` 로컬 프로그램 개체에를 저장 하 고, `GUID` `IDebugProgram2::GetProgramId` 이 개체에 대해 메서드가 호출 될 때이를 반환 해야 합니다. 는 `GUID` 다양 한 디버그 구성 요소에서 프로그램을 고유 하 게 식별 하는 데 사용 됩니다.  
  
 메서드가를 반환 하는 경우 `IDebugProgramNodeAttach2::OnAttach` `S_FALSE` `GUID` 프로그램에 사용할는 해당 메서드로 전달 되 고 `IDebugProgramNodeAttach2::OnAttach` `GUID` 로컬 프로그램 개체에 대해를 설정 하는 메서드입니다.  
  
 이제 DE가 프로그램에 연결 되 고 시작 이벤트를 보낼 준비가 되었습니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로그램에 직접 연결](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [포트에 알림](../../extensibility/debugger/notifying-the-port.md)   
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [첨부](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Get프로그래밍 Id](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md)
