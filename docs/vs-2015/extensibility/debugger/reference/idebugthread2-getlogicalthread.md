---
title: 'IDebugThread2:: GetLogicalThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f430ea7ba69ca55bc76543d853396e22b193cf02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153061"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진은이 메서드를 구현 하지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStackFrame`  
 진행 스택 프레임을 나타내는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 개체입니다.  
  
 `ppLogicalThread`  
 제한이 연결 된 `IDebugLogicalThread2` 논리 스레드를 나타내는 인터페이스를 반환 합니다. 디버그 엔진 구현에서는이 값을 null 값으로 설정 해야 합니다.  
  
## <a name="return-value"></a>반환 값  
 디버그 엔진 구현은 항상 `E_NOTIMPL` 를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
