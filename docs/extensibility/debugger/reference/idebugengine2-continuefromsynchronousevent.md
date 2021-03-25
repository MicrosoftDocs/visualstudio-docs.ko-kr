---
description: 이전에 디버그 엔진 (DE)에 의해 SDM에 보낸 동기 디버그 이벤트가 수신 및 처리 되었음을 나타내기 위해 SDM (세션 디버그 관리자)에 의해 호출 됩니다.
title: 'IDebugEngine2:: ContinueFromSynchronousEvent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64303d91ff9ab4743adc980bb8ee92f9bdec9345
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093888"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
이전에 디버그 엔진 (DE)에 의해 SDM에 보낸 동기 디버그 이벤트가 수신 및 처리 되었음을 나타내기 위해 SDM (세션 디버그 관리자)에 의해 호출 됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2* pEvent
);
```

```csharp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2 pEvent
);
```

## <a name="parameters"></a>매개 변수
`pEvent`\
진행 디버거가 계속 실행 되어야 하는 이전에 보낸 동기 이벤트를 나타내는 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 개체입니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
DE는 매개 변수가 나타내는 이벤트의 원본 인지 확인 해야 합니다 `pEvent` .

## <a name="example"></a>예제
다음 예제에서는 IDebugEngine2 인터페이스를 구현 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다 `CEngine` . [](../../../extensibility/debugger/reference/idebugengine2.md)

```cpp
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)
{
    HRESULT hr;

    // Create a pointer to a unique event interface defined for batch file
    // breaks.
    IAmABatchFileEvent *pBatEvent;
    // Check for successful query for the unique batch file event
    // interface.
    if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,
                                        (void **)&pBatEvent)))
    {
        // Release the result of the QI.
        pBatEvent->Release();
        // Check thread message for notification to continue.
        if (PostThreadMessage(GetCurrentThreadId(),
                              WM_CONTINUE_SYNC_EVENT,
                              0,
                              0))
        {
            hr = S_OK;
        }
        else
        {
            hr = HRESULT_FROM_WIN32(GetLastError());
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }
    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
