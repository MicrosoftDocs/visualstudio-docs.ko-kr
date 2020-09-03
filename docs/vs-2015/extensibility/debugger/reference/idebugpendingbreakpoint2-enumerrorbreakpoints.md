---
title: 'IDebugPendingBreakpoint2:: EnumErrorBreakpoints | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints
helpviewer_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints method
- EnumErrorBreakpoints method
ms.assetid: 2f9a9720-c1ac-4430-8f28-200d85360452
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f9cac8b19e6281b8993e84d13ae60138ddaeac89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201078"
---
# <a name="idebugpendingbreakpoint2enumerrorbreakpoints"></a>IDebugPendingBreakpoint2::EnumErrorBreakpoints
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 보류 중인 중단점에서 발생 한 모든 오류 중단점의 목록을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumErrorBreakpoints(   
   BP_ERROR_TYPE                 bpErrorType,  
   IEnumDebugErrorBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumErrorBreakpoints(   
   enum_BP_ERROR_TYPE              bpErrorType,  
   out IEnumDebugErrorBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `bpErrorType`  
 진행 열거할 오류 유형을 선택 하는 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) 열거형 값의 조합입니다.  
  
 `ppEnum`  
 제한이 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 개체의 목록을 포함 하는 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 중단점이 삭제 되었으면를 반환 `E_BP_DELETED` 합니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 `CPendingBreakpoint` [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스를 노출 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.  
  
```cpp#  
HRESULT CPendingBreakpoint::EnumErrorBreakpoints(  
   BP_ERROR_TYPE bpErrorType,  
   IEnumDebugErrorBreakpoints2** ppEnum)    
{    
   HRESULT hr;    
  
   // Verify that the passed IEnumDebugErrorBreakpoints2 interface pointer   
   // is valid.    
   if (ppEnum)    
   {    
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // Verify that this error is not a warning.    
         // All errors supported by this DE are errors, not warnings.    
         if (IsFlagSet(bpErrorType, BPET_TYPE_ERROR) && m_pErrorBP)    
         {    
            // Get the error breakpoint.    
            CComPtr<IDebugErrorBreakpoint2> spErrorBP;    
            hr = m_pErrorBP->QueryInterface(&spErrorBP);    
            assert(hr == S_OK);    
            if (hr == S_OK)    
            {    
               // Create the error breakpoint enumerator.    
               CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;    
               hr = CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum);    
               assert(hr == S_OK);    
               if (hr == S_OK)    
               {    
                  // Initialize the enumerator of error breakpoints with   
                  // the IDebugErrorBreakpoint2 information.      
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };    
                  hr = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);    
                  if (hr == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugErrorBreakpoints2     
                     // interface can be queried by the created   
                     // CEnumDebugErrorBreakpoints object.    
                     hr = pErrorEnum->QueryInterface(ppEnum);    
                     assert(hr == S_OK);    
                  }    
  
                  // Otherwise, delete the CEnumDebugErrorBreakpoints   
                  // object.    
                  if (FAILED(hr))    
                  {    
                     delete pErrorEnum;    
                  }    
               }    
            }    
         }    
         else    
         {    
            hr = S_FALSE;    
         }    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>관련 항목  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
