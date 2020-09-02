---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4ac1f3a8d9b470fbb3734f822601a7dce08a44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696676"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 현재 코드 위치에서 중지할지 여부를 세션 디버그 관리자 (SDM)에 게 표시 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 소스 코드의 단계별 실행을 지원 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. 즉, SDM에서 인터페이스에 액세스 하는 데 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 합니다 `IDebugEvent2` .  
  
 이 인터페이스의 구현은 SDM의 [Canstop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 호출을 디버그 엔진에 전달 해야 합니다. 예를 들어 디버그 엔진의 메시지 처리 스레드에 게시 된 메시지를 사용 하 여이 작업을 수행 하거나,이 인터페이스를 구현 하는 개체에서 디버그 엔진에 대 한 참조를 보유 하 고 플래그가 전달 된 디버그 엔진에 콜백할 수 있습니다 `IDebugCanStopEvent2::CanStop` .  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 De는 실행을 계속 하 라는 메시지가 표시 되 고 DE가 코드를 단계별로 실행 하 게 될 때마다이 메서드를 보낼 수 있습니다. 이 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback 함수를 사용 하 여 보냅니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugCanStopEvent2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|이 이벤트의 이유를 가져옵니다.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|디버그할 프로그램을이 이벤트의 위치에서 중지할지, 아니면 중지 이유를 설명 하는 이벤트를 보낼지, 아니면 계속 실행할지를 지정 합니다.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|이 이벤트의 위치를 설명 하는 문서 컨텍스트를 가져옵니다.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|이 이벤트의 위치를 설명 하는 코드 컨텍스트를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 사용자가 함수를 단계별로 수행 하 고, 디버그 정보를 찾을 수 없거나 디버그 정보가 있는 경우 de가이 인터페이스를 보내고, 해당 위치에 대 한 소스 코드를 표시할 수 있는지 여부를 알 수 없습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
