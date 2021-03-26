---
title: 세션 디버그 관리자 | Microsoft Docs
description: 여러 컴퓨터에서 여러 프로세스의 프로그램을 디버깅 하는 여러 디버그 엔진을 관리 하는 세션 디버그 관리자에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e5a206b8ece21b14758dfeb02563d4d323dcf60
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079464"
---
# <a name="session-debug-manager"></a>세션 디버그 관리자
세션 디버그 관리자 (SDM)는 개수에 관계 없이 여러 컴퓨터의 여러 프로세스에서 많은 프로그램을 디버그 하는 디버그 엔진 (DE)을 관리 합니다. SDM은 디버그 엔진 멀티플렉서 뿐만 아니라 IDE에 대 한 디버그 세션의 통합 보기를 제공 합니다.

## <a name="session-debug-manager-operation"></a>세션 디버그 관리자 작업
 세션 디버그 관리자 (SDM)는 DE를 관리 합니다. 동시에 한 컴퓨터에서 실행 되는 디버그 엔진이 두 개 이상 있을 수 있습니다. DEs를 멀티플렉싱 위해 SDM은 DEs에서 많은 인터페이스를 래핑하고 단일 인터페이스로 IDE에 노출 합니다.

 성능을 향상 시키기 위해 일부 인터페이스는 멀티플렉싱 되지 않습니다. 대신, DE에서 직접 사용 되며 이러한 인터페이스에 대 한 호출은 SDM을 통과 하지 않습니다. 예를 들어 메모리, 코드 및 문서 컨텍스트를 사용 하 여 사용 되는 인터페이스는 특정 DE에 의해 디버깅 되는 특정 프로그램에서 특정 명령, 메모리 또는 문서를 참조 하기 때문에 멀티플렉싱 되지 않습니다. 다른 DE는 해당 통신 수준에 포함 될 필요가 없습니다.

 이는 모든 컨텍스트에서는 적용 되지 않습니다. 식 평가 컨텍스트 인터페이스를 호출 하면 SDM을 거칩니다. 식을 평가 하는 동안 SDM은 IDE에 제공 하는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 래핑합니다 .이는 해당 식이 평가 될 때 동일한 스레드에서 실행 될 수 있는 동일한 프로세스에서 프로그램을 디버깅 하는 여러 DEs를 포함할 수 있습니다.

 이 SDM은 일반적으로 위임 메커니즘으로 작동 하지만 브로드캐스트 메커니즘으로 작동할 수 있습니다. 예를 들어 식 평가 중에 SDM은 지정 된 스레드에서 코드를 실행할 수 있다는 것을 모든 DEs에 알리기 위한 브로드캐스트 메커니즘 역할을 합니다. 마찬가지로, SDM이 중지 이벤트를 수신 하면 실행을 중지 해야 하는 프로그램에 브로드캐스트합니다. 단계가 호출 되 면 SDM은 계속 실행 될 수 있는 프로그램에 브로드캐스트합니다. 중단점도 모든 DE에 브로드캐스트 됩니다.

 SDM은 현재 프로그램, 스레드 또는 스택 프레임을 추적 하지 않습니다. 프로세스, 프로그램 및 스레드 정보는 특정 디버깅 이벤트와 함께 SDM에 전송 됩니다.

## <a name="see-also"></a>참조
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
