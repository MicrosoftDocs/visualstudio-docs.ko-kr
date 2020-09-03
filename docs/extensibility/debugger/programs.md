---
title: 프로그램 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738199"
---
# <a name="programs"></a>프로그램
디버거 아키텍처에서 *프로그램*은 다음을 수행 합니다.

- 는 스레드 집합과 모듈 집합 모두에 대 한 컨테이너입니다. 프로그램은 Windows 운영 체제에서 단일 비유를 포함 하지 않습니다.

     프로그램은 일종의 하위 프로세스입니다. 예를 들어 웹 사이트를 디버깅할 때 스크립트를 프로그램으로 볼 수 있습니다. 스크립트는 스크립트 엔진 프로세스에서 실행 되는 반면 다른 스크립트와는 독립적으로 해당 스레드 집합을 가집니다. 디버그 엔진 (DE)은 프로세스나 스레드가 아니라 프로그램에 연결 됩니다.

- 자체와 해당 프로세스가 실행 되 고 있는 프로세스를 식별할 수 있습니다. 프로그램을에 연결 하 고, 분리 하 고, 프로그램을 만든 DE를 설명할 수 있습니다 (있는 경우). 프로그램이 실행, 중지, 계속 및 종료 될 수도 있습니다.

- 모든 스레드를 열거할 수 있습니다. 프로그램은 자체 디스어셈블리 스트림을 제공할 수도 있고 지정 된 문서 위치의 모든 코드 컨텍스트를 열거할 수도 있습니다.

- 는 구현에 따라 프로그램이 연결 되기 전에 만들어지거나 연결 프로세스의 일부로 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스로 표시 됩니다. 포트에서 프로세스의 프로그램을 열거 하면 [addprogram 노드에](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)인수로 전달 된 해당 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스에 따라 각 프로그램이 만들어집니다. 디버그 엔진 `IDebugProgram2` 은 프로그램을 나타내는 인터페이스도 생성 하지만 프로그램 노드에 따라 이러한 프로그램이 만들어지지 않습니다. `IDebugProgramNode2`DE에 의해 생성 된 인터페이스는 실제 디버깅에 사용 되 고, 포트에 의해 생성 된 인터페이스는 프로세스에서 실행 중인 프로그램을 검색 하는 데만 사용 됩니다.

## <a name="see-also"></a>추가 정보
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
