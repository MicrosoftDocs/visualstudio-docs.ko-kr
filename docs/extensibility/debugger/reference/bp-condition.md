---
description: 중단점이 발생 하는 조건을 설명 합니다.
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 560cf7184e5fa7b25e35410313535675713742aa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085340"
---
# <a name="bp_condition"></a>BP_CONDITION
중단점이 발생 하는 조건을 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>멤버
`pThread`\
중단점을 포함 하는 응용 프로그램에 대 한 활성 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

`styleCondition`\
이 중단점 조건의 스타일을 설명 하는 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) 열거형의 값입니다.

`bstrContext`\
중단점의 위치입니다.

`bstrCondition`\
중단점의 발생 조건입니다.

`nRadix`\
숫자 정보를 평가 하는 데 사용할 기 수입니다.

## <a name="remarks"></a>설명
이 구조는 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조체의 멤버입니다.

이 구조체는 [setcondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) 및 [setcondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) 메서드에 매개 변수로도 전달 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
