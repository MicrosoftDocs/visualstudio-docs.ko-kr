---
title: 프로그램 종료 | Microsoft Docs
description: 이 문서에서는 IDE에서 디버그 엔진을 사용 하 여 단일 스레드를 사용 하 여 단일 프로그램을 종료 하는 방법을 설명 합니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1b2b883611d5479f0febc169b32f7f378230be4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995982"
---
# <a name="terminating-a-program"></a>프로그램 종료
다음 섹션에서는 하나의 스레드를 사용 하는 단일 프로그램 종료에 대해 설명 합니다.

## <a name="termination-process"></a>종료 프로세스

1. DE는 유효한 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)로 [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 를 보냅니다.

2. DE는 유효한 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)로 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 를 보냅니다.

   IDE가 디자인 모드로 전환 됩니다. 디버그 엔진 또는 런타임 환경에서는 [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 를 호출 하 여 포트에서 프로그램을 제거 합니다.

## <a name="see-also"></a>참고 항목
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
