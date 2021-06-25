---
title: 호출 스택 평가 | Microsoft Docs
description: EnumFrameInfo 메서드와 이를 구현하여 중단 모드 중에 호출 스택의 스택 프레임을 보는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 059c42349c7f8e681709d69104cf65a6fc245206
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898541"
---
# <a name="call-stack-evaluation"></a>호출 스택 평가
중단 모드 중에 호출 스택의 스택 프레임을 보려면 [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 메서드를 구현해야 합니다.

## <a name="methods-for-evaluation"></a>평가 방법
 간단한 디버그 엔진(DE)의 경우 스택 프레임이 하나만 있을 수 있습니다. 중단 모드 중에 스택 프레임을 검사하려면 [IDebugStackFrame2의](../../extensibility/debugger/reference/idebugstackframe2.md)다음 메서드를 구현해야 합니다.

|메서드|설명|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|스택 프레임의 코드 컨텍스트를 가져옵니다. 코드 컨텍스트는 스택 프레임의 현재 명령 포인터를 나타냅니다.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|스택 프레임의 문서 컨텍스트를 가져옵니다. 문서 컨텍스트는 스택 프레임에 대한 소스 코드의 현재 위치를 나타냅니다. 프로그램에서 중지될 때 소스 코드를 보는 데 필요합니다.|

 이러한 메서드를 사용하려면 여러 컨텍스트 관련 인터페이스 및 메서드를 구현해야 합니다. 따라서 [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 메서드와 [IDebugDocumentContext2의](../../extensibility/debugger/reference/idebugdocumentcontext2.md)다음 메서드를 구현해야 합니다.

|메서드|설명|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|문서 컨텍스트의 파일 문 범위를 가져옵니다.|

 코드 컨텍스트를 열거하려면 [IEnumDebugCodeContexts2의](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)모든 메서드를 구현해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
