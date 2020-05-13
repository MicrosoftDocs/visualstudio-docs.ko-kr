---
title: BP_STATE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2721028c0635af274174574e4a264546c1909778
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737806"
---
# <a name="bp_state"></a>BP_STATE
바인딩된 중단점의 존재를 지정하고 활성화된 경우 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>필드
`BPS_NONE`\
중단점이 없음을 지정합니다.

`BPS_DELETED`\
중단점이 삭제되었음을 지정합니다.

`BPS_DISABLED`\
중단점이 비활성화되도록 지정합니다.

`BPS_ENABLED`\
중단점이 활성화되도록 지정합니다.

## <a name="remarks"></a>설명
[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) 메서드에서 반환되었습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [겟스테이트](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
