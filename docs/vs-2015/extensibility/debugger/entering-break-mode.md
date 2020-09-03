---
title: 중단 모드 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182246"
---
# <a name="entering-break-mode"></a>중단 모드 적용
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음에서는 함수를 한 단계씩 실행 한 후 중단점에 커서가 있거나 중단점까지 실행 한 후 중단점에 도달 하면 발생 하는 프로세스에 대해 설명 합니다.  
  
## <a name="break-mode-process"></a>중단 모드 프로세스  
  
1. DE (디버그 엔진)는 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)또는 기타 중지 이벤트를 보내 IDE가 중단 모드로 전환 되도록 합니다.  
  
2. SDM은 다음과 같이 스레드에서 호출 스택 정보를 가져옵니다.  
  
    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    - 소스 코드 정보를 가져오는 [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)  
  
    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) 를 통해 파일 이름을 가져옵니다.  
  
    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 를 통해 문 범위 가져오기  
  
    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) 를 통해 메모리 정보 가져오기  
  
## <a name="see-also"></a>관련 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
