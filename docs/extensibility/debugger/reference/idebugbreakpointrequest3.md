---
description: IDebugBreakpointRequest3 인터페이스는 모든 중단점 형식을 만들고 바인딩하는 데 필요한 정보를 나타냅니다.
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6803b62975822f1b5219caa43844c8983303a998
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054415"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
이 인터페이스는 모든 중단점 형식을 만들고 바인딩하는 데 필요한 정보를 나타냅니다. [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)의 확장입니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 세션 디버그 관리자 (SDM)는 일반적으로이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE (디버그 엔진)는 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)에 대 한 호출에서 받은 IDebugBreakpointRequest2 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 를 호출 하 여이 인터페이스에 액세스 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)에서 상속 된 메서드 외에도 인터페이스는 `IDebugBreakpointRequest3` 다음 메서드를 노출 합니다.

|메서드|Description|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|이 중단점 요청을 설명 하는 중단점 요청 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조에 추가 정보를 제공 하는 데 사용 됩니다. 이 추가 정보에는 DE-DE의 공급 업체 ID (GUID 형식), 추적점 이름 및 중단점 제약 조건의 이름이 포함 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
