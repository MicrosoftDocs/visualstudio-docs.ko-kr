---
title: 'IDebugBoundBreakpoint2:: SetCondition | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ac19bfe2109d7885265342ccc5ef4d358727d49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156201"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 바인딩된 중단점과 연결 된 조건을 설정 하거나 변경 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `bpCondition`  
 진행 조건을 설명 하는 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 열거형의 값입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_BP_DELETED`바인딩된 중단점 개체의 상태가 `BPS_DELETED` ( [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 열거의 일부)로 설정 되어 있으면를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이전에이 중단점과 연결 된 모든 조건이 손실 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
