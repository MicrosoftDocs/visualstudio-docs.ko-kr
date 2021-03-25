---
title: 디버거 이벤트 호출 | Microsoft Docs
description: 디버깅 세션의 이벤트는 특정 순서로 발생 합니다. 이 문서에서는 일반적인 디버깅 세션에서 발생 하는 이벤트의 호출 순서를 나열 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b0c3169039115432758cfdcd3f0612c3578b74c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055053"
---
# <a name="call-debugger-events"></a>디버거 이벤트 호출
디버깅 세션의 이벤트는 특정 순서로 발생 합니다.

## <a name="discussion"></a>토론(Discussion)
 디버그 엔진 (DE)과 세션 디버그 관리자 (SDM) 간의 호출 패턴을 이해 하기 위해 다음은 일반적인 디버깅 세션에서 발생 하는 이벤트의 호출 순서를 나타냅니다.

1. [프로그램에 연결 및 분리](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [디버거 시작](../../extensibility/debugger/launching-the-debugger.md)

3. [프로그램 종료](../../extensibility/debugger/terminating-a-program.md)

4. [중단점 만들기](../../extensibility/debugger/creating-a-breakpoint.md)

5. [중단점이 바인딩 또는 바인딩 해제 되는 경우](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [중단점 오류](../../extensibility/debugger/breakpoint-errors.md)

7. [중단점 적중](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [중단점 삭제](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [중단 모드 시작](../../extensibility/debugger/entering-break-mode.md)

10. [중단 모드에서 단계별 실행](../../extensibility/debugger/stepping-in-break-mode.md)

11. [중단 모드에서 식 계산](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [예외 처리](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>참조
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
