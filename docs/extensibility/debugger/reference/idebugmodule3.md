---
title: 아이디버그모듈3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726737"
---
# <a name="idebugmodule3"></a>IDebugModule3
이 인터페이스는 기호 및 JustMyCode 상태의 대체 위치를 지원하는 모듈을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 이 인터페이스를 구현하여 기호의 대체 위치를 지원하고 JustMyCode 상태로 작업합니다("JustMyCode"의 정의는 [Visual Studio 디버거 용어집](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) 참조).

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetSymbolSearchInfo에](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 대한 호출은 이 인터페이스를 반환합니다. DE는 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드를 사용하여 세션 디버그 관리자(SDM)에 [IDebugSymbolSearchEventEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 인터페이스를 보냅니다. 또한 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출하면 이 인터페이스가 반환됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|기호를 검색한 경로 목록과 각 경로를 검색한 결과를 반환합니다.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|현재 모듈의 기호를 로드하고 초기화합니다.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|모듈이 사용자 코드를 나타내는지 여부를 지정하는 플래그를 반환합니다.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|모듈을 사용자 코드로 간주할지 여부를 지정합니다.|

## <a name="remarks"></a>설명
 비주얼 스튜디오는 이 인터페이스의 일반적인 소비자입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
