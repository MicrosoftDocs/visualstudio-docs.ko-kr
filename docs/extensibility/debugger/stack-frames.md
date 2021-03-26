---
title: 스택 프레임 | Microsoft Docs
description: 이 문서에서는 Visual Studio의 디버거 아키텍처에서 스택 프레임의 정의 및 역할에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b0c54292d79b119fc36c9eff3f0f3519c92a4205
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079397"
---
# <a name="stack-frames"></a>스택 프레임
디버거 아키텍처에서 *스택 프레임* 은 다음과 같습니다.

- 는 스레드의 실행 컨텍스트를 제공 하는 스택을 추상화 한 것입니다. 스레드는 항상 함수 내에서 실행 됩니다. 스택 프레임은 함수의 지역 변수와이 변수에 대 한 인수를 포함 합니다. Visual Studio를 사용 하 여 디버그 하려면 디버그 중인 언어나 환경에서 스택 프레임을 지원 해야 합니다.

- 는 자신을 식별 하 고 설명 하 고 연결 된 스레드를 반환할 수 있습니다. 스택 프레임은 현재 명령 포인터와 관련 된 설명서 및 식 계산 컨텍스트를 나타내는 코드 컨텍스트를 반환할 수도 있습니다.

- 에는 로컬 변수 및 인수의 이름, 형식 및 값을 설명 하 고 다양 한 IDE 디버그 창에 표시 되는 속성이 있습니다.

- 는 스레드 실행의 결과로 일반적으로 디버그 엔진 (DE) 또는 가상 머신에서 만든 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스로 표시 됩니다.

## <a name="see-also"></a>참조
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
