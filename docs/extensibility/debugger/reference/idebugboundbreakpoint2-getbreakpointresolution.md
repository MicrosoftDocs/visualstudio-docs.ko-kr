---
title: 'IDebugBoundBreakpoint2:: Get Pointresolution | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51912fce3bf98502be7ae05f815fce60e595e89c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887343"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
이 중단점을 설명 하는 중단점 확인을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

## <a name="parameters"></a>매개 변수
`ppBPResolution`\
제한이 다음 중 하나를 나타내는 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 인터페이스를 반환 합니다.

- 코드 중단점이 바인딩된 코드의 위치를 설명 하는 중단점 확인 개체입니다.

- 데이터 중단점이 바인딩된 데이터 위치입니다.

## <a name="return-value"></a>Return Value
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_BP_DELETED`바인딩된 중단점 개체의 상태가 `BPS_DELETED` ( [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 열거의 일부)로 설정 되어 있으면를 반환 합니다.

## <a name="remarks"></a>설명
[Get간 Pointtype](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) 메서드를 호출 하 여 코드 또는 데이터에 대 한 중단점 확인이 있는지 확인 합니다.

## <a name="example"></a>예제
다음 예제에서는 `CBoundBreakpoint` [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 인터페이스를 노출 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>참고 항목
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
