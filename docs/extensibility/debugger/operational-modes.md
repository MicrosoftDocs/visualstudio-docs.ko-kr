---
title: 운영 모드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738286"
---
# <a name="operational-modes"></a>작동 모드
다음과 같이 IDE가 작동할 수 있는 세 가지 모드가 있습니다.

- [디자인 모드](#vsconoperationalmodesanchor1)

- [실행 모드](#vsconoperationalmodesanchor2)

- [브레이크 모드](#vsconoperationalmodesanchor3)

  이러한 모드 간에 사용자 지정 디버그 엔진(DE)이 전환하는 방법은 전환 메커니즘에 대해 잘 알고 있어야 하는 구현 결정입니다. DE는 이러한 모드를 직접 구현할 수도 있거나 구현하지 않을 수도 있습니다. 이러한 모드는 실제로 DE의 사용자 작업 또는 이벤트에 따라 전환하는 디버그 패키지 모드입니다. 예를 들어 실행 모드에서 중단 모드로의 전환은 DE에서 중지 이벤트에 의해 선동됩니다. 중단에서 실행 모드 또는 단계 모드로의 전환은 단계 또는 실행과 같은 작업을 수행하는 사용자에 의해 선동됩니다. DE 전환에 대한 자세한 내용은 [실행 제어를](../../extensibility/debugger/control-of-execution.md)참조하십시오.

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>디자인 모드
 디자인 모드는 Visual Studio 디버깅의 실행되지 않는 상태이며, 이 기간 동안 응용 프로그램에서 디버깅 기능을 설정할 수 있습니다.

 설계 모드에서는 몇 가지 디버깅 기능만 사용됩니다. 개발자는 중단점을 설정하거나 시계 식을 만들 도록 선택할 수 있습니다. IDE가 디자인 모드에 있는 동안에는 DE가 로드되지 않거나 호출되지 않습니다. DE와의 상호 작용은 실행 및 중단 모드 중에만 발생합니다.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>실행 모드
 실행 모드는 프로그램이 IDE의 디버깅 세션에서 실행될 때 발생합니다. 응용 프로그램은 종료될 때까지, 중단점이 적중될 때까지 또는 예외가 throw될 때까지 실행됩니다. 응용 프로그램이 종료로 실행되면 DE는 디자인 모드로 전환됩니다. 중단점에 도달하거나 예외가 throw되면 DE가 중단 모드로 전환됩니다.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>브레이크 모드
 중단 모드는 디버깅 프로그램의 실행이 일시 중단될 때 발생합니다. 중단 모드는 개발자에게 중단 시 응용 프로그램의 스냅샷을 제공하며 개발자가 응용 프로그램의 상태를 분석하고 응용 프로그램의 실행 방법을 변경할 수 있도록 합니다. 개발자는 코드를 보고 편집하고, 데이터를 검사 또는 수정하거나, 응용 프로그램을 다시 시작하거나, 실행을 종료하거나, 동일한 지점에서 실행을 계속할 수 있습니다.

 DE가 동기 중지 이벤트를 보낼 때 중단 모드가 입력됩니다. 중지 이벤트라고도 하는 동기 중지 이벤트는 세션 디버그 관리자(SDM)와 디버깅 중인 응용 프로그램이 코드 실행을 중지했다는 것을 IDE에 알립니다. [IDebugBreakpointEventEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 및 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 인터페이스는 이벤트를 중지하는 예입니다.

 중지 이벤트는 다음 방법 중 하나에 대한 호출을 통해 계속되며, 디버거를 중단 모드에서 실행 또는 단계 모드로 전환합니다.

- [실행](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [단계](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [계속](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>단계 모드
 단계 모드는 프로그램이 함수의 다음 줄로 단계별로 또는 함수의 안으로, 또는 함수를 초과하거나 나갈 때 발생합니다. 단계는 메서드 [단계](../../extensibility/debugger/reference/idebugprocess3-step.md)단계를 호출하여 실행됩니다. 이 메서드는 `DWORD` [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 및 [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 열거체를 입력 매개변수로 지정하는 s가 필요합니다.

 프로그램이 다음 코드 줄이나 함수로 성공적으로 단계별 단계또는 커서 또는 설정된 중단점으로 실행되면 DE가 자동으로 중단 모드로 전환됩니다.

## <a name="see-also"></a>참조
- [실행 제어](../../extensibility/debugger/control-of-execution.md)
