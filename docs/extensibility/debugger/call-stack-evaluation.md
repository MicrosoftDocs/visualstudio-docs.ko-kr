---
title: 콜 스택 평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739183"
---
# <a name="call-stack-evaluation"></a>통화 스택 평가
중단 모드 중에 호출 스택의 스택 프레임을 보려면 [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 메서드를 구현해야 합니다.

## <a name="methods-for-evaluation"></a>평가 방법
 간단한 디버그 엔진(DE)의 경우 스택 프레임이 하나만 있을 수 있습니다. 중단 모드 중에 스택 프레임을 검사하려면 [IDebugStackFrame2의](../../extensibility/debugger/reference/idebugstackframe2.md)다음 메서드를 구현해야 합니다.

|방법|설명|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|스택 프레임에 대한 코드 컨텍스트를 가져옵니다. 코드 컨텍스트는 스택 프레임의 현재 명령 포인터를 나타냅니다.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|스택 프레임에 대한 문서 컨텍스트를 가져옵니다. 문서 컨텍스트는 스택 프레임의 소스 코드에서 현재 위치를 나타냅니다. 프로그램에서 중지될 때 소스 코드를 보는 데 필요합니다.|

 이러한 메서드에는 여러 컨텍스트 관련 인터페이스 및 메서드를 구현해야 합니다. 따라서 [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 메서드와 [IDebugDocumentContext2의](../../extensibility/debugger/reference/idebugdocumentcontext2.md)다음 메서드를 구현 해야 합니다.

|방법|설명|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|문서 컨텍스트의 파일 명령문 범위를 가져옵니다.|

 코드 컨텍스트를 열거하려면 [IEnumDebugCodeContexts2의](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)모든 메서드를 구현해야 합니다.

## <a name="see-also"></a>참조
- [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
