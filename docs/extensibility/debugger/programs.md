---
title: 프로그램 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738199"
---
# <a name="programs"></a>Programs
디버거 아키텍처에서 프로그램은 다음과 같은 *것입니다.*

- 스레드 집합과 모듈 집합 모두에 대한 컨테이너입니다. 프로그램에는 Windows 운영 체제에 단일 비유가 없습니다.

     프로그램은 일종의 하위 프로세스입니다. 예를 들어 웹 사이트를 디버깅하는 경우 스크립트를 프로그램으로 볼 수 있습니다. 스크립트는 다른 스크립트와 는 별개로 스크립팅 엔진 프로세스에서 실행되지만 자체 스레드 집합도 있습니다. 디버그 엔진(DE)은 프로세스나 스레드가 아닌 프로그램에 연결됩니다.

- 자체 및 실행 중인 프로세스를 식별할 수 있습니다. 프로그램을 연결하여 분리하고, 프로그램을 만든 DE(있는 경우)를 설명할 수 있습니다. 프로그램은 실행, 중지, 계속 및 종료할 수도 있습니다.

- 모든 스레드를 열거할 수 있습니다. 또한 프로그램은 자체 디스어셈블리 스트림을 제공할 수 있으며 지정된 문서 위치의 모든 코드 컨텍스트를 열거할 수 있습니다.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스로 표시되며, 프로그램이 연결되기 전에 생성하거나 구현에 따라 연결 프로세스의 일부로 표시됩니다. 포트가 프로세스의 프로그램을 연거할 때 각 프로그램은 [AddProgramNode에](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)대한 인수로 전달된 해당 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스에 따라 만들어집니다. 디버그 엔진은 `IDebugProgram2` 프로그램을 나타내는 인터페이스도 생성하지만 이러한 프로그램은 프로그램 노드에 따라 만들어지지 않습니다. DE에서 만든 인터페이스는 `IDebugProgramNode2` 실제 디버깅에 사용되며 포트에서 만든 인터페이스는 프로세스에서 실행 중인 프로그램을 검색하는 데만 사용됩니다.

## <a name="see-also"></a>참조
- [프로세스](../../extensibility/debugger/processes.md)
- [프로그램 노드](../../extensibility/debugger/program-nodes.md)
- [모듈](../../extensibility/debugger/modules.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [문서 위치](../../extensibility/debugger/document-position.md)
- [코드 컨텍스트](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
