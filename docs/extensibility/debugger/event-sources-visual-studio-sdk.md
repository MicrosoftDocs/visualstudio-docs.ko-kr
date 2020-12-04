---
title: 이벤트 소스 (Visual Studio SDK) | Microsoft Docs
description: Visual Studio 디버깅에서 디버그 엔진과 세션 디버그 관리자의 두 이벤트 소스에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], event sources
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ab0bc2bb61069e20276c471d1245d167715cc7a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559669"
---
# <a name="event-sources-visual-studio-sdk"></a>이벤트 소스 (Visual Studio SDK)
이벤트에는 디버그 엔진 (DE)과 세션 디버그 관리자 (SDM)의 두 가지 소스가 있습니다. DE에서 전송 된 이벤트에 NULL이 아닌 엔진이 있으며,이 경우 SDM에서 전송 된 이벤트에는 NULL 엔진이 있습니다.

## <a name="example"></a>예제
다음 예제에서는 **IDebugProgramCreateEvent2** 를 DE에서 SDM으로 보내는 방법을 보여 줍니다.

```csharp
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))
{
    // Handle failure here.
}
]

CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);

HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {
    HRESULT hr;

    if (m_dwAttrib & EVENT_STOPPING)
    {
        hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);
    }
    else if (m_dwAttrib & EVENT_SYNCHRONOUS)
    {
        hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }
    else
    {
        assert(m_dwAttrib == 0);
        hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }

    return hr;
}

HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {

    HRESULT hr;

    // Make sure the CEvent object running this code is not deleted until the code completes.
    AddRef();

    pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);

    // No error recovery here.
    hr = S_OK;

    Release();
    return hr;
}

```

## <a name="see-also"></a>참고 항목
- [이벤트 전송](../../extensibility/debugger/sending-events.md)
