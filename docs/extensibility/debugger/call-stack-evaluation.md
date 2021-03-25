---
title: 호출 스택 평가 | Microsoft Docs
description: Enumframe Info 메서드에 대해 알아보고 중단 모드에서 호출 스택의 스택 프레임을 볼 수 있도록 구현 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c7e7180301965e43e6757340019c3506fe1a5e1f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055091"
---
# <a name="call-stack-evaluation"></a>호출 스택 평가
중단 모드에서 호출 스택의 스택 프레임을 보려면 [Enum프레임 정보](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 메서드를 구현 해야 합니다.

## <a name="methods-for-evaluation"></a>평가 방법
 간단한 디버그 엔진 (DE)의 경우 스택 프레임은 하나만 있을 수 있습니다. 중단 모드에서 스택 프레임을 검사 하려면 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)의 다음 메서드를 구현 해야 합니다.

|메서드|Description|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|스택 프레임에 대 한 코드 컨텍스트를 가져옵니다. 코드 컨텍스트는 스택 프레임의 현재 명령 포인터를 나타냅니다.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|스택 프레임에 대 한 문서 컨텍스트를 가져옵니다. 문서 컨텍스트는 스택 프레임에 대 한 소스 코드의 현재 위치를 나타냅니다. 프로그램에서 중지 된 경우 소스 코드를 보는 데 필요 합니다.|

 이러한 메서드는 여러 컨텍스트 관련 인터페이스 및 메서드를 구현 해야 합니다. 따라서 [Getdocumentcontext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 메서드와 [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)의 다음 메서드를 구현 해야 합니다.

|메서드|Description|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|문서 컨텍스트의 파일 문 범위를 가져옵니다.|

 코드 컨텍스트를 열거 하려면 [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)의 모든 메서드를 구현 해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
