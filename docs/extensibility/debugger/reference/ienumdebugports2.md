---
title: 이넘데버그포트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716108"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
이 인터페이스는 컴퓨터 또는 포트 공급자의 포트를 개명합니다.

## <a name="syntax"></a>구문

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 공급자가 만든 포트 목록을 나타내기 위해 이 인터페이스를 구현합니다. Visual Studio는 자체 포트 공급자를 지원하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [EnumPorts를](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 호출하여 포트 공급자가 만든 포트 목록을 나타내는 이 인터페이스를 가져옵니다. [EnumPersistedPorts를](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) 호출하여 디스크에 저장된 포트 목록을 나타내는 이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugPorts2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|열거 순서에서 지정된 수의 포트를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|열거 순서에서 지정된 수의 포트를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|열거형의 포트 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 이 인터페이스를 사용하여 프로세스에 연결하는 데 사용되는 포트 목록을 채웁니다.

 디버그 엔진은 일반적으로 이 인터페이스를 사용하지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
