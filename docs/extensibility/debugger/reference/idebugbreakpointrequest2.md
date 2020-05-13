---
title: 아이디버그브레이크포인트요청2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734920"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
이 인터페이스는 모든 유형의 중단점을 만들고 바인딩하는 데 필요한 정보를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 세션 디버그 관리자(SDM)는 일반적으로 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 디버그 엔진(DE)은 보류 중인 중단점을 만들기 위해 [CreatePendingBreakpoint호출을](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 통해 이 인터페이스를 수신합니다. [GetBreakpointRequest에](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) 대한 호출은 DE에서 이 인터페이스를 검색할 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugBreakpointRequest2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|이 중단점 요청의 중단점 위치 유형을 가져옵니다.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|이 중단점 요청을 설명하는 중단점 요청 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 디버깅 중인 프로그램이 로드된 후 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 호출은 프로그램의 요청된 위치에 보류 중인 중단점을 바인딩합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [바인딩](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
