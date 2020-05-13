---
title: 바인딩 중단점 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739236"
---
# <a name="bind-breakpoints"></a>중단점 바인딩
사용자가 **F9을**눌러 중단점을 설정하는 경우 IDE는 요청을 공식화하고 디버그 세션을 표시하여 중단점을 만듭니다.

## <a name="set-a-breakpoint"></a>중단점 설정
 중단점 설정은 중단점의 영향을 받는 코드 나 데이터를 아직 사용할 수 없기 때문에 2 단계 프로세스입니다. 첫째, 중단점을 설명해야 하며 코드 나 데이터를 사용할 수 있게 되면 다음과 같이 해당 코드 또는 데이터에 바인딩되어야 합니다.

1. 중단점은 관련 디버그 엔진(DEs)에서 요청된 다음 중단점은 코드 또는 데이터에 바인딩되어 사용 가능해집니다.

2. 중단점 요청은 디버그 세션으로 전송되어 모든 관련 DEs로 전송됩니다. 중단점을 처리하도록 선택하는 모든 DE는 해당 보류 중인 중단점을 만듭니다.

3. 디버그 세션은 보류 중인 중단점을 수집하고 디버그 패키지(Visual Studio의 디버깅 구성 요소)로 다시 보냅니다.

4. 디버그 패키지는 디버그 세션이 보류 중인 중단점을 코드 또는 데이터에 바인딩하라는 메시지를 표시합니다. 디버그 세션은 이 요청을 모든 관련 DEs로 보냅니다.

5. DE가 중단점을 바인딩할 수 있는 경우 중단점 바인딩 된 이벤트를 디버그 세션으로 다시 보냅니다. 그렇지 않으면 중단점 오류 이벤트를 대신 보냅니다.

## <a name="pending-breakpoints"></a>보류 중인 중단점
 보류 중인 중단점은 여러 코드 위치에 바인딩할 수 있습니다. 예를 들어 C++ 템플릿에 대한 소스 코드 줄은 템플릿에서 생성된 모든 코드 시퀀스에 바인딩할 수 있습니다. 디버그 세션은 중단점 바인딩 이벤트를 사용하여 이벤트가 전송될 때 중단점에 바인딩된 코드 컨텍스트를 열거할 수 있습니다. 나중에 더 많은 코드 컨텍스트를 바인딩할 수 있으므로 DE는 각 바인드 요청에 대해 여러 중단점 바인딩 이벤트를 보낼 수 있습니다. 그러나 DE는 바인드 요청당 하나의 중단점 오류 이벤트만 보내야 합니다.

## <a name="implementation"></a>구현
 프로그래밍 방식으로 디버그 패키지는 세션 디버그 관리자(SDM)를 호출하고 설정할 중단점을 설명하는 [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) 구조를 래핑하는 [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 인터페이스를 제공합니다. 중단점은 여러 형태일 수 있지만 궁극적으로 코드 또는 데이터 컨텍스트로 해결됩니다.

 SDM은 [CreatePending중단점](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 메서드를 호출하여 각 관련 DE에 이 호출을 전달합니다. DE가 중단점을 처리하도록 선택하면 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스를 만들고 반환합니다. SDM은 이러한 인터페이스를 수집하여 단일 `IDebugPendingBreakpoint2` 인터페이스로 디버그 패키지로 다시 전달합니다.

 지금까지 이벤트가 생성되지 않았습니다.

 그런 다음 디버그 패키지는 DE에서 구현되는 [Bind를](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)호출하여 보류 중인 중단점을 코드 또는 데이터에 바인딩하려고 시도합니다.

 중단점이 바인딩된 경우 DE는 디버그 패키지에 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 이벤트 인터페이스를 보냅니다. 디버그 패키지는 이 인터페이스를 사용하여 하나 이상의 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 인터페이스를 반환하는 [EnumBoundBreakpoints를](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)호출하여 중단점에 바인딩된 모든 코드 컨텍스트(또는 단일 데이터 컨텍스트)를 열거합니다. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) 인터페이스는 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 인터페이스를 반환하고 [GetResolutionInfo는](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 코드 또는 데이터 컨텍스트를 포함하는 [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) 공용 구조체를 반환합니다.

 DE가 중단점을 바인딩할 수 없는 경우 단일 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 이벤트 인터페이스를 디버그 패키지로 보냅니다. 디버그 패키지는 [GetErrorBreakpoint를](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)호출하여 오류 유형(오류 또는 경고) 및 정보 메시지를 검색한 다음 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 및 [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)를 호출합니다. 그러면 오류 유형과 메시지가 포함된 [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) 구조가 반환됩니다.

 DE가 중단점을 처리하지만 바인딩할 수 없는 경우 형식 `BPET_TYPE_ERROR`의 오류를 반환합니다. 디버그 패키지는 오류 대화 상자를 표시하여 응답하고 IDE는 소스 코드 줄의 왼쪽에 중단점 문말 내부에 느낌표 문선을 배치합니다.

 DE가 중단점을 처리하는 경우 바인딩할 수 없지만 다른 DE에서는 바인딩할 수 있으므로 경고를 반환합니다. IDE는 소스 코드 줄의 왼쪽에 중단점 문말 내부에 질문 문선을 배치하여 응답합니다.

## <a name="see-also"></a>참조
- [작업 디버깅](../../extensibility/debugger/debugging-tasks.md)
