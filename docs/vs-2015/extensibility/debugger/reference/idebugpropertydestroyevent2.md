---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 034040ecd8df3368f53cb7a3bf99197e962e2b56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702298"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 특정 문서와 연결 된 속성이 소멸 되려고 할 때 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE는 속성이 소멸 되었음을 보고 하기 위해이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다. 이 인터페이스는 DE-DE가 스크립트와 연결 된 속성을 이전에 만든 경우에 구현 됩니다. 속성을 삭제 하면 IDE에서 연결 된 스크립트가 제거 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 DE는이 이벤트 개체를 만들어 속성이 소멸 되었다는 것을 보고 합니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPropertyDestroyEvent2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|제거할 속성을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이러한 이벤트가 사용 되는 이유에 대 한 자세한 내용은 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) 에 대 한 설명을 참조 하십시오.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
