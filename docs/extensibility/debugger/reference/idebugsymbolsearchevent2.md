---
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbe99422e506fb86b0a7e1d9d3242783f3258e6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718791"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
이 인터페이스는 디버그 엔진 (DE)에서 디버깅 되는 모듈에 대 한 디버깅 기호가 로드 되었음을 나타내기 위해 전송 됩니다.

## <a name="syntax"></a>Syntax

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는 모듈의 기호가 로드 되었음을 보고 하기 위해이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE는 모듈의 기호가 로드 되었음을 보고 하기 위해이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IDebugSymbolSearchEvent2`인터페이스는 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|기호 검색 결과에 대 한 정보를 검색 합니다.|

## <a name="remarks"></a>설명
 기호를 로드 하지 못한 경우에도이 이벤트가 전송 됩니다. 을 호출 하면 `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` 이 이벤트의 처리기에서 모듈에 실제로 기호가 있는지 확인할 수 있습니다.

 Visual Studio는 일반적으로이 이벤트를 사용 하 여 **모듈** 창에서 로드 된 기호의 상태를 업데이트 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
