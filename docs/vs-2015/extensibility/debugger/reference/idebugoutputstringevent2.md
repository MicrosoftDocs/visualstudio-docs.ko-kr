---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 844d93a6752538c6b7239b6c10688fdfbd98b401
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695186"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 문자열을 출력 하기 위해 디버그 엔진 (DE)에서 세션 디버그 관리자 (SDM)로 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE는이 인터페이스를 구현 하 여 IDE의 **출력** 창에 문자열을 보냅니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 DE는 **출력** 창에 문자열을 보내기 위해이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugOutputStringEvent2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|표시할 메시지를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 예를 들어 비관리 코드에서 디버그할 프로그램에서 Win32 함수에 문자열을 보내는 경우 출력할 문자열이 발생할 수 있습니다 `OutputDebugString` . 이 문자열은 DE에서 가로채서 이벤트로 SDM에 전송 됩니다 `IDebugOutputStringEvent2` .  
  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) 를 사용 하 여 사용자 응답이 필요한 메시지를 보냅니다.  
  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 를 사용 하 여 응답이 필요 하지 않은 오류 메시지를 보냅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
