---
title: IDebugPending중단점2::가상화 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Virtualize
helpviewer_keywords:
- Virtualize method
- IDebugPendingBreakpoint2::Virtualize method
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ad5aac997cf694a7cf8fa887ae63fbef54ca07f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725662"
---
# <a name="idebugpendingbreakpoint2virtualize"></a>IDebugPendingBreakpoint2::Virtualize
이 보류 중인 중단점의 가상화 상태를 전환합니다. 보류 중인 중단점이 가상화되면 디버그 엔진은 새 코드가 프로그램에 로드될 때마다 바인딩을 시도합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Virtualize(
    BOOL fVirtualize
);
```

```cpp
int Virtualize(
    int fVirtualize
);
```

## <a name="parameters"></a>매개 변수
`fVirtualize`\
【인】 보류 중인 중단점을 가상화하려면 비영(0)()으로`TRUE`설정하거나 0(0)으로`FALSE`설정하여 가상화를 해제합니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 중단점이 삭제된 경우 반환합니다. `E_BP_DELETED`

## <a name="remarks"></a>설명
가상화된 중단점은 코드가 로드될 때마다 바인딩됩니다.

## <a name="example"></a>예제
다음 예제에서는 `CPendingBreakpoint` [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스를 노출 하는 간단한 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        if (fVirtualize)
        {
            // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            SetFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
        else
        {
            // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
        hr = S_OK;
    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
