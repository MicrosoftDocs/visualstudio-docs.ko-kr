---
title: 'IDebugExceptionEvent2:: Can Sto디버기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 383287a027a75adfb4c58020675e08a46198eacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163803"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)이 실행을 다시 시작할 때 디버깅 중인 프로그램에이 예외를 전달 하는 옵션을 지원 하는지 여부를 결정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Return Value  
 는 `S_OK` (예외를 프로그램에 전달할 수 있음) 또는 `S_FALSE` (예외를 전달할 수 없음)을 반환 합니다.  
  
## <a name="remarks"></a>설명  
 DE에는 디버기에 전달 하기 위한 기본 작업이 있어야 합니다. IDE는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트를 수신 하 고 메서드를 호출 하지 않고 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 메서드를 호출할 수 있습니다 `CanPassToDebuggee` . 따라서 DE에는 예외를 전달 하기 위한 기본 사례가 있어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
