---
title: 아이데버그코어서버3 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732813"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
이 인터페이스를 통해 프로세스가 실행 중인 서버에 대한 정보에 액세스할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스에서 이 인터페이스를 가져옵니다. [GetServer를](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) 호출하면 이 인터페이스를 반환할 수도 있습니다. 이 인터페이스는 사용자 지정 포트 공급자가 서버(로컬 또는 원격)에서 프로그램을 시작하는 데 가장 자주 사용됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetServer이름](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|서버 이름을 검색합니다.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|친숙한 버전의 서버 이름을 검색합니다.|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|특정 디버그 엔진이 프로세스가 시작될 때 프로세스에 자동으로 연결하도록 지시합니다.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|자동 연결이 실패할 때 특정 오류 코드를 검색합니다.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|서버에서 디버그 엔진의 인스턴스를 만듭니다.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|서버가 호출자와 동일한 컴퓨터에 있는지 여부를 나타내는 플래그를 검색합니다.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|서버와 통신하는 데 사용되는 프로토콜을 나타내는 값을 검색합니다.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|이 서버가 알고 있는 모든 디버그 엔진에 대한 모든 자동 연결 설정을 비활성화합니다.|

## <a name="remarks"></a>설명
 사용자 지정 포트 공급자는 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)에 대한 호출시 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스를 수신합니다. 인터페이스는 `IDebugCoreServer3` 해당 인터페이스에서 가져올 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
