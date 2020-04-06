---
title: 프로세스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738239"
---
# <a name="processes"></a>프로세스
디버거 아키텍처에서 *프로세스:*

- 일련의 프로그램 컨테이너입니다. 스레드 집합에 대 한 컨테이너는 Windows 프로세스와 매우 유사 합니다.

- 이름, 식별자 또는 물리적 식별자로 자신을 식별할 수 있습니다.

- 실행 중인 모든 프로그램(및 해당 스레드)을 열거할 수 있습니다.

- 자체, 실행 중인 포트 및 해당 포트를 포함하는 컴퓨터를 설명할 수 있습니다.

- 하나 이상의 프로그램을 만들거나, 프로그램을 종료하거나, 프로그램을 중지할 수 있습니다.

- 프로세스가 시작될 때 생성되는 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스로 표시됩니다. 프로세스는 세션 디버그 관리자(SDM) 또는 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)에 의해 시작됩니다.

  디버그 패키지는 Debug 엔진(DE)을 [연결하여](../../extensibility/debugger/reference/idebugprocess2-attach.md)프로세스에 연결할 수 있으며, 이는 DE가 처리할 수 있는 프로세스에서 실행중인 모든 가능한 프로그램에 연결된다는 것을 의미합니다. 예를 들어 공통 언어 런타임 DE가 프로세스에 연결하는 경우 관리 되는 코드를 실행 하는 프로그램에만 연결 됩니다.

## <a name="see-also"></a>참조
- [Programs](../../extensibility/debugger/programs.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [디버그 패키지](../../extensibility/debugger/debug-package.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [연결](../../extensibility/debugger/reference/idebugprocess2-attach.md)
