---
title: 'IDebugBreakpointUnboundEvent2:: GetBreakpoint | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
ms.assetid: ad73a207-b778-4dc5-b645-5ec668a63333
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cfc913ed80244c0f6cb323dc37a5b0faa8716b1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881024"
---
# <a name="idebugbreakpointunboundevent2getbreakpoint"></a>IDebugBreakpointUnboundEvent2::GetBreakpoint
바인딩 해제 된 중단점을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetBreakpoint(
    IDebugBoundBreakpoint2** ppBP
);
```

```csharp
int GetBreakpoint(
    out IDebugBoundBreakpoint2 ppBP
);
```

## <a name="parameters"></a>매개 변수
`ppBP`\
제한이 바인딩 해제 된 중단점을 나타내는 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) 인터페이스를 노출 하는 **CBreakpointUnboundDebugEventBase** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetBreakpoint(
    IDebugBoundBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pbp )
        {
            IDebugBoundBreakpoint2 *pibp;

            hRes = m_pbp->QueryInterface(IID_IDebugBoundBreakpoint2, (void **) & pibp);

            if ( S_OK == hRes )
                *ppbp = pibp;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>참고 항목
- [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
