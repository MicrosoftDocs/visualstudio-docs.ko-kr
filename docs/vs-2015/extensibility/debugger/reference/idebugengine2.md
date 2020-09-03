---
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c011a530bbd4323546257a40334a4b8a0f57bdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195906"
---
# <a name="idebugengine2"></a>IDebugEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 디버그 엔진 (DE)을 나타냅니다. 이 클래스는 중단점을 만들어 예외를 설정 및 해제 하는 방법에서 디버깅 세션의 다양 한 측면을 관리 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 프로그램의 디버깅을 관리 하기 위해 사용자 지정 DE에 의해 구현 됩니다. 이 인터페이스는 DE에 의해 구현 되어야 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 예외 관리, 중단점 만들기 및 DE-DE에서 보낸 동기 이벤트에 대 한 응답을 포함 하 여 디버깅 세션을 관리 하기 위해 SDM (세션 디버그 관리자)에 의해 호출 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugEngine2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|DE에 의해 디버깅 되는 모든 프로그램에 대 한 열거자를 만듭니다.|  
|[연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)|프로그램에 DE를 연결 합니다.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE에서 보류 중인 중단점을 만듭니다.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|DE가 지정 된 예외를 처리 하는 방법을 지정 합니다.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|지정 된 예외를 제거 하 여 디버그 엔진에서 더 이상 처리 하지 않도록 합니다.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|특정 런타임 아키텍처 또는 언어에 대해 IDE에서 설정한 예외 목록을 제거 합니다.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|DE의 GUID를 가져옵니다.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|지정 된 프로그램이 atypically 종료 되었으며 DE가 프로그램에 대 한 모든 참조를 정리 하 고 프로그램 제거 이벤트를 보내야 함을 DE에 알립니다.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|이전에 DE에서 SDM에 보낸 동기 디버그 이벤트가 수신 및 처리 되었음을 나타내기 위해 SDM에 의해 호출 됩니다.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|DE의 로캘을 설정 합니다.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|DE에서 현재 사용 중인 레지스트리 루트를 설정 합니다.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|메트릭을 설정 합니다.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|다음에 스레드 중 하나를 실행 하려고 할 때이 DE에서 디버깅 중인 모든 프로그램의 실행이 중지 되도록 요청 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
