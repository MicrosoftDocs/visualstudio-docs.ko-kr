---
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 676a3a7d184c1f34cafcfc2b2a4dd7a1c3f81a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387332"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

중지 된 상태에서이 프로그램을 계속 실행 합니다. 모든 이전 실행 상태 (예: 단계)는 지워지고 프로그램의 실행이 다시 시작 됩니다.  
  
> [!NOTE]
> 이 메서드는 더 이상 사용되지 않습니다. 대신 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) 메서드를 사용 해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Return Value  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 사용자가 다른 프로그램의 스레드에서 중지 된 상태에서 실행을 시작 하면이 메서드가이 프로그램에서 호출 됩니다. 이 메서드는 사용자가 IDE의 **디버그** 메뉴에서 **시작** 명령을 선택 하는 경우에도 호출 됩니다. 이 메서드의 구현은 프로그램의 현재 스레드에서 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드를 호출 하는 것 처럼 간단할 수 있습니다.  
  
> [!WARNING]
> 이 호출을 처리 하는 동안 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 에 중지 이벤트 또는 즉각적인 (동기) 이벤트를 보내지 않습니다. 그렇지 않으면 디버거가 응답 하지 않을 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [재개](../../../extensibility/debugger/reference/idebugthread2-resume.md)
