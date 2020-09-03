---
title: IDebugModule3 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726737"
---
# <a name="idebugmodule3"></a>IDebugModule3
이 인터페이스는 기호 및 JustMyCode 상태의 대체 위치를 지 원하는 모듈을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 기호에 대 한 대체 위치를 지원 하 고 JustMyCode 상태를 사용 합니다 ("JustMyCode" 정의는 [Visual Studio 디버거 용어집](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) 참조).

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Get기호 Searchinfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 에 대 한 호출은이 인터페이스를 반환 합니다. DE는 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드를 사용 하 여 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 인터페이스를 세션 디버그 관리자 (SDM)로 보냅니다. 또한 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 를 호출 하면이 인터페이스가 반환 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|기호에 대해 검색 된 경로 목록과 각 경로를 검색 한 결과를 반환 합니다.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|현재 모듈에 대 한 기호를 로드 하 고 초기화 합니다.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|모듈이 사용자 코드를 나타내는지 여부를 지정 하는 플래그를 반환 합니다.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|모듈을 사용자 코드로 간주 해야 하는지 여부를 지정 합니다.|

## <a name="remarks"></a>설명
 Visual Studio는이 인터페이스의 일반적인 소비자입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
