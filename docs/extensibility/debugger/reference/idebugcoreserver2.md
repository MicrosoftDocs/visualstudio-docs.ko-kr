---
title: IDebugCoreServer2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733028"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
이 인터페이스는 네트워크에 있는 컴퓨터의 서버에서 정보를 표시 하 고 가져오는 데 사용 됩니다.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는 서버를 나타내기 위해이 인터페이스를 구현 합니다. Visual Studio의 각 인스턴스는이 인터페이스의 인스턴스를 만듭니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 사용자 지정 포트 공급자는 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)에 대 한 호출에서이 인터페이스를 수신 합니다.

 디버그 엔진은 [Getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) 에 대 한 호출을 통해이 인터페이스를 간접적으로 가져올 수 있습니다 .이 인터페이스는에서 파생 되는 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)을 반환 `IDebugCoreServer2` 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugCoreServer2` .

|메서드|설명|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|컴퓨터의 이름과 특성을 가져옵니다.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|컴퓨터의 이름을 가져옵니다.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|컴퓨터에 있는 포트 공급자를 가져옵니다.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|컴퓨터에 이미 있는 포트를 가져옵니다.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|컴퓨터의 모든 포트에 대 한 열거자를 만듭니다.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|컴퓨터의 모든 포트 공급 업체에 대 한 열거자를 만듭니다.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|컴퓨터의 컴퓨터 유틸리티를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 Visual Studio에서 네트워크의 컴퓨터에서 실행 중인 프로세스를 검색 하는 데도 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
