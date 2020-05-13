---
title: 프로그램 종료 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712516"
---
# <a name="terminating-a-program"></a>프로그램 종료
다음 섹션에서는 하나의 스레드가 있는 단일 프로그램의 종료에 대해 설명합니다.

## <a name="termination-process"></a>종료 프로세스

1. DE는 유효한 [IDebugThread2를 가진 IDebugThreadDestroyEvent2를](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 보냅니다. [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)

2. DE는 유효한 [IDebugProgram2와 함께 IDebugProgramDestroyEvent2를](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 보냅니다. [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

   IDE는 디자인 모드로 전환됩니다. 디버그 엔진 또는 런타임 [환경에서는 IDebugPortNotify2::RemoveProgramNode를](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 호출하여 포트에서 프로그램을 제거합니다.

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
