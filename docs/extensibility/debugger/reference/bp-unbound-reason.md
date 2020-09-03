---
title: BP_UNBOUND_REASON | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737779"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
중단점이 바인딩 해제 된 이유를 제공 합니다.

## <a name="syntax"></a>Syntax

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
원인을 알 수 없습니다.

`BPUR_CODE_UNLOADED`\
중단점이 포함 된 코드가 언로드 되었습니다.

`BPUR_BREAKPOINT_REBIND`\
중단점이 다른 위치에 바인딩 되었습니다. 이는 중단점이 이동할 때 편집 하며 계속 하기 작업 후에 발생할 수 있으며, 더 이상 유효 하지 않은 경로를 사용 하 여 중단점을 파일에 바인딩할 때 발생할 수 있습니다.

`BPUR_ BREAKPOINT_ERROR`\
중단점은 바인딩된 후에 오류가 있는 것으로 확인 됩니다. 이는 해당 조건이 더 이상 유효 하지 않은 관리 되는 중단점에 발생 합니다.

## <a name="remarks"></a>설명
[Getreason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) 메서드에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
