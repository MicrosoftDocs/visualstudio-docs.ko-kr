---
title: 프로세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153662"
---
# <a name="processes"></a>프로세스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면에서 **프로세스**는 다음과 같습니다.  
  
- 는 프로그램 집합에 대 한 컨테이너입니다. 스레드 집합의 컨테이너인 Windows 프로세스와 매우 유사 합니다.  
  
- 이름, 식별자 또는 실제 식별자로 자신을 식별할 수 있습니다.  
  
- 는 실행 중인 모든 프로그램 (및 해당 스레드)을 열거할 수 있습니다.  
  
- 자체, 실행 중인 포트 및이를 포함 하는 컴퓨터를 설명할 수 있습니다.  
  
- 하나 이상의 프로그램을 만들거나, 만든 프로그램을 종료 하거나, 프로그램을 중지할 수 있습니다.  
  
- 는 프로세스를 시작할 때 생성 되는 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스로 표시 됩니다. 프로세스는 SDM (세션 디버그 관리자) 또는 [Launchsuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)에 의해 시작 됩니다.  
  
  디버그 패키지는 [attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)를 호출 하 여 디버그 엔진 (DE)을 프로세스에 연결할 수 있습니다. 즉, DE는 처리할 수 있는 프로세스에서 실행 되는 모든 가능한 프로그램에 연결 됩니다. 예를 들어 공용 언어 런타임 DE가 프로세스에 연결 되 면 관리 코드를 실행 하는 프로그램에만 연결 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [프로그램인](../../extensibility/debugger/programs.md)   
 [임계값](../../extensibility/debugger/threads.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [패키지 디버그](../../extensibility/debugger/debug-package.md)   
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended 중단 됨](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [연결](../../extensibility/debugger/reference/idebugprocess2-attach.md)
