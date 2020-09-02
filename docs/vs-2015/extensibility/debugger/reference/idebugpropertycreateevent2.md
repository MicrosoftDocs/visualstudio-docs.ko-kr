---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1558aa8ca9cad93b00cf90f02f3af6d346b036b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698658"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 특정 문서와 연결 된 속성을 만들 때 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE는이 인터페이스를 구현 하 여 속성이 생성 되었음을 보고 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다. 이 인터페이스는 DE-DE가 로드 되거나 만들어진 스크립트와 연결 된 속성을 만든 경우와 해당 스크립트가 IDE에 표시 되어야 하는 경우에 구현 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 DE는이 이벤트 개체를 만들어 속성을 만들었음을 보고 합니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는 인터페이스의 메서드를 보여 줍니다 `IDebugPropertyCreateEvent2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|새 속성을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 속성에 관련 된 문서 또는 스크립트가 있는 경우 DE는 문서 이름을 사용 하 여 **스크립트 문서** 창을 업데이트 하기 위해이 이벤트를 SDM으로 보낼 수 있습니다. SDM은 인수를 사용 하 여 [Getextendedinfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) 를 호출 `guidDocument` 하 여 `VARIANT` [IUnknown](https://msdn.microsoft.com/library/e6b85472-e54b-4b8c-b19f-4454d6c05a8f) 포인터를 포함 하는을 검색 합니다. SDM은이 포인터에서 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 호출 하 여 **스크립트 문서** 창을 업데이트 하는 데 사용 되는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 검색 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
