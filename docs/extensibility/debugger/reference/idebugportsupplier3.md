---
title: 아이디버그포트공급업체3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724433"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
이 인터페이스를 통해 호출자는 포트 공급자가 디버거 호출 간에 포트를 디스크에 기록하여 보존할 수 있는지 여부를 결정한 다음 보존된 포트 목록을 얻을 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 이 인터페이스를 구현하여 포트 정보를 디스크에 유지하거나 저장합니다. 이 인터페이스는 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스와 동일한 개체에서 구현되어야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 `IDebugPortSupplier2` 얻으려면 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스에서 상속된 메서드 외에도 다음을 지원합니다.

|방법|설명|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|포트 공급자가 디버거 호출 사이에 포트를 디스크에 기록하여 포트를 지속할 수 있는지 여부를 반환합니다.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|이 포트 공급자가 디스크에 기록한 모든 포트를 열거하는 데 사용할 수 있는 개체를 반환합니다.|

## <a name="remarks"></a>설명
 포트 공급자가 호출 간에 포트를 지속할 수 있는 경우 이 인터페이스를 구현해야 합니다. 포트 공급자가 인스턴스화될 때 포트를 로드하고 포트 공급자가 소멸될 때 디스크에 기록해야 합니다.

 디버그 엔진은 일반적으로 포트 공급자와 상호 작용하지 않으며 이 인터페이스에 사용할 수 없습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
