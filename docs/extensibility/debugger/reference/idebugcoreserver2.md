---
title: 이데버그코어서버2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5990c84fbaeb5ebb3b1e188d3317234afda06b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733028"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
이 인터페이스는 네트워크의 컴퓨터에 있는 서버에서 정보를 나타내고 가져오는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 서버를 나타내기 위해 이 인터페이스를 구현합니다. Visual Studio의 각 인스턴스는 이 인터페이스의 인스턴스를 만듭니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 사용자 지정 포트 공급자는 [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)에 대한 호출에서 이 인터페이스를 수신합니다.

 디버그 엔진은 `IDebugCoreServer2`GetServer(IDebugCoreServer3에서 파생된 인터페이스인 [IDebugCoreServer3를](../../../extensibility/debugger/reference/idebugcoreserver3.md)반환하는)를 호출하여 간접적으로 이 인터페이스를 가져올 수 있습니다. [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugCoreServer2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|컴퓨터의 이름과 특성을 가져옵니다.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|컴퓨터의 이름을 가져옵니다.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|컴퓨터에 있는 포트 공급자를 가져옵니다.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|컴퓨터에 이미 있는 포트를 가져옵니다.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|컴퓨터의 모든 포트에 대한 열거형기를 만듭니다.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|기계의 모든 포트 공급업체에 대한 열거형기를 만듭니다.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|기계에 대한 기계 유틸리티를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 Visual Studio에서 네트워크의 컴퓨터에서 실행되는 프로세스를 찾아보는 데도 사용됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
