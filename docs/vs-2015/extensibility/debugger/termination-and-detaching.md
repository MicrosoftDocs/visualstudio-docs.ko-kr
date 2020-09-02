---
title: 종료 및 분리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176678"
---
# <a name="termination-and-detaching"></a>종료 및 분리
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음은 정상 종료에 대 한 설명입니다.  
  
## <a name="discussion"></a>토론(Discussion)  
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 또는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 인터페이스가 계속 되 면 디버깅 될 응용 프로그램에서 중단점, 예외, 런타임 오류 또는 무한 루프가 발생 하지 않는 경우 디버깅 중인 프로그램이 완료 될 때까지 실행 됩니다. 정상적인 종료입니다.  
  
 정상적인 종료를 구현 하려면 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 을 보내야 합니다. 이렇게 하려면 [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) 메서드를 구현 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
