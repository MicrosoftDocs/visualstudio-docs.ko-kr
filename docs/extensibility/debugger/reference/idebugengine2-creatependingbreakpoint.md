---
title: IDebugEngine2:생성보류 중단점 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731122"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
DE(디버그 엔진)에서 보류 중인 중단점을 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>매개 변수
`pBPRequest`\
【인】 만들 보류 중인 중단점을 설명하는 [IDebug중단점Request2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 개체입니다.

`ppPendingBP`\
【아웃】 보류 중인 중단점을 나타내는 [IDebugPending중단점2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 일반적으로 `E_FAIL` 매개 `pBPRequest` 변수가 DE에서 지원하는 언어와 일치하지 `pBPRequest` 않는 경우 매개 변수가 유효하지 않거나 불완전한 경우 반환됩니다.

## <a name="remarks"></a>설명
보류 중인 중단점은 기본적으로 중단점을 코드에 바인딩하는 데 필요한 모든 정보의 모음입니다. 이 메서드에서 반환 되는 보류 중인 중단점은 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 메서드가 호출될 때까지 코드에 바인딩되지 않습니다.

사용자가 설정하는 각 보류 중인 중단점에 대해 세션 디버그 관리자(SDM)는 연결된 각 DE에서 이 메서드를 호출합니다. 해당 DE에서 실행 중인 프로그램에 대해 중단점이 유효한지 확인하는 것은 DE의 책임이 있습니다.

사용자가 코드 줄에 중단점을 설정하면 DE는 이 코드에 해당하는 문서의 가장 가까운 줄에 중단점을 자유롭게 바인딩할 수 있습니다. 이렇게 하면 사용자가 다중 줄 문의 첫 번째 줄에 중단점을 설정할 수 있지만 마지막 줄에 바인딩할 수 있습니다(모든 코드가 디버그 정보에 기인하는 경우).

## <a name="example"></a>예제
다음 예제에서는 간단한 `CProgram` 개체에 대해 이 메서드를 구현하는 방법을 보여 주습니다. DE의 구현은 `IDebugEngine2::CreatePendingBreakpoint` 각 프로그램에서 메서드의 이 구현에 대한 모든 호출을 전달할 수 있습니다.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [바인딩](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
