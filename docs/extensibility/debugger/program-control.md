---
title: 프로그램 제어 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738235"
---
# <a name="program-control"></a>프로그램 제어
Visual Studio 디버깅에서 다음 단계 및 계속 루틴은 모두 프로그램 수준에서 발생합니다.

- 다음 명령어 를 설정, 즉, 특정 프레임 환경에서 실행될 다음 명령으로 컴퓨터를 설정

- 실행, 즉, 스테핑 모드에서 종료 계속

- 다음 명령으로 단계적 단계적

- 현재 스테핑 모드 계속

- 프로그램에 포함된 스레드 일시 중단

- 프로그램에 포함된 스레드 다시 시작

> [!NOTE]
> 호출 스택보기는 스레드 수준에서 구현됩니다. 스레드에 대 한 호출 스택을 볼 때 프레임 정보를 열거하려면 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스의 모든 메서드를 구현 해야 합니다.

## <a name="methods-of-program-control"></a>프로그램 제어 방법
 다음 표에서는 최소 기능의 디버그 엔진(DE) 및 실행 제어를 위해 구현해야 하는 [IDebugProgram2의](../../extensibility/debugger/reference/idebugprogram2.md) 메서드를 보여 주며, 이 방법은 다음과 같은 것입니다.

|방법|설명|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|중지된 상태에서 프로그램에 포함된 모든 스레드를 계속 실행합니다. 실행 제어에 필요합니다.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|중지된 상태에서 프로그램에 포함된 모든 스레드를 계속 실행합니다. 실행 제어에 필요합니다.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|지정된 스레드에서 단계를 수행합니다. 프로그램에 포함된 다른 모든 스레드를 계속 실행합니다. 실행 제어에 필요합니다.|

 다중 스레드 프로그램의 경우 [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 메서드와 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) 인터페이스의 모든 메서드도 구현해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
