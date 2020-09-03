---
title: 프로그램 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b68fa67f784d155288482ad724b632ed5ba5fa41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713165"
---
# <a name="register-the-program"></a>프로그램 등록
디버그 엔진이 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스로 표시 되는 포트를 가져온 후 프로그램을 디버그할 수 있도록 하는 다음 단계는 포트에 등록 하는 것입니다. 등록 된 프로그램은 다음 방법 중 하나를 사용 하 여 디버그할 수 있습니다.

- 디버거가 실행 중인 응용 프로그램의 완전 한 디버깅 제어를 얻을 수 있도록 하는 연결 프로세스입니다.

- JIT (just-in-time) 디버깅-디버거를 독립적으로 실행 하는 프로그램의 사후 디버깅을 허용 합니다. 런타임 아키텍처에서 오류를 catch 하는 경우 운영 체제 또는 런타임 환경에서 오류가 발생 한 프로그램의 메모리와 리소스를 해제 하기 전에 디버거가 알림이 표시 됩니다.

## <a name="registering-procedure"></a>프로시저 등록

### <a name="to-register-your-program"></a>프로그램을 등록 하려면

1. 포트에서 구현한 [Add프로그램 노드](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 메서드를 호출 합니다.

     `IDebugPortNotify2::AddProgramNode`[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스에 대 한 포인터가 필요 합니다.

     일반적으로 운영 체제 또는 런타임 환경에서는 프로그램을 로드할 때 프로그램 노드를 만듭니다. 디버그 엔진 (DE)에 프로그램을 로드 하 라는 메시지가 표시 되 면 DE는 프로그램 노드를 만들고 등록 합니다.

     다음 예제에서는 프로그램을 시작 하 고 포트에 등록 하는 디버그 엔진을 보여 줍니다.

    > [!NOTE]
    > 이 코드 샘플은 프로세스를 시작 하 고 다시 시작 하는 유일한 방법은 아닙니다. 이 코드는 주로 포트를 사용 하 여 프로그램을 등록 하는 예제입니다.

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
                    hr  = spPortEx->ResumeProcess(pDebugProcess);
                }
            }
        }
        return(hr);
    }

    ```

## <a name="see-also"></a>추가 정보
- [포트 가져오기](../../extensibility/debugger/getting-a-port.md)
- [프로그램을 디버그할 수 있도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
