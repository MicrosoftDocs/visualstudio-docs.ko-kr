---
title: 포트 가져오기 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738635"
---
# <a name="get-a-port"></a>포트 가져오기
포트는 프로세스가 실행 중인 컴퓨터에 대 한 연결을 나타냅니다. 이 컴퓨터는 로컬 컴퓨터 또는 원격 컴퓨터 일 수 있습니다. 즉, Windows 기반이 아닌 운영 체제를 실행할 수 있습니다. 자세한 내용은 [포트](../../extensibility/debugger/ports.md) 를 참조 하십시오.

포트는 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스로 표시 됩니다. 포트가 연결 된 컴퓨터에서 실행 중인 프로세스에 대 한 정보를 가져오는 데 사용 됩니다.

디버그 엔진은 포트에 프로그램 노드를 등록 하 고 프로세스 정보에 대 한 요청을 충족 하기 위해 포트에 액세스 해야 합니다. 예를 들어 디버그 엔진이 [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스를 구현 하는 경우 [Getproviderprocessdata](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 메서드에 대 한 구현에서 필요한 프로세스 정보를 반환 하도록 포트에 요청할 수 있습니다.

Visual Studio는 필요한 포트를 디버그 엔진에 제공 하 고 포트 공급자에서이 포트를 가져옵니다. 프로그램이에 연결 되어 있는 경우 (디버거 내에서 또는 예외가 throw 되어 Just-in-time [JIT] 대화 상자를 트리거) 사용자에 게 사용할 전송 선택 (포트 공급자의 다른 이름)이 제공 됩니다. 그렇지 않고 사용자가 디버거 내에서 프로그램을 시작 하는 경우 프로젝트 시스템은 사용할 포트 공급자를 지정 합니다. 어느 경우 든 Visual Studio는 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스로 표시 되는 포트 공급자를 인스턴스화하고 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 인터페이스를 사용 하 여 [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 를 호출 하 여 새 포트를 요청 합니다. 그런 다음이 포트는 디버그 엔진에 한 형식 또는 다른 형식으로 전달 됩니다.

## <a name="example"></a>예
이 코드 조각에서는 [Launchsuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 에 제공 된 포트를 사용 하 여 [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)에 프로그램 노드를 등록 하는 방법을 보여 줍니다. 명확 하 게 하기 위해이 개념과 직접 관련 되지 않은 매개 변수는 생략 되었습니다.

> [!NOTE]
> 이 예제에서는 포트를 사용 하 여 프로세스를 시작 하 고 다시 시작 하며 [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) 인터페이스가 포트에서 구현 된 것으로 가정 합니다. 이는 이러한 작업을 수행 하는 유일한 방법 이며, 포트가 지정 된 프로그램의 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 을 포함 하지 않을 수도 있습니다.

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

## <a name="see-also"></a>추가 정보
- [프로그램 등록](../../extensibility/debugger/registering-the-program.md)
- [프로그램을 디버그할 수 있도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [포트 공급자](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)
