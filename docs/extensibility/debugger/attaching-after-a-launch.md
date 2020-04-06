---
title: 출시 후 연결 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739289"
---
# <a name="attach-after-a-launch"></a>시작 후 연결
프로그램이 실행되면 디버그 세션이 DEBug 엔진(DE)을 이 프로그램에 연결할 준비가 되었습니다.

## <a name="design-decisions"></a>설계 결정
 공유 주소 공간 내에서 통신이 더 쉬워지므로 디버그 세션과 DE 간의 통신 설정이라는 두 가지 디자인 방법 중에서 선택해야 합니다. 또는 DE와 프로그램 간의 통신을 설정합니다. 다음 중에서 선택합니다.

- 디버그 세션과 DE 간의 통신을 설정하는 것이 더 합리적이면 디버그 세션은 DE를 공동 으로 만들고 DE가 프로그램에 연결하도록 요청합니다. 이 디자인은 디버그 세션과 DE를 하나의 주소 공간에 함께 두고 런타임 환경과 프로그램을 다른 주소 공간에 함께 둡습니다.

- DE와 프로그램 간의 통신을 설정하는 것이 더 합리적이면 런타임 환경이 DE를 공동 만듭니다. 이 디자인은 SDM을 한 주소 공간에 두고 DE, 런타임 환경 및 프로그램을 다른 주소 공간에 함께 둡습니다. 이 디자인은 스크립트 언어를 실행하기 위해 인터프리터와 함께 구현되는 DE의 전형입니다.

    > [!NOTE]
    > DE가 프로그램에 연결하는 방식은 구현에 따라 다릅니다. DE와 프로그램 간의 통신도 구현에 따라 다릅니다.

## <a name="implementation"></a>구현
 프로그래밍 방식으로 세션 디버그 관리자(SDM)가 시작할 프로그램을 나타내는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 개체를 처음 수신하면 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) 메서드를 호출하여 나중에 디버그 이벤트를 SDM으로 다시 전달하는 데 사용되는 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 개체를 전달합니다. 그런 `IDebugProgram2::Attach` 다음 메서드는 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출합니다. SDM이 `IDebugProgram2` 인터페이스를 수신하는 방법에 대한 자세한 내용은 [포트 알림 참조를](../../extensibility/debugger/notifying-the-port.md)참조하십시오.

 DE가 디버깅하는 프로그램과 동일한 주소 공간에서 실행되어야 하는 경우: DE는 일반적으로 스크립트를 실행하는 인터프리터의 `IDebugProgramNodeAttach2::OnAttach` 일부이므로 메서드가 반환됩니다. `S_FALSE` 반환은 `S_FALSE` 연결 프로세스를 완료했음을 나타냅니다.

 그러나 DE가 SDM의 주소 공간에서 실행되는 경우 `IDebugProgramNodeAttach2::OnAttach` 메서드가 `S_OK`반환되거나 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스가 디버깅하는 프로그램과 연결된 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 개체에서 전혀 구현되지 않습니다. 이 경우 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드가 결국 호출되어 연결 작업을 완료합니다.

 후자의 경우 메서드에 전달된 `IDebugProgram2` `IDebugEngine2::Attach` 개체에 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 호출 하고 `GUID` 로컬 프로그램 개체에 저장 `GUID` 한 `IDebugProgram2::GetProgramId` 다음 메서드가 이후에이 개체에 호출 될 때 이 메서드를 반환 해야 합니다. 는 `GUID` 다양한 디버그 구성 요소에서 고유하게 프로그램을 식별하는 데 사용됩니다.

 반환 `IDebugProgramNodeAttach2::OnAttach` `S_FALSE`하는 메서드의 경우 `GUID` 프로그램에 대 한 사용 하는 메서드는 해당 `IDebugProgramNodeAttach2::OnAttach` 메서드에 전달 `GUID` 되 고 로컬 프로그램 개체에 설정 하는 메서드입니다.

 이제 DE가 프로그램에 연결되고 시작 이벤트를 보낼 준비가 되었습니다.

## <a name="see-also"></a>참조
- [프로그램에 직접 연결](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [포트 알림](../../extensibility/debugger/notifying-the-port.md)
- [작업 디버깅](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [연결](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [연결](../../extensibility/debugger/reference/idebugengine2-attach.md)
