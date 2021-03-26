---
description: 중단점이 코드 위치에 있는지, 데이터 위치에 있는지 또는 다른 중단점 형식 인지를 지정 합니다.
title: BP_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23f7b6c42b1c4736ba0eb76a451bb91e74ca5ff5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089097"
---
# <a name="bp_type"></a>BP_TYPE
중단점이 코드 위치에 있는지, 데이터 위치에 있는지 또는 다른 중단점 형식 인지를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>필드
`BPT_NONE`\
중단점 형식을 지정 하지 않습니다.

`BPT_CODE`\
코드 중단점을 지정 합니다.

`BPT_DATA`\
데이터 중단점을 지정 합니다.

`BPT_SPECIAL`\
코드와 데이터 형식이 아닌 중단점을 지정 합니다. 이 형식은 더 이상 사용 되지 않으므로 사용 하면 안 됩니다.

## <a name="remarks"></a>설명
[Get간 pointtype](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) 및 [getto pointtype](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) 메서드에 매개 변수로 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
