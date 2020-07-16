---
title: 'IDebugProcess3:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f9b70deabd4cb7996d76373c6216057678c0bd3
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386175"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중지 된 상태에서이 프로세스를 계속 실행 합니다. 모든 이전 실행 상태 (예: 단계)는 지워지고 프로세스가 다시 실행 되기 시작 합니다.  
  
> [!NOTE]
> 이 메서드는 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)대신 사용 해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pThread`  
 진행 실행할 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 사용자가 다른 프로세스의 스레드에서 중지 된 상태에서 실행을 시작 하면이 프로세스에서이 메서드가 호출 됩니다. 이 메서드는 사용자가 IDE의 **디버그** 메뉴에서 **시작** 명령을 선택 하는 경우에도 호출 됩니다. 이 메서드의 구현은 프로세스의 현재 스레드에서 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드를 호출 하는 것 처럼 간단할 수 있습니다.  
  
> [!WARNING]
> 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [진행할](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
