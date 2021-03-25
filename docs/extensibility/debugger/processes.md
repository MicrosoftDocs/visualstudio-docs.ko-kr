---
title: 프로세스 | Microsoft Docs
description: 이 문서에서는 Visual Studio의 디버거 아키텍처에서 프로세스의 정의와 역할에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 46e25ddfbe60e1b9ee456e586c6f424fc489f626
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067714"
---
# <a name="processes"></a>프로세스
디버거 아키텍처에서 *프로세스* 는 다음과 같습니다.

- 는 프로그램 집합에 대 한 컨테이너입니다. 스레드 집합의 컨테이너인 Windows 프로세스와 매우 유사 합니다.

- 이름, 식별자 또는 실제 식별자로 자신을 식별할 수 있습니다.

- 는 실행 중인 모든 프로그램 (및 해당 스레드)을 열거할 수 있습니다.

- 자체, 실행 중인 포트 및이를 포함 하는 컴퓨터를 설명할 수 있습니다.

- 하나 이상의 프로그램을 만들거나, 만든 프로그램을 종료 하거나, 프로그램을 중지할 수 있습니다.

- 는 프로세스를 시작할 때 생성 되는 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스로 표시 됩니다. 프로세스는 SDM (세션 디버그 관리자) 또는 [Launchsuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)에 의해 시작 됩니다.

  디버그 패키지는 [attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)를 호출 하 여 디버그 엔진 (de)을 프로세스에 연결할 수 있습니다 .이는 de-de가 처리할 수 있는 프로세스에서 실행 되는 모든 프로그램에 연결 하는 것을 의미 합니다. 예를 들어 공용 언어 런타임 DE가 프로세스에 연결 되 면 관리 코드를 실행 하는 프로그램에만 연결 됩니다.

## <a name="see-also"></a>참조
- [프로그램](../../extensibility/debugger/programs.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [패키지 디버그](../../extensibility/debugger/debug-package.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [연결](../../extensibility/debugger/reference/idebugprocess2-attach.md)
