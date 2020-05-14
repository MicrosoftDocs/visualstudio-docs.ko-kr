---
title: 브레이크 모드 입력 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738884"
---
# <a name="enter-break-mode"></a>브레이크 모드 입력
다음 정보는 함수에 침입하거나, 커서가 있는 소스 코드 줄로 실행되거나, 중단점으로 실행한 후 중단점이 발생할 때 발생하는 프로세스에 대해 설명합니다.

## <a name="break-mode-process"></a>브레이크 모드 프로세스

1. 디버그 엔진(DE)은 [IDebugBreakpointEventEvent2,](../../extensibility/debugger/reference/idebugbreakpointevent2.md) [IDebugExceptionEventEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)또는 기타 중지 이벤트를 전송하여 IDE가 중단 모드로 진입하도록 합니다.

2. SDM은 다음과 같이 스레드에서 호출 스택 정보를 가져옵니다.

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 소스 코드 정보를 가져옵니다

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) 파일 이름을 가져옵니다.

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 문 범위를 가져옵니다.

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) 메모리 정보를 가져옵니다

## <a name="see-also"></a>참조
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
