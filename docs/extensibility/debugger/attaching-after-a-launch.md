---
title: 시작 후 연결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739289"
---
# <a name="attach-after-a-launch"></a>시작 후 연결
프로그램이 시작 된 후 디버그 세션은 디버그 엔진 (DE)을 프로그램에 연결할 준비가 된 것입니다.

## <a name="design-decisions"></a>디자인 결정
 공유 주소 공간 내에서 통신이 더 쉽기 때문에 두 가지 디자인 방법, 즉 디버그 세션과 DE 간의 통신 설정을 선택 해야 합니다. 또는 DE와 프로그램 간의 통신을 설정 합니다. 다음 중에서 선택 합니다.

- 디버그 세션과 DE 사이에 통신을 설정 하는 것이 더 적합 한 경우 디버그 세션은 DE를 공동 생성 하 고 DE를 프로그램에 연결 하 라는 메시지를 표시 합니다. 이 디자인은 디버그 세션을 한 주소 공간으로 유지 하 고 런타임 환경 및 프로그램을 다른 주소 공간으로 함께 유지 합니다.

- DE와 프로그램 간의 통신을 설정 하는 것이 더 적합할 경우 런타임 환경에서 DE를 공동 만듭니다. 이 디자인은 SDM을 하나의 주소 공간 및 DE-DE, 런타임 환경 및 프로그램으로 함께 유지 합니다. 이 디자인은 스크립트 언어를 실행 하기 위해 인터프리터를 사용 하 여 구현 되는 일반적인 DE입니다.

    > [!NOTE]
    > 프로그램에 대 한 연결 해제는 구현에 따라 다릅니다. DE와 프로그램 간의 통신도 구현에 따라 달라 집니다.

## <a name="implementation"></a>구현
 프로그래밍 방식으로 실행 될 프로그램을 나타내는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 개체를 먼저 수신 하는 경우에는 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) 메서드를 호출 하 여 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 개체를 전달 합니다 .이 개체는 나중에 디버그 이벤트를 다시 SDM에 전달 하는 데 사용 됩니다. `IDebugProgram2::Attach`그런 다음 메서드는 [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출 합니다. SDM에서 인터페이스를 수신 하는 방법에 대 한 자세한 내용은 `IDebugProgram2` [포트에 알림](../../extensibility/debugger/notifying-the-port.md)을 참조 하세요.

 디버깅 하는 프로그램과 동일한 주소 공간에서 DE를 실행 해야 하는 경우: DE는 일반적으로 스크립트를 실행 하는 인터프리터의 일부 이기 때문에 메서드는를 `IDebugProgramNodeAttach2::OnAttach` 반환 `S_FALSE` 합니다. `S_FALSE`반환은 연결 프로세스를 완료 했음을 나타냅니다.

 그러나 DE가 SDM의 주소 공간에서 실행 되는 경우: `IDebugProgramNodeAttach2::OnAttach` 메서드가 반환 `S_OK` 되거나, 디버깅 중인 프로그램에 연결 된 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 개체에 대해 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스가 구현 되지 않습니다. 이 경우 [attach 메서드를 호출 하 여 연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 작업을 완료 합니다.

 후자의 경우에는 메서드에 전달 된 개체에서 [get프로그래밍할 id](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 호출 하 고 `IDebugProgram2` `IDebugEngine2::Attach` , `GUID` 로컬 프로그램 개체에를 저장 하 고, `GUID` `IDebugProgram2::GetProgramId` 이 개체에 대해 메서드가 호출 될 때이를 반환 해야 합니다. 는 `GUID` 다양 한 디버그 구성 요소에서 프로그램을 고유 하 게 식별 하는 데 사용 됩니다.

 메서드가를 반환 하는 경우 `IDebugProgramNodeAttach2::OnAttach` `S_FALSE` `GUID` 프로그램에 사용할는 해당 메서드로 전달 되 고 `IDebugProgramNodeAttach2::OnAttach` `GUID` 로컬 프로그램 개체에 대해를 설정 하는 메서드입니다.

 이제 DE가 프로그램에 연결 되 고 시작 이벤트를 보낼 준비가 되었습니다.

## <a name="see-also"></a>추가 정보
- [프로그램에 직접 연결](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [포트에 알림](../../extensibility/debugger/notifying-the-port.md)
- [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [연결](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [연결](../../extensibility/debugger/reference/idebugengine2-attach.md)
