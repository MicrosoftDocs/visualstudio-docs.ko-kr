---
title: IDebugErrorBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1581e9f00e4a2dcb0a7bdab67cfe601b1c9dd05f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888383"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
이 인터페이스는 중단점 오류의 해상도를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진은 중단점에 대 한 지원의 일부로이 인터페이스를 구현 합니다. 이 인터페이스는 중단점을 바인딩하지 못한 위치를 보고 하는 데 사용 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Getto Pointresolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 을 호출 하면이 인터페이스를 반환 하 여 중단점을 바인딩하지 못한 위치에 대 한 정보를 제공 합니다. [Geterrorbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) 메서드는 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugErrorBreakpointResolution2` .

|메서드|Description|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|중단점 형식을 가져옵니다.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|중단점 확인 정보를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
