---
title: 스레드 | Microsoft Docs
description: 이 문서에서는 Visual Studio의 디버거 아키텍처에서 스레드의 정의 및 역할에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 168d29b8306ec58233f426b48c3ab0adfacb2bd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057847"
---
# <a name="threads"></a>스레드
디버거 아키텍처에서 *스레드* 는 다음과 같습니다.

- 계산의 기본 단위입니다. 스레드는 단일 호출 스택의 컨텍스트 내에서 해당 명령을 순차적으로 실행 하 여 코드 컨텍스트 간에 이동 합니다.

- 자체와 해당 프로그램이 실행 되는 프로그램을 식별할 수 있습니다. 스레드 이름을 지정 하 고, 일시 중지 하 고, 다시 시작할 수 있습니다. 또한 스레드는 연결 된 스택 프레임을 열거 하 고, 경우에 따라 다른 스택 프레임으로 이동할 수 있습니다. 스택 프레임의 컨텍스트가 지정 된 경우 스레드에서 연결 된 논리 스레드를 반환할 수 있습니다 (있는 경우). 스레드에는 IDE의 **스레드** 창에 표시 될 수 있는 일시 중단 횟수와 같은 속성이 있습니다.

- 는 프로그램 실행의 결과로 일반적으로 디버그 엔진 (DE) 또는 가상 머신에서 만든 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 인터페이스로 표시 됩니다.

## <a name="see-also"></a>참조
- [프로그램](../../extensibility/debugger/programs.md)
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)
