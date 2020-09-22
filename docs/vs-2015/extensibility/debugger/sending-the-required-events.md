---
title: 필요한 이벤트를 보내는 중 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 457e2daf3e52c23ba9733d09d3aeb94750b5fab9
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "90842218"
---
# <a name="sending-the-required-events"></a>필요한 이벤트 보내기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 절차를 사용 하 여 필요한 이벤트를 전송 합니다.  
  
## <a name="process-for-sending-required-events"></a>필요한 이벤트를 보내는 프로세스  
 다음 이벤트는 디버그 엔진 (DE)을 만들어 프로그램에 연결 하는 경우에 필요 합니다.  
  
1. 프로세스에서 하나 이상의 프로그램을 디버깅 하기 위해 DE-DE가 초기화 되 면 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 이벤트 개체를 세션 디버그 관리자 (SDM)로 보냅니다.  
  
2. 디버그할 프로그램을에 연결 하는 경우 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트 개체를 SDM으로 보냅니다. 이 이벤트는 엔진 디자인에 따라 중지 이벤트 일 수 있습니다.  
  
3. 프로세스를 시작할 때 프로그램이에 연결 되어 있으면 새 스레드의 IDE에 알리도록 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 이벤트 개체를 SDM에 보냅니다. 이 이벤트는 엔진 디자인에 따라 중지 이벤트 일 수 있습니다.  
  
4. 디버그 중인 프로그램의 로드가 완료 되거나 프로그램에 연결을 완료 한 경우 SDM에 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 이벤트 개체를 보냅니다. 이 이벤트는 중지 이벤트 여야 합니다.  
  
5. 디버그할 응용 프로그램이 시작 되 면 런타임 아키텍처에서 코드의 첫 번째 명령이 실행 될 때 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 이벤트 개체를 SDM으로 보냅니다. 이 이벤트는 항상 중지 이벤트입니다. 디버깅 세션을 한 단계씩 실행 하는 경우 IDE는이 이벤트를 중지 합니다.  
  
> [!NOTE]
> 대부분의 언어는 코드의 시작 부분에서 전역 이니셜라이저 또는 미리 컴파일된 외부 함수 (CRT 라이브러리 또는 _Main)를 사용 합니다. 디버깅 중인 프로그램의 언어에 초기 진입점 전에 이러한 형식의 요소가 포함 되어 있는 경우이 코드가 실행 되 고 **main** 또는와 같은 사용자 진입점에 도달할 때 진입점 이벤트가 전송 됩니다 `WinMain` .  
  
## <a name="see-also"></a>참고 항목  
 [디버그할 프로그램을 사용하도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
