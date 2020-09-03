---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccbe76d800be035bc39caa477955b91bf21c074e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195682"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)에서 프로그램을 시작 하 고 종료 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 사용자 지정 포트로 완전히 처리할 수 없는 프로세스를 시작 하기 위한 특별 한 요구 사항이 있는 경우 사용자 지정 DE에 의해 구현 됩니다. 이는 일반적으로 DE가 인터프리터의 일부이 고 디버깅 중인 프로세스가 스크립트인 경우입니다. 인터프리터를 먼저 실행 한 다음 스크립트를 로드 하 고 시작 해야 합니다. 포트에서 인터프리터를 시작할 수 있지만 스크립트에 특별 한 처리가 필요할 수 있습니다 (여기서 DE에 역할이 있는 경우). 이 인터페이스는 사용자 지정 포트에서 처리할 수 없는 프로그램을 시작 하기 위한 고유한 요구 사항이 있는 경우에만 구현 됩니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 SDM이 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스에서이 인터페이스를 가져올 수 있는 경우 (세션 디버그 관리자)에 의해 호출 됩니다 (QueryInterface 사용). 이 인터페이스를 얻을 수 있는 경우 SDM은 DE에 특별 한 요구 사항이 있음을 알고 있으며이 인터페이스를 호출 하 여 포트를 시작 하는 대신 프로그램을 시작 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugEngineLaunch2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|DE를 사용 하 여 프로세스를 시작 합니다.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|프로세스 실행을 다시 시작 합니다.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|프로세스를 종료할 수 있는지 여부를 확인 합니다.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|프로세스를 종료 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
