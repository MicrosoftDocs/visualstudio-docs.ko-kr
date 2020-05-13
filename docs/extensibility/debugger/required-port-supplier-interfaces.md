---
title: 필수 포트 공급업체 인터페이스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713160"
---
# <a name="required-port-supplier-interfaces"></a>필수 포트 공급업체 인터페이스
포트 공급자는 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스를 구현해야 합니다. [아이디버그포트Supplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 포트 공급자는 포트를 공급하고 구현합니다. 따라서 다음 인터페이스를 실행 해야 합니다.

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  포트에 대해 설명하고 포트에서 실행되는 모든 프로세스를 연보합니다.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  포트에서 프로세스를 시작하고 종료할 수 있습니다.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  이 포트의 컨텍스트 내에서 실행 중인 프로그램에 대 한 메커니즘을 제공 합니다 프로그램 노드 생성 및 소멸을 알리는. 자세한 내용은 [프로그램 노드 를 참조하십시오.](../../extensibility/debugger/program-nodes.md)

- `IConnectionPointContainer`

  [IDebugPortEvents2에](../../extensibility/debugger/reference/idebugportevents2.md)대한 연결 지점을 제공합니다.

## <a name="port-supplier-operation"></a>포트 공급업체 운영
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) 싱크는 포트에서 프로세스 및 프로그램을 만들고 소멸할 때 알림을 받습니다. 포트는 프로세스가 생성될 때 [IDebugProcessCreateEvent2를](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) 보내고 포트에서 프로세스가 소멸될 때 [IDebugProcessDestroyEvent2를](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) 보내야 합니다. 또한 포트는 프로그램이 생성될 때 [IDebugProgramCreateEvent2를](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 보내고 포트에서 실행되는 프로세스에서 프로그램이 소멸될 때 [IDebugProgramDestroyEvent2를](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 보내야 합니다.

 포트는 일반적으로 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 및 [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 메서드에 대한 응답으로 이벤트를 만들고 삭제하는 프로그램을 각각 보냅니다.

 포트는 물리적 프로세스와 논리 프로그램을 모두 시작하고 종료할 수 있으므로 디버그 엔진에서도 다음 인터페이스를 구현해야 합니다.

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  물리적 프로세스에 대해 설명합니다. 최소한 다음 메서드를 구현해야 합니다.

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  SDM이 프로세스에서 자체적으로 연결하고 분리할 수 있는 방법을 제공합니다.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  논리 프로그램을 설명합니다. 최소한 다음 메서드를 구현해야 합니다.

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  SDM이 이 프로그램에 연결할 수 있는 방법을 제공합니다.

## <a name="see-also"></a>참조
- [포트 공급업체 구현](../../extensibility/debugger/implementing-a-port-supplier.md)
