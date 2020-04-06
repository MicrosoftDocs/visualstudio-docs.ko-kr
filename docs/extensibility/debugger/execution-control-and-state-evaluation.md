---
title: 실행 제어 및 상태 평가 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738746"
---
# <a name="execution-control-and-state-evaluation"></a>실행 제어 및 상태 평가
응용 프로그램을 디버깅하려면 함수 단계별 단계, 중단점에서 중지 및 실행 을 계속하는 것과 같은 실행 제어 기능을 구현해야 합니다. Visual Studio 디버깅은 디버거 구성 요소 간에 전송되는 이벤트에 대한 실행 제어를 기반으로 합니다.

## <a name="in-this-section"></a>섹션 내용
 [프로그램 제어](../../extensibility/debugger/program-control.md) 프로그램 수준에서 발생하는 다음 루틴을 나열합니다: 다음 문을 설정, 실행, 단계, 계속, 일시 중단 및 다시 시작.

 [중단점 관련 방법](../../extensibility/debugger/breakpoint-related-methods.md) Visual Studio에서 지원하는 중단점의 바인딩 및 보류 중인 형식을 정의합니다.

 [통화 스택 평가](../../extensibility/debugger/call-stack-evaluation.md) 중단 모드 중에 호출 스택의 스택 프레임을 볼 수 있는 메서드의 구현에 대해 설명합니다.

 [표현식 평가](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) 디버그 엔진(DE), 식 평가(EE) 및 세션 디버그 관리자가 IDE의 창 중 하나에 입력된 식의 구문 분석 및 평가에 관여하는 방법을 설명합니다.

 [이벤트 제어](../../extensibility/debugger/control-events.md) 프로그램의 제어된 실행 중에 이벤트를 보내는 데 사용되는 인터페이스에 대해 설명합니다.
