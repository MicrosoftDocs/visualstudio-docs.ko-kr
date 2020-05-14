---
title: 아이데버그 심볼서치2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718791"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
이 인터페이스는 디버그 엔진(DE)에 의해 전송되어 디버깅 중인 모듈의 디버깅 기호가 로드되었음을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 모듈의 기호가 로드되었음을 보고하기 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 모듈의 기호가 로드되었음을 보고하기 위해 이 이벤트 개체를 만들고 보냅니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 인터페이스는 `IDebugSymbolSearchEvent2` 다음 메서드를 노출합니다.

|방법|설명|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|기호 검색 결과에 대한 정보를 검색합니다.|

## <a name="remarks"></a>설명
 이 이벤트는 기호가 로드되지 못한 경우에도 전송됩니다. 호출을 `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` 사용하면 이 이벤트의 처리기가 모듈에 실제로 기호가 있는지 확인할 수 있습니다.

 Visual Studio는 일반적으로 이 이벤트를 사용하여 모듈 창에서 로드된 기호의 상태를 **업데이트합니다.**

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
