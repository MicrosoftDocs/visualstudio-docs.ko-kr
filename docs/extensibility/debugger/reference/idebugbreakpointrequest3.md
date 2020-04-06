---
title: 아이디버그브레이크포인트요청3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734824"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
이 인터페이스는 모든 유형의 중단점을 만들고 바인딩하는 데 필요한 정보를 나타냅니다. [IDebugBreakpointRequest2의](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)확장입니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 세션 디버그 관리자(SDM)는 일반적으로 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 디버그 엔진(DE)은 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)에 대한 호출에서 수신된 IDebugBreakpointRequest2 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출하여 이 인터페이스에 액세스합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugBreakpointRequest2에서](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)상속된 메서드 외에도 인터페이스는 `IDebugBreakpointRequest3` 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|이 중단점 요청을 설명하는 중단점 요청 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조를 통해 DE에 추가 정보를 제공하는 데 사용됩니다. 이 추가 정보에는 DE의 공급업체 ID(GUID 형식), 추적점 이름 및 중단점 제약 조건의 이름이 포함됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
