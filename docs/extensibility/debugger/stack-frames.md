---
title: 스택 프레임 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712838"
---
# <a name="stack-frames"></a>스택 프레임
디버거 아키텍처에서 스택 *프레임:*

- 스레드의 실행 컨텍스트를 제공하는 스택의 추상화입니다. 스레드는 항상 함수 내에서 실행됩니다. 스택 프레임에는 함수의 로컬 변수와 함수에 대한 인수를 보유합니다. Visual Studio를 사용하여 디버깅하려면 디버깅중인 언어 또는 환경이 스택 프레임을 지원해야 합니다.

- 자신을 식별하고 설명할 수 있으며 연결된 스레드를 반환할 수 있습니다. 스택 프레임은 현재 명령 포인터와 관련 문서 및 식 평가 컨텍스트를 나타내는 코드 컨텍스트를 반환할 수도 있습니다.

- 지역 변수 및 인수의 이름, 형식 및 값을 설명하고 다양한 IDE 디버그 창에 나타나는 속성을 포함합니다.

- 스레드를 실행한 결과로 일반적으로 디버그 엔진(DE) 또는 가상 시스템에 의해 생성된 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스로 표시됩니다.

## <a name="see-also"></a>참조
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
