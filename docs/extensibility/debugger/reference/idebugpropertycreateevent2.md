---
title: 아이디버그프로퍼라이드이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720923"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
이 인터페이스는 특정 문서와 연결된 속성을 만들 때 디버그 엔진(DE)에 의해 세션 디버그 관리자(SDM)로 전송됩니다.

## <a name="syntax"></a>구문

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 속성이 만들어졌다는 보고를 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다. 이 인터페이스는 DE가 로드되거나 생성된 스크립트와 연결된 속성을 만들고 해당 스크립트가 IDE에 표시되어야 하는 경우 구현됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 이 이벤트 개체를 만들고 전송하여 속성이 생성되었음을 보고합니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 인터페이스의 `IDebugPropertyCreateEvent2` 메서드를 보여 줍니다.

|방법|설명|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|새 속성을 가져옵니다.|

## <a name="remarks"></a>설명
 속성에 연결된 특정 문서 또는 스크립트가 있는 경우 DE는 문서 이름으로 **스크립트 문서** 창을 업데이트하기 위해 이 이벤트를 SDM으로 보낼 수 있습니다. SDM은 [I알 수 없는](/cpp/atl/iunknown) `guidDocument` 포인터를 `VARIANT` 포함하는 포인터를 검색하기 위해 인수와 함께 [GetExtendedInfo를](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) 호출합니다. SDM은 이 포인터에서 [QueryInterface를](/cpp/atl/queryinterface) 호출하여 **스크립트 문서** 창을 업데이트하는 데 사용되는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 인터페이스를 검색합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
