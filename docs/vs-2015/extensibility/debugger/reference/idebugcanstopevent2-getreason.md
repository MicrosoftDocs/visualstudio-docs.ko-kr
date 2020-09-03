---
title: 'IDebugCanStopEvent2:: GetReason | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191146"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)을 중지 하려는 이유를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcr`  
 제한이 이 이벤트의 이유를 설명 하는 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 열거형의 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 일반적으로 [Canstop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 메서드 이전에 호출 되므로 호출자가 0이 아닌 ()을 메서드에 전달할지 여부를 결정할 수 있습니다 `TRUE` `IDebugCanStopEvent2::CanStop` .  
  
 를 중지 하는 이유는이 될 수 있습니다 `CANSTOP_ENTRYPOINT` . 즉, de가 진입점에 도달 했거나 함수를 단계별로 실행할 수 있음을 의미 합니다 `CANSTOP_STEPIN` .  
  
## <a name="see-also"></a>관련 항목  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
