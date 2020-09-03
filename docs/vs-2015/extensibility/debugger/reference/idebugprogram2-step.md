---
title: 'IDebugProgram2:: Step | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd9d314865eb2051b67d7c127a6c5cc2395b1863
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387228"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

단계를 수행 합니다.  
  
> [!NOTE]
> 이 메서드는 더 이상 사용되지 않습니다. 대신 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) 메서드를 사용 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pThread`  
 진행 단계별 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.  
  
 `sk`  
 진행 단계 종류를 지정 하는 [stkind](../../../extensibility/debugger/reference/stepkind.md) 열거형의 값입니다.  
  
 `step`  
 진행 단계 단위 (예: 문 또는 명령)를 지정 하는 [stunit](../../../extensibility/debugger/reference/stepunit.md) 열거형의 값입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 스레드 동기화 또는 스레드 간 통신이 있는 경우 특정 스레드가 단계별로 실행 될 때 프로그램의 다른 스레드를 실행 해야 합니다.  
  
> [!WARNING]
> 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
