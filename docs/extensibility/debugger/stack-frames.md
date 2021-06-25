---
title: 스택 프레임 | Microsoft Docs
description: 이 문서에서는 Visual Studio 디버거 아키텍처에서 스택 프레임의 정의 및 역할을 설명합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77b503afcc38ab9427e5268097655433007de5d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898554"
---
# <a name="stack-frames"></a>스택 프레임
디버거 아키텍처에서 스택 *프레임:*

- 스레드의 실행 컨텍스트를 제공하는 스택의 추상화입니다. 스레드는 항상 함수 내에서 실행됩니다. 스택 프레임은 함수의 지역 변수와 함수에 대한 인수를 보유합니다. Visual Studio 사용하여 디버그하려면 디버깅 중인 언어 또는 환경에서 스택 프레임을 지원해야 합니다.

- 자신을 식별하고 설명할 수 있으며 연결된 스레드를 반환할 수 있습니다. 스택 프레임은 현재 명령 포인터와 관련 설명서 및 식 계산 컨텍스트를 나타내는 코드 컨텍스트를 반환할 수도 있습니다.

- 지역 변수 및 인수의 이름, 형식 및 값을 설명하고 다양한 IDE 디버그 창에 표시되는 속성이 있습니다.

- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스로 표현되며, 일반적으로 스레드 실행의 결과로 디버그 엔진(DE) 또는 가상 머신에서 생성됩니다.

## <a name="see-also"></a>참조
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
