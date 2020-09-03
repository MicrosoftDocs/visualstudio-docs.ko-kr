---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1188f18e4a6f604dfd82991433bc0ffe0a07ad47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148570"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 디버그할 수 있는 프로그램을 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE) 또는 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 디버그할 수 있는 프로그램을 나타냅니다. 이 인터페이스는 일반적으로 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 구현 하는 동일한 개체에서 구현 됩니다. 이 인터페이스는에 등록 됩니다 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] . [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Getprovider프로그래밍 노드](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 를 호출 하 여이 인터페이스를 반환 합니다. 사용자 지정 포트 공급자는 [Add프로그래밍 노드](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)호출을 통해이 인터페이스를 수신 합니다. DE는 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)호출을 통해이 인터페이스를 수신 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProgramNode2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|프로그램의 이름을 가져옵니다.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|프로그램을 호스트 하는 프로세스의 이름을 가져옵니다.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|프로그램을 호스트 하는 프로세스의 시스템 프로세스 식별자를 가져옵니다.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Mapi. 사용 하지 마십시오.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Mapi. 사용 하지 마십시오. 다른 방법은 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스를 참조 하세요.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|이 프로그램을 실행 하는 DE-DE의 이름과 식별자를 가져옵니다.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Mapi. 사용 하지 마십시오.|  
  
## <a name="remarks"></a>설명  
 일반적으로 세션 디버그 관리자 (SDM)는 [Getprovider프로그래밍 노드](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 를 호출 하 여이 인터페이스를 가져옵니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Add프로그래밍 노드](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [첨부](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Getprovider프로그래밍 노드](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
