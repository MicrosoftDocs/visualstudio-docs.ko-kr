---
description: 이 인터페이스는 프로세스가 실행 되 고 있는 서버에 대 한 정보에 액세스할 수 있도록 합니다.
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1328a97742a4672cdc71805c4c674d66fe05e817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154615"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
이 인터페이스는 프로세스가 실행 되 고 있는 서버에 대 한 정보에 액세스할 수 있도록 합니다.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스에서이 인터페이스를 가져오려면 [QueryInterface](/cpp/atl/queryinterface) 를 사용 합니다. [Getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) 에 대 한 호출 에서도이 인터페이스를 반환할 수 있습니다. 이 인터페이스는 사용자 지정 포트 공급자가 서버 (로컬 또는 원격)에서 프로그램을 시작 하는 데 가장 자주 사용 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|서버의 이름을 검색 합니다.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|친숙 한 버전의 서버 이름을 검색 합니다.|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|해당 프로세스가 시작 될 때 프로세스에 자동으로 연결 되도록 특정 디버그 엔진에 지시 합니다.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|자동 연결이 실패 하는 경우 특정 오류 코드를 검색 합니다.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|서버에 디버그 엔진의 인스턴스를 만듭니다.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|서버가 호출자와 동일한 컴퓨터에 있는지 여부를 나타내는 플래그를 검색 합니다.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|서버와 통신 하는 데 사용 되는 프로토콜을 나타내는 값을 검색 합니다.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|이 서버에서 인식 하는 모든 디버그 엔진의 자동 연결 설정을 모두 사용 하지 않도록 설정 합니다.|

## <a name="remarks"></a>설명
 사용자 지정 포트 공급자는 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)호출에서 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스를 수신 합니다. 인터페이스 `IDebugCoreServer3` 에서 인터페이스를 가져올 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
