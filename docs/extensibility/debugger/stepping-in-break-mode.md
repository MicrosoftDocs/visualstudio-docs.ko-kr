---
title: 중단 모드에서 단계별 실행 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712849"
---
# <a name="stepping-in-break-mode"></a>중단 모드에서 단계별 실행
다음 섹션에서는 디버거가 중단 모드에 있을 때 발생 하는 프로세스에 대해 설명 하 고 코드를 단계별로 실행 해야 합니다.

## <a name="stepping-process"></a>단계별 프로세스

1. 단계를 실행 하려면 [Stkind](../../extensibility/debugger/reference/stepkind.md) 와 [stunit](../../extensibility/debugger/reference/stepunit.md) 인수를 사용 하 여 [IDebugProgram2:: step](../../extensibility/debugger/reference/idebugprogram2-step.md) 을 호출 합니다.

2. 단계가 완료 되 면 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 를 중지 이벤트로 보냅니다.

## <a name="see-also"></a>참고 항목
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
