---
title: 프로그램 종료 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421865"
---
# <a name="terminating-a-program"></a>프로그램 종료
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음은 하나의 스레드를 사용 하는 단일 프로그램 종료에 대 한 설명입니다.  
  
## <a name="termination-process"></a>종료 프로세스  
  
1. DE는 유효한 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)로 [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 를 보냅니다.  
  
2. DE는 유효한 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)로 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 를 보냅니다.  
  
   IDE가 디자인 모드로 전환 됩니다. 디버그 엔진 또는 런타임 환경에서는 [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 를 호출 하 여 포트에서 프로그램을 제거 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
