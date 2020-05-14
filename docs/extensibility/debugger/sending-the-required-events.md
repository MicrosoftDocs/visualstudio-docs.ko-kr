---
title: 필수 이벤트 보내기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713002"
---
# <a name="send-the-required-events"></a>필요한 이벤트 보내기
필요한 이벤트를 보낼 때 는 이 절차를 사용합니다.

## <a name="process-for-sending-required-events"></a>필요한 이벤트 전송 프로세스
 DE(디버그 엔진)를 만들고 프로그램에 연결할 때 다음 이벤트가 필요합니다.

1. 프로세스에서 하나 이상의 프로그램을 디버깅하기 위해 DE가 초기화되면 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 이벤트 개체를 세션 디버그 관리자(SDM)로 보냅니다.

2. 디버깅할 프로그램이 연결되면 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트 개체를 SDM에 보냅니다. 이 이벤트는 엔진 설계에 따라 중지 이벤트일 수 있습니다.

3. 프로세스가 시작될 때 프로그램이 연결된 경우 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 이벤트 개체를 SDM에 보내 IDE에 새 스레드를 알립니다. 이 이벤트는 엔진 설계에 따라 중지 이벤트일 수 있습니다.

4. 디버깅 중인 프로그램이 로드가 완료되거나 프로그램에 연결할 때 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 이벤트 개체를 SDM에 보냅니다. 이 이벤트는 중지 이벤트여야 합니다.

5. 디버깅할 응용 프로그램이 시작되면 런타임 아키텍처의 코드 의 첫 번째 명령이 실행될 때 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 이벤트 개체를 SDM에 보냅니다. 이 이벤트는 항상 중지 이벤트입니다. 디버깅 세션에 들어서면 IDE가 이 이벤트에서 중지됩니다.

> [!NOTE]
> 대부분의 언어는 코드 의 시작 부분에 전역 초기화자 또는 CRT 라이브러리 또는 _Main 외부 사전 컴파일된 함수를 사용합니다. 디버깅하는 프로그램의 언어에 초기 진입점 이전에 이러한 유형의 요소가 포함되어 있으면 이 코드가 실행되고 **기본** 또는 `WinMain`에 도달한 사용자 진입점에 도달하면 진입점 이벤트가 전송됩니다.

## <a name="see-also"></a>참조
- [프로그램을 디버깅할 수 있도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
