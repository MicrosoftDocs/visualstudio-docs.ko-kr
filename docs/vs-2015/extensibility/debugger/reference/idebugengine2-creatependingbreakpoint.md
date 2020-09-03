---
title: 'IDebugEngine2:: CreatePendingBreakpoint | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84c36d08c7ad907006eb9f41d2f6e2c9cd77e7bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196040"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)에서 보류 중인 중단점을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pBPRequest`  
 진행 만들 보류 중단점을 설명 하는 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 개체입니다.  
  
 `ppPendingBP`  
 제한이 보류 중인 중단점을 나타내는 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 매개 변수가 `E_FAIL` `pBPRequest` 잘못 되었거나 불완전 한 경우는 일반적으로 매개 변수가 de-de에서 지 원하는 언어와 일치 하지 않는 경우를 반환 합니다 `pBPRequest` .  
  
## <a name="remarks"></a>설명  
 보류 중인 중단점은 기본적으로 중단점을 코드에 바인딩하는 데 필요한 모든 정보를 수집 하는 것입니다. 이 메서드에서 반환 된 보류 중인 중단점은 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 메서드가 호출 될 때까지 코드에 바인딩되지 않습니다.  
  
 사용자가 설정 하는 보류 중인 각 중단점에 대해 세션 디버그 관리자 (SDM)는 연결 된 각 DE-DE에서이 메서드를 호출 합니다. 중단점이 해당 DE에서 실행 되는 프로그램에 대해 유효한 지 확인 합니다.  
  
 사용자가 코드 줄에 중단점을 설정 하면 DE를 사용 하 여이 코드에 해당 하는 문서의 가장 가까운 줄에 중단점을 바인딩할 수 있습니다. 이렇게 하면 사용자가 여러 줄 문의 첫 번째 줄에 중단점을 설정 하 고 마지막 줄에 바인딩할 수 있습니다 (모든 코드가 디버그 정보에서 특성을 사용 하는 경우).  
  
## <a name="example"></a>예  
 다음 예제에서는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다 `CProgram` . 그러면의 DE 구현이 `IDebugEngine2::CreatePendingBreakpoint` 각 프로그램에서이 메서드 구현에 대 한 모든 호출을 전달할 수 있습니다.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [바인딩하며](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
