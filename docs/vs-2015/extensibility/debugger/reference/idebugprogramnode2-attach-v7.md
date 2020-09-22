---
title: 'IDebugProgramNode2:: Attach_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08028f2b03f3ea36cc72172ca8f9de31740b49f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841434"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Mapi. 사용 하지 마십시오.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pMDMProgram`  
 진행 연결할 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스입니다.  
  
 `pCallback`  
 진행 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스를 사용 하 여 디버그 이벤트를 SDM으로 보냅니다.  
  
 `dwReason`  
 진행 연결 이유를 지정 하는 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 열거형의 값입니다.  
  
## <a name="return-value"></a>반환 값  
 구현은 항상를 반환 해야 `E_NOTIMPL` 합니다.  
  
## <a name="remarks"></a>설명  
  
> [!WARNING]
> [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]에서이 메서드는 더 이상 사용 되지 않으며 항상를 반환 해야 `E_NOTIMPL` 합니다. 프로그램 노드에 연결할 수 없거나 프로그램 노드가 단순히 프로그램을 설정 하는 경우에는 다른 방법으로 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스를 참조 하세요 `GUID` . 그렇지 않으면 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 구현 합니다.  
  
## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005 이전  
 이 메서드는 디버그 중인 프로그램의 주소 공간에서 DE를 실행 하는 경우에만 구현 해야 합니다. 그렇지 않으면이 메서드는를 반환 해야 `S_FALSE` 합니다.  
  
 이 메서드가 호출 되 면 DE는이 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스 인스턴스와 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 및 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 이벤트 개체를 아직 보내지 않은 경우 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) 이벤트 개체를 전송 해야 합니다. 그런 다음 매개 변수가 인 경우 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 이벤트 개체가 전송 됩니다 `dwReason` `ATTACH_REASON_LAUNCH` .  
  
 DE는 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트 개체에서 제공 하는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체의 [get프로그래밍할 id](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 호출 해야 하며, de에서 구현 된 개체의 인스턴스 데이터에 해당 프로그램의 GUID를 저장 해야 합니다 `IDebugProgram2` .  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [첨부](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
