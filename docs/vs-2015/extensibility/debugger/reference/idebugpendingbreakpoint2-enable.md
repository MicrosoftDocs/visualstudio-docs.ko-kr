---
title: 'IDebugPendingBreakpoint2:: Enable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5dc3c1e37a817c1c962d05745db33422008c550
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194487"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

보류 중인 중단점의 활성화 상태를 전환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Enable(   
   BOOL fEnable  
);  
```  
  
```csharp  
int Enable(   
   int fEnable  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fEnable`  
 진행 보류 중인 중단점을 설정 하려면 0이 아닌 값으로 설정 하 `TRUE` 고, `FALSE` 사용 하지 않으려면 0 ()으로 설정 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 중단점이 삭제 되었으면를 반환 `E_BP_DELETED` 합니다.  
  
## <a name="remarks"></a>설명  
 보류 중인 중단점을 사용 하거나 사용 하지 않도록 설정 하면이 중단점에서 바인딩된 모든 중단점이 동일한 상태로 설정 됩니다.  
  
 이 메서드는 중단점을 이미 사용 하거나 사용 하지 않을 경우에도 필요에 따라 여러 번 호출할 수 있습니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 `CPendingBreakpoint` [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스를 노출 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.  
  
```cpp#  
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      // If the bound breakpoint member variable is valid, then enable or   
      // disable the bound breakpoint.    
      if (m_pBoundBP)    
      {    
         m_pBoundBP->Enable(fEnable);    
      }    
      // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure   
      // to enabled or disabled depending on the passed BOOL condition.    
      m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;    
      hr = S_OK;    
  
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>관련 항목  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
