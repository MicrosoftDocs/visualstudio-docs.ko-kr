---
title: 스레드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 028ad25495ba01d9763c8bec3bbb9c4480d72ff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185365"
---
# <a name="threads"></a>스레드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면에서 **스레드**는 다음과 같습니다.  
  
- 계산의 기본 단위입니다. 스레드는 단일 호출 스택의 컨텍스트 내에서 해당 명령을 순차적으로 실행 하 여 코드 컨텍스트 간에 이동 합니다.  
  
- 는 자신과 실행 중인 프로그램을 식별 하 고 이름을 지정 하 고, 일시 중지 하 고, 다시 시작할 수 있습니다. 또한 스레드는 연결 된 스택 프레임을 열거 하 고, 경우에 따라 다른 스택 프레임으로 이동할 수 있습니다. 스택 프레임의 컨텍스트가 지정 된 경우 스레드에서 연결 된 논리 스레드를 반환할 수 있습니다 (있는 경우). 스레드에는 IDE의 스레드 창에 표시 될 수 있는 일시 중단 횟수와 같은 속성이 있습니다.  
  
- 는 프로그램 실행의 결과로 일반적으로 디버그 엔진 (DE) 또는 가상 머신에서 만든 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 인터페이스로 표시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [프로그램인](../../extensibility/debugger/programs.md)   
 [스택 프레임](../../extensibility/debugger/stack-frames.md)   
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)
