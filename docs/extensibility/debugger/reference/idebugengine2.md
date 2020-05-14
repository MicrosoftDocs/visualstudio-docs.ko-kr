---
title: 아이데버그엔진2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730854"
---
# <a name="idebugengine2"></a>IDebugEngine2
이 인터페이스는 DE(디버그 엔진)를 나타냅니다. 중단점 만들기에서 예외 설정 및 지우기에 이르기까지 디버깅 세션의 다양한 측면을 관리하는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 프로그램의 디버깅을 관리하기 위해 사용자 지정 DE에 의해 구현됩니다. 이 인터페이스는 DE에서 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 예외 관리, 중단점 만들기 및 DE에서 보낸 동기 이벤트에 응답하는 등 디버깅 세션을 관리하기 위해 세션 디버그 관리자(SDM)에서 호출됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugEngine2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|DE에서 디버깅하는 모든 프로그램에 대해 열거기를 만듭니다.|
|[연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)|프로그램에 DE를 연결합니다.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE에서 보류 중인 중단점을 만듭니다.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|DE가 지정된 예외를 처리하는 방법을 지정합니다.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|디버그 엔진에서 더 이상 처리되지 않도록 지정된 예외를 제거합니다.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|IDE가 특정 런타임 아키텍처 또는 언어에 대해 설정한 예외 목록을 제거합니다.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|DE의 GUID를 가져옵니다.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|지정된 프로그램이 비정상적으로 종료되었으며 DE가 프로그램에 대한 모든 참조를 정리하고 프로그램 삭제 이벤트를 보내야 한다는 것을 DE에 알립니다.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|이전에 DE에서 SDM으로 보낸 동기 디버그 이벤트가 수신되고 처리되었음을 나타내기 위해 SDM에서 호출했습니다.|
|[Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|DE의 로캘을 설정합니다.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|DE에서 현재 사용 중인 레지스트리 루트를 설정합니다.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|메트릭을 설정합니다.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|다음에 스레드 중 하나가 실행하려고 할 때 이 DE에 의해 디버깅되는 모든 프로그램이 실행을 중지하도록 요청합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
