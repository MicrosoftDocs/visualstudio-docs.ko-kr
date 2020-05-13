---
title: 세션 디버그 관리자 | 마이크로 소프트 문서
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712880"
---
# <a name="session-debug-manager"></a>세션 디버그 관리자
세션 디버그 관리자(SDM)는 여러 컴퓨터에서 여러 프로세스의 프로그램 수를 디버깅하는 DE(디버그 엔진)를 관리합니다. SDM은 디버그 엔진 멀티플렉서일 뿐만 아니라 IDE에 디버그 세션의 통합보기를 제공합니다.

## <a name="session-debug-manager-operation"></a>세션 디버그 관리자 작업
 세션 디버그 관리자(SDM)는 DE를 관리합니다. 동시에 컴퓨터에서 실행되는 디버그 엔진이 두 개 이상 있을 수 있습니다. DEs를 다중화하기 위해 SDM은 DEs에서 여러 인터페이스를 래핑하고 이를 IDE에 단일 인터페이스로 노출시합니다.

 성능을 높이기 위해 일부 인터페이스는 멀티플렉싱되지 않습니다. 대신 DE에서 직접 사용되며 이러한 인터페이스에 대한 호출은 SDM을 거치지 않습니다. 예를 들어 메모리, 코드 및 문서 컨텍스트와 함께 사용되는 인터페이스는 특정 DE에서 디버깅한 특정 프로그램의 특정 명령, 메모리 또는 문서를 참조하기 때문에 다중화되지 않습니다. 다른 DE는 해당 통신 수준에 관여할 필요가 없습니다.

 모든 컨텍스트에서 사실이 아닙니다. 식 평가 컨텍스트 인터페이스에 대한 호출은 SDM을 통과합니다. 식 평가 중에 SDM은 해당 표현식이 평가될 때 동일한 스레드에서 실행될 수 있는 동일한 프로세스에서 프로그램을 디버깅하는 여러 DEs를 포함할 수 있기 때문에 IDE에 제공하는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 래핑합니다.

 SDM은 일반적으로 위임 메커니즘의 역할을 하지만 브로드캐스트 메커니즘으로 작동할 수 있습니다. 예를 들어 식 평가 중에 SDM은 지정된 스레드에서 코드를 실행할 수 있음을 모든 DE에게 알리는 브로드캐스트 메커니즘의 역할을 합니다. 마찬가지로 SDM이 중지 이벤트를 수신하면 실행을 중지해야 하는 프로그램에 브로드캐스트됩니다. 단계가 호출되면 SDM은 계속 실행할 수 있는 프로그램에 브로드캐스트합니다. 중단점은 모든 DE에도 브로드캐스트됩니다.

 SDM은 현재 프로그램, 스레드 또는 스택 프레임을 추적하지 않습니다. 프로세스, 프로그램 및 스레드 정보는 특정 디버깅 이벤트와 함께 SDM으로 전송됩니다.

## <a name="see-also"></a>참조
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
