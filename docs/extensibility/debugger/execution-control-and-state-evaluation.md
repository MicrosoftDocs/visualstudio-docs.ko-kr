---
title: 실행 제어 및 상태 평가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738746"
---
# <a name="execution-control-and-state-evaluation"></a>실행 제어 및 상태 평가
응용 프로그램을 디버깅 하려면 함수를 한 단계씩 실행 하 고 중단점에서 중지 하 고 실행을 계속 하는 등의 실행 제어 기능을 구현 해야 합니다. Visual Studio 디버깅은 디버거 구성 요소 간에 전송 된 이벤트에 대 한 실행 제어를 기반으로 합니다.

## <a name="in-this-section"></a>섹션 내용
 [프로그램 제어](../../extensibility/debugger/program-control.md) 프로그램 수준에서 발생 하는 다음 루틴을 나열 합니다. 다음 문 설정, 실행, 단계별 실행, 계속, 일시 중단 및 다시 시작

 [중단점 관련 메서드](../../extensibility/debugger/breakpoint-related-methods.md) Visual Studio에서 지 원하는 바인딩 및 보류 중인 중단점 형식을 정의 합니다.

 [호출 스택 평가](../../extensibility/debugger/call-stack-evaluation.md) 중단 모드에서 호출 스택의 스택 프레임을 볼 수 있도록 하는 메서드의 구현에 대해 설명 합니다.

 [식 계산](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) 디버그 엔진 (DE), 식 계산 (EE) 및 세션 디버그 관리자가 IDE의 창 중 하나에 입력 된 식의 구문 분석 및 평가와 관련 되는 방법을 설명 합니다.

 [컨트롤 이벤트](../../extensibility/debugger/control-events.md) 프로그램의 제어 되는 실행 중에 이벤트를 전송 하는 데 사용 되는 인터페이스에 대해 설명 합니다.
