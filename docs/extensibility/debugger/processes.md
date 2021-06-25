---
title: 프로세스 | Microsoft Docs
description: 이 문서에서는 Visual Studio 디버거 아키텍처에서 프로세스의 정의 및 역할을 설명합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3cadf314b189c72320da3f54488af8560cf3fd8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901255"
---
# <a name="processes"></a>프로세스
디버거 아키텍처에서 *프로세스:*

- 프로그램 집합에 대한 컨테이너입니다. 스레드 집합에 대한 컨테이너인 Windows 프로세스와 매우 유사합니다.

- 이름, 식별자 또는 물리적 식별자를 통해 자신을 식별할 수 있습니다.

- 실행 중인 모든 프로그램(및 해당 스레드)을 열거할 수 있습니다.

- 자체, 실행 중인 포트 및 해당 포트가 포함된 머신을 설명할 수 있습니다.

- 하나 이상의 프로그램을 만들거나, 프로그램을 만들거나, 프로그램을 종료하거나, 프로그램을 중지할 수 있습니다.

- 프로세스가 시작될 때 만들어지는 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스로 표시됩니다. SDM(세션 디버그 관리자) 또는 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)에 의해 프로세스가 시작됩니다.

  디버그 패키지는 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)를 호출하여 프로세스에 DE(디버그 엔진)를 연결할 수 있습니다. 즉, DE는 처리할 수 있는 프로세스에서 실행 중인 모든 가능한 프로그램에 연결됩니다. 예를 들어 공용 언어 런타임 DE가 프로세스에 연결하는 경우 관리 코드를 실행하는 프로그램에만 연결됩니다.

## <a name="see-also"></a>참조
- [프로그램](../../extensibility/debugger/programs.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [패키지 디버그](../../extensibility/debugger/debug-package.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [연결](../../extensibility/debugger/reference/idebugprocess2-attach.md)
