---
title: 'IDebugProgram2:: Continue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 461aa702350e1385e01df6f78e942bbe73b16402
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386201"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중지 된 상태에서이 프로그램을 계속 실행 합니다. 모든 이전 실행 상태 (예: 단계)는 유지 되 고 프로그램의 실행이 다시 시작 됩니다.  
  
> [!NOTE]
> 이 메서드는 더 이상 사용되지 않습니다. 대신 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드를 사용 해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pThread`  
 진행 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 디버깅 중인 프로그램 수 또는 중지 이벤트를 생성 한 프로그램에 관계 없이이 프로그램에서 호출 됩니다. 구현은 이전 실행 상태 (예: 단계)를 유지 하 고 이전 실행을 완료 하기 전에 중지 된 적이 없는 경우에도 계속 실행 해야 합니다. 즉,이 프로그램의 스레드가 단계별 작업을 수행 하 고 일부 다른 프로그램이 중지 되어 중지 된 경우이 메서드가 호출 되 면 프로그램에서 원래 단계별 작업을 완료 해야 합니다.  
  
> [!WARNING]
> 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
