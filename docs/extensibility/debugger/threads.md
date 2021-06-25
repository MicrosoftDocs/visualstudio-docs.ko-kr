---
title: 스레드 | Microsoft Docs
description: 이 문서에서는 Visual Studio 디버거 아키텍처에서 스레드의 정의 및 역할을 설명합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc745a4361c0935896048bbf72a4084f007ecf7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905737"
---
# <a name="threads"></a>스레드
디버거 아키텍처에서 *스레드:*

- 계산의 기본 단위입니다. 스레드는 단일 호출 스택의 컨텍스트 내에서 해당 명령을 순차적으로 실행하여 한 코드 컨텍스트에서 다음 코드 컨텍스트로 이동합니다.

- 자체 및 실행 중인 프로그램을 식별할 수 있습니다. 스레드의 이름을 지정하고 일시 중단한 다음 다시 시작할 수 있습니다. 스레드는 연결된 스택 프레임을 열거할 수도 있으며 일부 조건에서 다른 스택 프레임으로 이동할 수 있습니다. 스택 프레임의 컨텍스트를 고려할 때 스레드는 연결된 논리 스레드(있는 경우)를 반환할 수 있습니다. 스레드에는 IDE의 **스레드** 창에 표시할 수 있는 일시 중단 횟수와 같은 속성이 있습니다.

- 일반적으로 디버그 엔진(DE) 또는 가상 머신에서 프로그램을 실행한 결과로 만들어지는 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 인터페이스로 표시됩니다.

## <a name="see-also"></a>참조
- [프로그램](../../extensibility/debugger/programs.md)
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)
