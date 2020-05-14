---
title: 브레이크 모드에서 스테핑 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712849"
---
# <a name="stepping-in-break-mode"></a>브레이크 모드에서 스테핑
다음 섹션에서는 디버거가 중단 모드에 있을 때 발생하는 프로세스에 대해 설명하고 코드를 단계별로 수행해야 합니다.

## <a name="stepping-process"></a>스테핑 프로세스

1. [IDebugProgram2::STEPKIND](../../extensibility/debugger/reference/idebugprogram2-step.md) [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 및 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 인수를 사용하여 단계를 실행합니다.

2. 단계가 완료되면 [IDebugStepCompleteEvent2를](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 중지 이벤트로 보냅니다.

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
