---
title: 'IDebugThread2:: Resume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152986"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

스레드의 실행을 다시 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdwSuspendCount`  
 제한이 다시 시작 작업 후 일시 중단 횟수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드에 대 한 각 호출은 0에 도달할 때까지 일시 중단 횟수를 감소 시킵니다. 이때 실행은 실제로 다시 시작 됩니다. 이 일시 중단 횟수는 **스레드** 디버그 창에 표시 됩니다.  
  
 이 메서드에 대 한 각 호출에는 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) 메서드를 이전에 호출 해야 합니다. 일시 중단 횟수는 `IDebugThread2::Suspend` 지금까지 메서드가 호출 된 횟수를 결정 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [일시 중지됨](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
