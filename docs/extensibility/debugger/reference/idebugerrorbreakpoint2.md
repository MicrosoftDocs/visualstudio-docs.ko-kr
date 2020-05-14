---
title: IDebug오류 중단점2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17b20d0f3545b0f7266ad6d0c6423d581233dd3c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730075"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
이 인터페이스는 잘못된 위치, 잘못된 식 또는 보류 중인 중단점이 바인딩되지 않은 이유(코드가 아직 로드되지 않은 등)와 같은 오류 또는 경고 중단점을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진은 중단점에 대한 지원의 일부로 이 인터페이스를 구현합니다. 이 인터페이스는 중단점 바인딩 문제를 보고하는 데 사용됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetErrorBreakpoint에](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) 대한 호출은 이 인터페이스를 가져옵니다. 이 인터페이스는 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 또는 [EnumErrorBreakbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)에 대한 호출로(IEnumDebugErrorBreakpoints2 인터페이스로 표시되는 목록의 일부로) 반환될 수도 있습니다. [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugErrorBreakpoint2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|오류를 일으킨 보류 중인 중단점을 가져옵니다.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|오류를 설명하는 중단점 오류 확인을 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
