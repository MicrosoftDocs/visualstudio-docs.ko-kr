---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7274d621e47c9c705cc0ce6bc4ad49f24e144f59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683289"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스를 통해 세션 디버그 관리자 (SDM)는 디버그 엔진 (DE)을 나타내는 인터페이스를 검색할 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE는 DE-DE의 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스에 대 한 액세스를 허용 하기 위해 가장 일반적인 de 인터페이스 (예: [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)및 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md))를 구현 하는 개체에 대해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 일반적인 DE 인터페이스에서 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 를 호출 하 여이 인터페이스를 가져옵니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDebugQueryEngine2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|사용자 지정 디버그 엔진 (DE) 인터페이스를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 일반적으로 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 구현 하는 개체에서 구현 되며 함수를 통한 인과 관계 순서 단계별 실행을 지원 합니다. 즉, 디버거에서 함수를 실행 하는 경우 다음에 실행할 함수는 스택의 이전 함수가 아닐 수 있지만 다른 스레드의 함수는 완전히 아닙니다. "인과 관계"에 대 한 정의는 [Visual Studio 디버거 용어](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
