---
title: 아이디버그모듈2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726911"
---
# <a name="idebugmodule2"></a>IDebugModule2
이 인터페이스는 DLL과 같은 프로그램의 실행 단위인 모듈을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DEBug 엔진(DE)은 모듈을 나타내고 해당 모듈에 대한 정보에 대한 액세스를 제공하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetModule에](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) 대한 호출은 이 인터페이스를 반환합니다. DE는 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드를 사용하여 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 인터페이스를 세션 디버그 관리자(SDM)로 보냅니다.

 이 인터페이스는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) [구조(EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)호출에 의해 반환됨)에서도 반환될 수 있습니다.

- [다음으로](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) 이 인터페이스도[반환합니다(EnumModules는](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) [IEnumDebugModules2 인터페이스를 반환합니다).](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugModule2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|이 모듈을 설명하는 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 가져옵니다.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|사용되지 않습니다. 사용하지 마십시오. 이 모듈의 기호를 다시 로드합니다.|

## <a name="remarks"></a>설명
 모듈 정보는 IDE의 **모듈** 창에 표시할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
