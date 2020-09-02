---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97bc8383f990f6c0c35a402f2ab36b2595d82a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147681"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 interfac는 현재 디버그 세션에서 실행 되는 스레드를 열거 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE)은이 인터페이스를 구현 하 여 프로그램의 스레드 목록을 나타냅니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [Enumthreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) 를 호출 하 여 프로세스에서 실행 되는 모든 프로그램의 모든 스레드 목록을 나타내는이 인터페이스를 가져옵니다. [Enumthreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 를 호출 하 여 프로그램에서 실행 중인 스레드 목록을 나타내는이 인터페이스를 가져옵니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugThreads2` .  
  
|메서드|설명|  
|------------|-----------------|  
|[다음](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|열거형 시퀀스에서 지정 된 수의 스레드를 검색 합니다.|  
|[skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|열거형 시퀀스에서 지정 된 수의 스레드를 건너뜁니다.|  
|[재설정](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|  
|[복제](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|열거자의 스레드 수를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 Visual Studio는 일반적으로 **스레드** 창을 업데이트 하는 것 뿐만 아니라 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)및 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)을 호출 하기 위해 목록의 첫 번째 스레드를 가져오는 인터페이스를 가져옵니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [이동](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [하기](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [실행](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
