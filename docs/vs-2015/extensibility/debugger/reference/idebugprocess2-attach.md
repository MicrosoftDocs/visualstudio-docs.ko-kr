---
title: 'IDebugProcess2:: Attach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4664f164675c445510d8976f33577684dbd1d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188104"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로세스에 SDM (세션 디버그 관리자)을 연결 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pCallback`  
 진행 디버그 이벤트 알림에 사용 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.  
  
 `rgguidSpecificEngines`  
 진행 프로세스에서 실행 되는 프로그램을 디버깅 하는 데 사용 되는 디버그 엔진의 Guid 배열입니다. 이 매개 변수는 null 값일 수 있습니다. 자세한 내용은 설명 부분을 참조 하십시오.  
  
 `celtSpecificEngines`  
 진행 배열의 디버그 엔진 수 `rgguidSpecificEngines` 와 배열의 크기입니다 `rghrEngineAttach` .  
  
 `rghrEngineAttach`  
 [in, out] 디버그 엔진에서 반환 하는 HRESULT 코드의 배열입니다. 이 배열의 크기는 `celtSpecificEngines` 매개 변수에 지정 됩니다. 각 코드는 일반적으로 `S_OK` 또는 `S_ATTACH_DEFERRED` 입니다. 후자는 현재 DE-DE가 프로그램에 연결 되어 있지 않음을 나타냅니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음 표에서는 다른 가능한 값을 보여 줍니다.  
  
|값|설명|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|지정 된 프로세스가 이미 디버거에 연결 되어 있습니다.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|연결 절차를 수행 하는 동안 보안 위반이 발생 했습니다.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|데스크톱 프로세스를 디버거에 연결할 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 프로세스에 연결 하면 해당 프로세스에서 실행 되는 모든 프로그램에 SDM이 연결 되어 배열에 지정 된 디버그 엔진 (DE)으로 디버그할 수 있습니다 `rgguidSpecificEngines` . `rgguidSpecificEngines`매개 변수를 null 값으로 설정 하거나 `GUID_NULL` 배열에를 포함 하 여 프로세스의 모든 프로그램에 연결 합니다.  
  
 프로세스에서 발생 하는 모든 디버그 이벤트는 지정 된 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체에 전송 됩니다. 이 `IDebugEventCallback2` 개체는 SDM에서이 메서드를 호출할 때 제공 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
