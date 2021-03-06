---
description: 이 이벤트에 바인딩된 중단점의 열거자를 만듭니다.
title: 'IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62163e1f15efd39014c3000d77a843057b40a3fa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088746"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
이 이벤트에 바인딩된 중단점의 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumBoundBreakpoints( 
    IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
    out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 이 이벤트에서 바인딩된 모든 중단점을 열거 하는 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
성공하면 `S_OK`를 반환합니다. `S_FALSE`바인딩된 중단점이 없으면를 반환 하 고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
바인딩된 중단점의 목록은이 이벤트에 바인딩된 것 이며 보류 중인 중단점에서 바인딩된 중단점의 전체 목록이 아닐 수 있습니다. 보류 중인 중단점에 바인딩된 모든 중단점 목록을 가져오려면 [Getpendingbreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 메서드를 호출 하 여 연결 된 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 개체를 가져온 다음 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) 메서드를 호출 하 여 보류 중인 중단점에 대 한 바인딩된 모든 중단점을 포함 하는 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 개체를 가져옵니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 인터페이스를 노출 하는 **Cbreakpointsetdebugeventbase** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(
    IEnumDebugBoundBreakpoints2 **ppEnum)
{
    HRESULT hRes = E_FAIL;

    if ( ppEnum )
    {
        if ( m_pEnumBound )
        {
            hRes = m_pEnumBound->Clone(ppEnum);

            if ( EVAL(S_OK == hRes) )
                (*ppEnum)->Reset();
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>참조
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
