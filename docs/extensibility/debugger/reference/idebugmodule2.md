---
description: 이 인터페이스는 모듈 즉, DLL과 같은 프로그램의 실행 가능한 단위를 나타냅니다.
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 848aa60ad7b8343d84489f460cfcb5fb6ec2d77d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065556"
---
# <a name="idebugmodule2"></a>IDebugModule2
이 인터페이스는 모듈 즉, DLL과 같은 프로그램의 실행 가능한 단위를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 모듈을 나타내고 해당 모듈에 대 한 정보에 대 한 액세스를 제공 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) 에 대 한 호출은이 인터페이스를 반환 합니다. DE는 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드를 사용 하 여 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다.

 이 인터페이스는 [enuminfo](../../../extensibility/debugger/reference/frameinfo.md) 구조에서 반환 될 수도 있습니다 ( [enum프레임 정보](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)에 대 한 호출에서 반환 됨).

- [다음](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) 도이 인터페이스를 반환 합니다.[Enummodules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 은 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugModule2` .

|메서드|Description|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|이 모듈을 설명 하는 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 을 가져옵니다.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|사용되지 않습니다. 사용 하지 마십시오. 이 모듈에 대 한 기호를 다시 로드 합니다.|

## <a name="remarks"></a>설명
 모듈 정보는 IDE의 **모듈** 창에 표시 될 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
