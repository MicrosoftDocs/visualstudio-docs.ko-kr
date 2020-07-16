---
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5069a40f4e3ea4b1fba74c8133a18b46f2b3f2d2
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386227"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로세스에서 하나의 명령 또는 문을 단계별로 실행 합니다.  
  
> [!NOTE]
> 이 메서드는 [단계](../../../extensibility/debugger/reference/idebugprogram2-step.md)대신 사용 해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pThread`  
 진행 단계별 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.  
  
 `sk`  
 진행 [Stkind](../../../extensibility/debugger/reference/stepkind.md) 값 중 하나입니다.  
  
 `step`  
 진행 [Stunit](../../../extensibility/debugger/reference/stepunit.md) 값 중 하나입니다.  
  
## <a name="return-value"></a>Return Value  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 스레드 동기화 또는 스레드 간 통신이 있는 경우 특정 스레드가 단계별로 실행 될 때 프로세스의 다른 스레드를 실행 해야 합니다.  
  
 **경고** 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
