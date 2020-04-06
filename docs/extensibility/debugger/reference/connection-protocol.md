---
title: CONNECTION_PROTOCOL | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737642"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
디버그 서버와 DE(디버그 패키지) 간에 통신하는 데 사용되는 프로토콜을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>필드
`CONNECTION_NONE`\
서버에 연결되지 않았습니다.

`CONNECTION_UNKNOWN`\
연결이 되었지만 알 수 없는 형식입니다.

`CONNECTION_LOCAL`\
로컬 서버에 연결됩니다.

`CONNECTION_PIPE`\
연결은 명명된 파이프를 통해 입니다.

`CONNECTION_TCPIP`\
연결은 TCP/IP를 사용합니다.

`CONNECTION_HTTP`\
연결은 웹 서버를 통해 HTTP를 사용합니다.

`CONNECTION_OTHER`\
일부 다른 유형의 연결이 설정되었습니다(이 값은 현재 사용되지 않음).

## <a name="remarks"></a>설명
이러한 값은 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) 메서드에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
