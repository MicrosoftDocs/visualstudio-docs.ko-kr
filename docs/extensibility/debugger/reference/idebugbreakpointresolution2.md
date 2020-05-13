---
title: 아이디버그브레이크포인트해상도2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb5e4f9e32017cfb493aae00a24f9f8184605d1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734742"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
이 인터페이스는 바인딩된 중단점을 설명하는 정보를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다. 이 인터페이스는 사용자가 중단점의 속성을 볼 때 세션 디버그 관리자가 사용하는 바인딩된 중단점에 대한 설명을 제공합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetBreakpointResolution에](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) 대한 호출은 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugBreakpointResolution2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|이 해상도로 표시되는 중단점의 형식을 가져옵니다.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|이 중단점을 설명하는 중단점 확인 정보를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
