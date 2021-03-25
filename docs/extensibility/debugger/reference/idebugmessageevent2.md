---
description: 이 인터페이스는 디버그 엔진 (DE)에서 사용자의 응답이 필요한 Visual Studio로 메시지를 보내는 데 사용 됩니다.
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5593e822b974ddb7c666f622192e3e4630b7222
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058432"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
이 인터페이스는 디버그 엔진 (DE)에서 사용자의 응답이 필요한 Visual Studio로 메시지를 보내는 데 사용 됩니다.

## <a name="syntax"></a>구문

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE는이 인터페이스를 구현 하 여 사용자 응답이 필요한 Visual Studio로 메시지를 보냅니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는이 인터페이스와 동일한 개체에서 구현 되어야 합니다. SDM은 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 `IDebugEvent2` 인터페이스에 액세스 합니다.

 이 인터페이스의 구현은 Visual Studio의 [Setresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) 호출을 DE에 전달 해야 합니다. 예를 들어 DE의 메시지 처리 스레드에 게시 된 메시지를 사용 하 여이 작업을 수행 하거나,이 인터페이스를 구현 하는 개체에서 DE에 대 한 참조를 보유 하 고에 전달 된 응답을 사용 하 여 DE로 콜백할 수 있습니다 `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>호출자 참고 사항
 DE는 응답을 요구 하는 사용자에 게 메시지를 표시 하기 위해이 이벤트 개체를 만들어 보냅니다. 이벤트는 디버깅 중인 프로그램에 연결 될 때 SDM에서 제공 하는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 콜백 함수를 사용 하 여 보냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugMessageEvent2` .

|메서드|Description|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|표시할 메시지를 가져옵니다.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|메시지 상자에서 응답을 설정 합니다 (있는 경우).|

## <a name="remarks"></a>설명
 특정 메시지에 대 한 사용자의 특정 응답이 필요한 경우 DE는이 인터페이스를 사용 합니다. 예를 들어, 프로그램에 원격으로 연결 하려고 시도 하 고 나 서 "액세스가 거부 되었습니다." 메시지가 표시 되는 경우 DE는 `IDebugMessageEvent2` 메시지 상자 스타일이 있는 이벤트에서이 특정 메시지를 Visual Studio로 보냅니다 `MB_RETRYCANCEL` . 이를 통해 사용자는 연결 작업을 다시 시도 하거나 취소할 수 있습니다.

 DE는 Win32 함수의 규칙에 따라이 메시지를 처리 하는 방법을 지정 합니다 `MessageBox` (자세한 내용은 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) 참조).

 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 인터페이스를 사용 하 여 사용자의 응답이 필요 없는 Visual Studio로 메시지를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
