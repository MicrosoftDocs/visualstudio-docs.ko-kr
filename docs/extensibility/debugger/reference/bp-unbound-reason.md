---
title: BP_UNBOUND_REASON | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737779"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
중단점이 언바운드된 이유를 제공합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>필드
`BPUR_UNKNOWN`\
그 이유는 알 수 없습니다.

`BPUR_CODE_UNLOADED`\
중단점을 포함하는 코드가 언로드되었습니다.

`BPUR_BREAKPOINT_REBIND`\
중단점은 다른 위치로 반등했습니다. 이 문제는 중단점이 이동하거나 중단점이 더 이상 유효하지 않은 경로가 있는 파일에 바인딩된 경우 편집 및 계속 작업 후에 발생할 수 있습니다.

`BPUR_ BREAKPOINT_ERROR`\
중단점은 바인딩된 후 오류가 있는 것으로 확인됩니다. 이는 조건이 더 이상 유효하지 않은 관리중단점에 발생합니다.

## <a name="remarks"></a>설명
[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) 메서드에 의해 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
