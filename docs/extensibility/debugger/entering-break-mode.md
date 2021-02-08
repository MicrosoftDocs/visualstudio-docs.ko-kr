---
title: 중단 모드 시작 | Microsoft Docs
description: 함수에서 발생 하는 중단점에 대해 알아보고 커서의 소스 코드 줄을 실행 하거나 중단점까지 실행 하는 프로세스에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3ec09994f6998f87daafc690b1908b31e54706b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840654"
---
# <a name="enter-break-mode"></a>중단 모드로 전환
다음 정보는 함수를 한 단계씩 실행 한 후 중단점에 커서를 포함 하는 소스 코드 줄을 실행 하거나 중단점까지 실행 한 후에 발생 하는 프로세스에 대해 설명 합니다.

## <a name="break-mode-process"></a>중단 모드 프로세스

1. DE (디버그 엔진)는 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)또는 기타 중지 이벤트를 보내 IDE가 중단 모드로 전환 되도록 합니다.

2. SDM은 다음과 같이 스레드에서 호출 스택 정보를 가져옵니다.

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - 소스 코드 정보를 가져오는 [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)

    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) 를 통해 파일 이름을 가져옵니다.

    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 를 통해 문 범위 가져오기

    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) 를 통해 메모리 정보 가져오기

## <a name="see-also"></a>참고 항목
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
