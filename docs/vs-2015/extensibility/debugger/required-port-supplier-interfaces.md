---
title: 필요한 포트 공급자 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a065389a6b9b67b8bce82394569ce65afb0f8d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821429"
---
# <a name="required-port-supplier-interfaces"></a>필요한 포트 공급자 인터페이스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

포트 공급자는 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스를 구현 해야 합니다. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 포트 공급자는 포트를 제공 하기 때문에 포트도 구현 해야 합니다. 따라서 다음 인터페이스를 구현 해야 합니다.  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     포트에 대해 설명 하 고 포트에서 실행 중인 모든 프로세스를 열거할 수 있습니다.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     는 포트에서 프로세스를 시작 및 종료 하는 기능을 제공 합니다.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     이 포트의 컨텍스트 내에서 실행 되는 프로그램에 대 한 메커니즘을 제공 하 여 프로그램 노드 만들기 및 소멸을 알립니다. 자세한 내용은 [Program Nodes](../../extensibility/debugger/program-nodes.md)을 (를) 참조 하세요.  
  
- `IConnectionPointContainer`  
  
     [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)에 대 한 연결 지점을 제공 합니다.  
  
## <a name="port-supplier-operation"></a>포트 공급자 작업  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) 싱크는 프로세스 및 프로그램이 포트에서 만들어지고 제거 될 때 알림을 받습니다. 프로세스가 생성 될 때 [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) [를 전송 하 고 포트](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) 에서 프로세스가 소멸 될 때 포트가 필요 합니다. 포트는 프로그램이 생성 될 때 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 를 전송 하 고 포트에서 실행 중인 프로세스에서 프로그램이 소멸 될 때 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 도 필요 합니다.  
  
 일반적으로 포트는 [addprogram 노드와](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 메서드에 대 한 응답으로 프로그램 만들기 및 삭제 이벤트를 각각 보냅니다.  
  
 포트는 물리적 프로세스와 논리적 프로그램을 모두 시작 하 고 종료할 수 있으므로 디버그 엔진 에서도 이러한 인터페이스를 구현 해야 합니다.  
  
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
  실제 프로세스에 대해 설명 합니다. 적어도 다음 메서드를 구현 해야 합니다.  

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
    SDM이 프로세스에서 자신을 연결 하 고 분리 하는 방법을 제공 합니다.  
  
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
  논리적 프로그램에 대해 설명 합니다. 적어도 다음 메서드를 구현 해야 합니다.  

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     SDM이이 프로그램에 연결 하는 방법을 제공 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [포트 공급자 구현](../../extensibility/debugger/implementing-a-port-supplier.md)
