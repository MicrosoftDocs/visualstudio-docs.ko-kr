---
title: 아이데버그메시지이벤트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727367"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
이 인터페이스는 DE(디버그 엔진)에서 사용자의 응답이 필요한 메시지를 Visual Studio에 보내는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 사용자 응답이 필요한 메시지를 Visual Studio에 보내기 위해 이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 이 인터페이스와 동일한 개체에서 구현되어야 합니다. SDM은 [쿼리인터페이스를](/cpp/atl/queryinterface) 사용하여 `IDebugEvent2` 인터페이스에 액세스합니다.

 이 인터페이스의 구현은 DE에 대한 Visual Studio의 [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) 호출을 전달해야 합니다. 예를 들어, 이 작업은 DE의 메시지 처리 스레드에 게시된 메시지로 수행하거나 이 인터페이스를 구현하는 개체가 DE에 대한 참조를 `IDebugMessageEvent2::SetResponse`보유하고 에 전달된 응답으로 DE로 다시 호출할 수 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 DE는 이 이벤트 개체를 만들고 보내 응답이 필요한 메시지를 사용자에게 표시합니다. 이 이벤트는 디버깅되는 프로그램에 연결될 때 SDM에서 제공하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용하여 전송됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugMessageEvent2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|표시할 메시지를 가져옵니다.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|메시지 상자에서 응답을 설정합니다(있는 경우).|

## <a name="remarks"></a>설명
 DE는 특정 메시지에 대한 사용자의 특정 응답이 필요한 경우 이 인터페이스를 사용합니다. 예를 들어 DE가 프로그램에 원격으로 연결하려고 시도한 후 "액세스 거부" 메시지를 받는 경우 DE는 메시지 `IDebugMessageEvent2` 상자 스타일이 `MB_RETRYCANCEL`있는 이벤트에서 이 특정 메시지를 Visual Studio로 보냅니다. 이렇게 하면 사용자가 연결 작업을 다시 시도하거나 취소할 수 있습니다.

 DE는 Win32 함수의 `MessageBox` 규칙을 따라 이 메시지를 처리하는 방법을 지정합니다(자세한 내용은 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) 참조).

 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 인터페이스를 사용하여 사용자의 응답이 필요하지 않은 메시지를 Visual Studio로 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
