---
title: 아이디버그프로그램제공자2::워치포퍼리제공자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
helpviewer_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
ms.assetid: 2eb93653-b5fb-45b6-b136-56008c5d25ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a48e082556cf96a35ed83afd5008d3240e600b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721755"
---
# <a name="idebugprogramprovider2watchforproviderevents"></a>IDebugProgramProvider2::WatchForProviderEvents
프로세스에 포트 이벤트에 대한 알림을 받을 수 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WatchForProviderEvents(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   CONST_GUID_ARRAY     EngineFilter,
   REFGUID              guidLaunchingEngine,
   IDebugPortNotify2*   pEventCallback
);
```

```csharp
int WatchForProviderEvents(
   enum_PROVIDER_FLAGS   Flags,
   IDebugDefaultPort2    pPort,
   AD_PROCESS_ID         ProcessId,
   CONST_GUID_ARRAY      EngineFilter,
   ref Guid              guidLaunchingEngine,
   IDebugPortNotify2     pEventCallback
);
```

## <a name="parameters"></a>매개 변수
`Flags`\
【인】 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 열거형의 플래그 조합입니다. 다음 플래그는 이 호출의 일반적인 플래그입니다.

|플래그|설명|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|호출기가 원격 컴퓨터에서 실행되고 있습니다.|
|`PFLAG_DEBUGGEE`|호출자는 현재 디버깅 중입니다(각 노드에 대해 마샬링에 대한 추가 정보가 반환됨).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|호출자가 연결되었지만 디버거에 의해 시작되지 않았습니다.|
|`PFLAG_REASON_WATCH`|발신자는 이벤트를 감시하려고 합니다. 이 플래그가 설정되지 않은 경우. 그런 다음 콜백 이벤트가 제거되고 호출자는 더 이상 알림을 받지 않습니다.|

`pPort`\
【인】 호출 프로세스가 실행 중인 포트입니다.

`processId`\
【인】 해당 프로그램이 포함된 프로세스의 ID를 보유한 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조입니다.

`EngineFilter`\
【인】 프로세스와 관련된 디버그 엔진의 GUID 배열입니다.

`guidLaunchingEngine`\
【인】 이 프로세스를 시작한 디버그 엔진의 GUID(있는 경우)입니다.

`pEventCallback`\
【인】 이벤트 알림을 받는 [IDebugPortNotify2 개체입니다.](../../../extensibility/debugger/reference/idebugportnotify2.md)

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 호출자가 이 메서드에 대한 이전 호출로 설정된 이벤트 처리기를 제거하려고 하면 호출자는 처음 했던 것과 동일한 `PFLAG_REASON_WATCH` 매개 변수를 전달하지만 플래그에서 벗어납니다.

## <a name="example"></a>예제
 다음 예제에서는 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스를 노출 하는 **CDebugEngine** 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CDebugEngine::WatchForProviderEvents(
    PROVIDER_FLAGS Flags,
    IDebugDefaultPort2 *pPort,
    AD_PROCESS_ID processId,
    CONST_GUID_ARRAY EngineFilter,
    REFGUID guidLaunchingEngine,
    IDebugPortNotify2 *pPortNotify)
{
    HRESULT hRes = E_FAIL;

    if (EVAL(pPort != NULL) && EVAL(pPortNotify != NULL))
    {
        // We will only watch/send events about the process if the debugger
        // is actually debugging the process, and only if this is an attach or a LoRIE launch
        if (IsFlagSet(Flags, PFLAG_DEBUGGEE) &&
            guidLaunchingEngine == GUID_NULL &&
            processId.ProcessIdType == AD_PROCESS_ID_SYSTEM)
        {
            // We don't support WatchForProviderEvents when in interop mode
            if (m_fInterop)
            {
                ASSERT(!"Shouldn't ever be called in interop mode");
                hRes = E_FAIL;
            }
            else
            {
                if (IsFlagSet(Flags, PFLAG_REASON_WATCH))
                {
                    // QI to get IDebugEventCallback2 which is required.
                    CComQIPtr<IDebugEventCallback2> pCallback(pPortNotify);

                    ASSERT(pCallback != NULL);
                    if ( pCallback != NULL )
                    {
                        // Register the callback
                        hRes = this->InitDebugSession(pCallback);

                        if ( S_OK == hRes )
                        {
                            // Get the IDebugProcess2 from the port and call AttachImpl
                            CComPtr<IDebugProcess2> spProcess;

                            hRes = pPort->GetProcess(processId, &spProcess);

                            if (HREVAL(S_OK, hRes))
                            {
                                hRes = AttachImpl(spProcess, NULL, NULL, processId.ProcessId.dwProcessId, ATTACH_REASON_USER, NULL);

                                if ( FAILED(hRes) && (!m_pPidList || 0 == m_pPidList->GetCount()) )
                                    this->Cleanup();
                            }
                        }
                        else
                            this->Cleanup();
                    }
                    else
                        hRes = E_FAIL;
                }
                else
                {
                    // Detach will be done by SDM calling on programs directly if there are managed programs.

                    // This handling is the case where no managed code ever ran.
                    if ( this->IsProcessBeingDebugged(processId.ProcessId.dwProcessId) )
                    {
                        ProgramList *pProgList = this->GetProgramListCopy();

                        if ( EVAL(pProgList) )
                        {
                            if ( pProgList->GetCount() == 0)
                            {
                                CComPtr<ICorDebugProcess> pCorProcess;

                                hRes = this->GetCorProcess(processId.ProcessId.dwProcessId, &pCorProcess);

                                if (HREVAL(S_OK, hRes) )
                                {
                                    hRes = pCorProcess->Stop(INFINITE);

                                    if ( HREVAL(S_OK, hRes) )
                                        hRes = pCorProcess->Detach();
                                }

                                // Tell the engine that it should unregister this process from com+
                                this->UnregisterProcess(processId.ProcessId.dwProcessId);

                                // If there are no more pids left then cleanup everything.
                                if ( 0 == m_pPidList->GetCount() )
                                    this->Cleanup();
                            }
                            // This is needed for cases where the SDM has not yet received program create
                            // by the time that we need to detach (example: the managed attach succeeds,
                            // but some other attach step fails).
                            else
                            {
                                PROGNODE *pProgNode = NULL;
                                while ( pProgNode = pProgList->Next(pProgNode) )
                                {
                                    CDebugProgram * pProgram = ((CDebugProgram *)pProgNode->data);
                                    hRes = pProgram->Detach();
                                }
                            }

                            delete pProgList;
                        }
                    }
                    else
                        hRes = S_OK;
                }
            }
        }
        else
        {
            hRes = S_FALSE;
        }
    }
    else
    {
        hRes = E_INVALIDARG;
    }

    return hRes;
}
```

## <a name="see-also"></a>참조
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
