---
title: 이데버그캔스탑이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734516"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
이 인터페이스는 세션 디버그 관리자(SDM)에게 현재 코드 위치에서 중지할지 여부를 묻는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 소스 코드를 단계적 단계적 단계적 지원으로 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다(SDM은 `IDebugEvent2` [QueryInterface를](/cpp/atl/queryinterface) 사용하여 인터페이스에 액세스합니다).

 이 인터페이스의 구현은 SDM의 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 호출을 디버그 엔진에 전달해야 합니다. 예를 들어 디버그 엔진의 메시지 처리 스레드에 게시된 메시지 또는 이 인터페이스를 구현하는 개체가 디버그 엔진에 대한 참조를 보유하고 플래그가 `IDebugCanStopEvent2::CanStop`로 전달된 디버그 엔진으로 다시 호출할 수 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 DE가 실행을 계속하라는 메시지가 메시지가 지고 DE가 코드를 단계별로 실행할 때마다 이 메서드를 보낼 수 있습니다. 이 이벤트는 디버깅 중인 프로그램에 연결할 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugCanStopEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|이 이벤트의 이유를 가져옵니다.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|디버깅 중인 프로그램이 이 이벤트의 위치에서 중지할지(중지 이유를 설명하는 이벤트를 전송) 또는 실행을 계속할지 지정합니다.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|이 이벤트의 위치를 설명하는 문서 컨텍스트를 가져옵니다.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|이 이벤트의 위치를 설명하는 코드 컨텍스트를 가져옵니다.|

## <a name="remarks"></a>설명
 DE는 사용자가 함수에 들어가서 DE가 디버그 정보를 찾지 못하거나 디버그 정보가 존재하지만 해당 위치에 대해 소스 코드를 표시할 수 있는지 를 알 수 없는 경우 이 인터페이스를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
