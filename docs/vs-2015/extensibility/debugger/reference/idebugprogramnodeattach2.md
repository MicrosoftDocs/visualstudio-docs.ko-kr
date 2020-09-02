---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 580d4d2432a957bae8c590b3590a11b1a0b5e84e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148522"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로그램 노드에 연결 된 프로그램에 대 한 연결 시도를 알릴 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 연결 작업에 대 한 알림을 수신 하 고 연결 작업을 취소할 수 있는 기회를 제공 하기 위해 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스를 구현 하는 동일한 클래스에서 구현 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 `QueryInterface` [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체에서 메서드를 호출 하 여이 인터페이스를 가져옵니다. [연결 메서드를](../../../extensibility/debugger/reference/idebugengine2-attach.md) 호출 하기 전에 [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출 하 여 프로그램 노드에 연결 프로세스를 중지할 수 있는 기회를 제공 해야 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|연결 된 프로그램에 연결 하거나 [연결 방법에](../../../extensibility/debugger/reference/idebugengine2-attach.md) 대 한 연결 프로세스를 지연 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 사용 되지 않는 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) 메서드에 대 한 기본 설정 대안입니다. 모든 디버그 엔진은 항상 함수를 사용 하 여 로드 됩니다 `CoCreateInstance` . 즉, 디버깅 중인 프로그램의 주소 공간 외부에서 인스턴스화됩니다.  
  
 메서드의 이전 구현에서 `IDebugProgramNode2::Attach_V7` 디버깅 중인 프로그램의를 단순히 설정 하는 경우에는 `GUID` [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드만 구현 하면 됩니다.  
  
 이전 메서드 구현에서 제공 된 `IDebugProgramNode2::Attach_V7` 콜백 인터페이스를 사용한 경우에는 해당 기능을 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드 구현으로 이동 해야 하며 `IDebugProgramNodeAttach2` 인터페이스를 구현할 필요가 없습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [첨부](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
