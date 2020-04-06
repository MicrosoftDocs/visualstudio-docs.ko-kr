---
title: 호출 디버거 이벤트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739173"
---
# <a name="call-debugger-events"></a>호출 디버거 이벤트
디버깅 세션의 이벤트는 특정 순서로 발생합니다.

## <a name="discussion"></a>토론
 DE(디버그 엔진)와 세션 디버그 관리자(SDM) 간의 호출 패턴을 이해하려면 일반적인 디버깅 세션에서 발생하는 이벤트의 호출 순서를 나타냅니다.

1. [프로그램에 연결 및 분리](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [디버거 실행](../../extensibility/debugger/launching-the-debugger.md)

3. [프로그램 종료](../../extensibility/debugger/terminating-a-program.md)

4. [중단점 만들기](../../extensibility/debugger/creating-a-breakpoint.md)

5. [중단점이 바인딩되거나 언바운드되는 경우](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [중단점 오류](../../extensibility/debugger/breakpoint-errors.md)

7. [중단점 도착](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [중단점 삭제](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [브레이크 모드 진입](../../extensibility/debugger/entering-break-mode.md)

10. [브레이크 모드에서 스테핑](../../extensibility/debugger/stepping-in-break-mode.md)

11. [중단 모드에서 표현식 평가](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [예외 처리](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>참조
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
