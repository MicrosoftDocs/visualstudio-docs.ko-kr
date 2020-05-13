---
title: BP_FLAGS90 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738052"
---
# <a name="bp_flags90"></a>BP_FLAGS90
선택적 플래그에 대한 유효한 값을 등록합니다. 중단점을 설정할 때 추가 정보를 지정하는 데 선택적 플래그를 사용할 수 있습니다. 이 열거형은 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 열거를 확장합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>필드
`BP90_FLAG_NONE`\
중단점 플래그를 지정하지 않습니다.

`BP90_FLAG_MAP_DOCPOSITION`\
디버그 엔진(DE)이 문서 위치를 사용하여 중단점을 매핑해야 한다고 지정합니다. 이는 ASP(활성 서버 페이지)와 같은 스크립트 지향 소스 파일에 설정된 중단점에만 적용됩니다.

`BP90_FLAG_DONT_STOP`\
디버그 엔진에서 중단점을 처리해야 하지만 디버그 엔진이 궁극적으로 거기서 멈추지 않도록 지정합니다. 즉, [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 이벤트 개체를 전송하지 않아야 합니다. 이 플래그는 주로 추적 점에서 사용되도록 설계되었습니다.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
기본 디버그 엔진에서 스테핑 상태를 지워야 하는지 여부를 결정하는 데 사용됩니다. 추적 지점이 매크로를 실행하면 BP90_FLAG_DONT_STOP 설정되지 않기 때문에 BP90_FLAG_DONT_STOP 다릅니다.

## <a name="requirements"></a>요구 사항
헤더: Msdbg90.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
