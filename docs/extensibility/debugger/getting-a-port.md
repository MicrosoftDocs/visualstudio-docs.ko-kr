---
title: 항구 얻기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738635"
---
# <a name="get-a-port"></a>포트 받기
포트는 프로세스가 실행 중인 컴퓨터에 대한 연결을 나타냅니다. 해당 컴퓨터는 로컬 컴퓨터 또는 원격 컴퓨터일 수 있습니다(Windows 기반이 아닌 운영 체제를 실행중일 수 있으며 자세한 내용은 [포트](../../extensibility/debugger/ports.md) 참조).

포트는 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스로 표시됩니다. 포트가 연결된 컴퓨터에서 실행되는 프로세스에 대한 정보를 얻는 데 사용됩니다.

디버그 엔진은 포트에 프로그램 노드를 등록하고 프로세스 정보에 대한 요청을 충족하기 위해 포트에 액세스해야 합니다. 예를 들어 디버그 엔진이 [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스를 구현하는 경우 [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 메서드에 대한 구현에서 포트에 반환할 필요한 프로세스 정보를 요청할 수 있습니다.

Visual Studio는 디버그 엔진에 필요한 포트를 공급하고 포트 공급자로부터 이 포트를 가져옵니다. 프로그램이 (디버거 내에서 또는 예외로 인해 Throw된 경우, Just-In-Time [JIT] 대화 상자)에 연결된 경우, 사용자는 전송(포트 공급자의 다른 이름)을 선택할 수 있습니다. 그렇지 않으면 사용자가 디버거 내에서 프로그램을 시작하면 프로젝트 시스템에서 포트 공급자가 사용하도록 지정합니다. 두 경우 모두 Visual Studio는 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스로 표시되는 포트 공급자를 인스턴스화하고 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 인터페이스를 사용하여 [AddPort를](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 호출하여 새 포트를 요청합니다. 그런 다음 이 포트는 한 가지 형태로 디버그 엔진에 전달됩니다.

## <a name="example"></a>예제
이 코드 조각은 [LaunchSuspended에](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 제공된 포트를 사용하여 [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)에서 프로그램 노드를 등록하는 방법을 보여 주며 있습니다. 이 개념과 직접 관련이 없는 매개 변수는 명확성을 위해 생략되었습니다.

> [!NOTE]
> 이 예제에서는 포트를 사용하여 프로세스를 시작하고 다시 시작하고 [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) 인터페이스가 포트에서 구현된다고 가정합니다. 이것은 결코 이러한 작업을 수행 하는 유일한 방법은, 그리고 포트도 그것에 게 주어진 프로그램의 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 를 가지고 이외의 관여 되지 않을 수 있습니다.

```cpp
// This is an IDebugEngineLaunch2 method.
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                      IDebugPort2 *pPort,
                                      /* omitted parameters */,
                                      IDebugProcess2**ppDebugProcess)
{
    // do stuff here to set up for a launch (such as handling the other parameters)
    ...

    // Now get the IPortNotify2 interface so we can register a program node
    // in CDebugEngine::ResumeProcess.
    CComPtr<IDebugDefaultPort2> spDefaultPort;
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);
    if (SUCCEEDED(hr))
    {
        CComPtr<IDebugPortNotify2> spPortNotify;
        hr = spDefaultPort->GetPortNotify(&spPortNotify);
        if (SUCCEEDED(hr))
        {
            // Remember the port notify so we can use it in ResumeProcess.
            m_spPortNotify = spPortNotify;

            // Now launch the process in a suspended state and return the
            // IDebugProcess2 interface
            CComPtr<IDebugPortEx2> spPortEx;
            hr = pPort->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                // pass on the parameters we were given (omitted here)
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
            }
        }
    }
    return(hr);
}

HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
{
    // Make a program node for this process
    HRESULT hr;
    CComPtr<IDebugProgramNode2> spProgramNode;
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
    if (SUCCEEDED(hr))
    {
        hr = m_spPortNotify->AddProgramNode(spProgramNode);
        if (SUCCEEDED(hr))
        {
            // resume execution of the process using the port given to us earlier.
            // (Querying for the IDebugPortEx2 interface is valid here since
            // that's how we got the IDebugPortNotify2 interface in the first place.)
            CComPtr<IDebugPortEx2> spPortEx;
            hr = m_spPortNotify->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>참조
- [프로그램 등록](../../extensibility/debugger/registering-the-program.md)
- [프로그램을 디버깅할 수 있도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [항구 공급업체](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)
