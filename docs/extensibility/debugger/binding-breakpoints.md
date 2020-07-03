---
title: 바인딩 중단점 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e839b6e0e7967c4802bee5617da3334c5d4033c5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903226"
---
# <a name="bind-breakpoints"></a>중단점 바인딩
사용자가 **F9**키를 눌러 중단점을 설정 하는 경우 IDE에서 요청을 공식화 하 고 디버그 세션에 메시지를 표시 하 여 중단점을 만듭니다.

## <a name="set-a-breakpoint"></a>중단점 설정
 중단점 설정은 중단점의 영향을 받는 코드 또는 데이터를 아직 사용 하지 못할 수 있기 때문에 2 단계 프로세스입니다. 먼저 중단점을 설명 하 고 나 서 코드 또는 데이터를 사용할 수 있게 되 면 다음과 같이 해당 코드 또는 데이터에 바인딩되어야 합니다.

1. 관련 디버그 엔진 (DEs)에서 중단점을 요청 하 고 중단점은 사용할 수 있게 되 면 코드 또는 데이터에 바인딩됩니다.

2. 중단점 요청은 모든 관련 DEs로 전송 되는 디버그 세션으로 전송 됩니다. 중단점을 처리 하도록 선택 하는 모든 DE는 해당 하는 보류 중인 중단점을 만듭니다.

3. 디버그 세션은 보류 중인 중단점을 수집 하 고 디버그 패키지 (Visual Studio의 디버깅 구성 요소)로 다시 보냅니다.

4. 디버그 패키지는 보류 중인 중단점을 코드 또는 데이터에 바인딩하기 위해 디버그 세션에 메시지를 표시 합니다. 디버그 세션은 모든 관련 DEs로이 요청을 보냅니다.

5. DE가 중단점을 바인딩할 수 있는 경우 중단점 바인딩 이벤트를 다시 디버그 세션으로 보냅니다. 그렇지 않으면 중단점 오류 이벤트를 대신 보냅니다.

## <a name="pending-breakpoints"></a>보류 중인 중단점
 보류 중인 중단점은 여러 코드 위치에 바인딩할 수 있습니다. 예를 들어 c + + 템플릿에 대 한 소스 코드 줄은 템플릿에서 생성 된 모든 코드 시퀀스에 바인딩될 수 있습니다. 디버그 세션은 중단점 바인딩 이벤트를 사용 하 여 이벤트가 전송 될 때 중단점에 바인딩된 코드 컨텍스트를 열거할 수 있습니다. 나중에 더 많은 코드 컨텍스트를 바인딩할 수 있으므로 DE는 각 바인드 요청에 대해 여러 중단점 바인딩 이벤트를 보낼 수 있습니다. 그러나 DE는 바인드 요청당 하나의 중단점 오류 이벤트만 전송 해야 합니다.

## <a name="implementation"></a>구현
 디버그 패키지는 프로그래밍 방식으로 [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 인터페이스를 호출 하 여 설정할 중단점을 설명 하는 [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) 구조체를 래핑하는 데 사용 됩니다. 중단점은 많은 형태 이지만 궁극적으로는 코드 또는 데이터 컨텍스트로 확인 됩니다.

 SDM은 [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 메서드를 호출 하 여이 호출을 관련 된 각 DE에 전달 합니다. DE가 중단점을 처리 하도록 선택 하면 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스를 만들고 반환 합니다. SDM은 이러한 인터페이스를 수집 하 여 단일 인터페이스로 다시 디버그 패키지에 전달 합니다 `IDebugPendingBreakpoint2` .

 지금까지 이벤트가 생성 되지 않았습니다.

 그런 다음 디버그 패키지는 DE에서 구현 하는 [bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)를 호출 하 여 보류 중인 중단점을 코드 또는 데이터에 바인딩하려 려 합니다.

 중단점이 바인딩되면 DE는 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 이벤트 인터페이스를 디버그 패키지로 보냅니다. 디버그 패키지는이 인터페이스를 사용 하 여 하나 이상의 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 인터페이스를 반환 하는 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)를 호출 하 여 중단점에 바인딩된 모든 코드 컨텍스트 (또는 단일 데이터 컨텍스트)를 열거 합니다. [GetIDebugBreakpointResolution2 Pointresolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) 인터페이스는 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 인터페이스를 반환 하 고 [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 는 코드 또는 데이터 컨텍스트를 포함 하는 [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) 공용 구조체를 반환 합니다.

 DE가 중단점에 바인딩할 수 없는 경우 단일 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 이벤트 인터페이스를 디버그 패키지로 보냅니다. 디버그 패키지는 [Geterrorbreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)을 호출 하 고 그 다음에 [GetGetResolutionInfo Pointresolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 및 [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)를 호출 하 여 오류 유형 (오류 또는 경고) 및 정보 메시지를 검색 합니다. 그러면 오류 유형 및 메시지를 포함 하는 [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) 구조가 반환 됩니다.

 DE가 중단점을 처리 하지만 바인딩할 수 없는 경우 형식의 오류를 반환 `BPET_TYPE_ERROR` 합니다. 디버그 패키지는 오류 대화 상자를 표시 하 여 응답 하 고, IDE는 소스 코드 줄의 왼쪽에 있는 중단점 문자 모양 안에 느낌표를 놓습니다.

 DE가 중단점을 처리 하는 경우에는 바인딩할 수 없지만 다른 DE는이를 바인딩할 수 있지만 경고를 반환 합니다. IDE는 소스 코드 줄의 왼쪽에 있는 중단점 문자 모양 안에 물음표 문자 모양을 배치 하 여 응답 합니다.

## <a name="see-also"></a>참조
- [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
