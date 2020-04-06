---
title: 프로그램 노드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738223"
---
# <a name="program-nodes"></a>프로그램 노드
디버거 아키텍처에서 프로그램 *노드:*

- 프로그램의 간단한 설명입니다.

- 자체 및 실행 중인 프로세스를 식별할 수 있습니다. 프로그램 노드를 연결하여 분리하고, 분리하고, 이를 만든 DE(디버그 엔진)(있는 경우)를 설명할 수 있습니다.

- 일반적으로 DE 또는 포트에 의해 생성된 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스로 표시됩니다. 프로그램 노드는 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)를 호출하여 포트에 추가됩니다. 프로그램 노드가 포트에 추가되면 이 프로그램 노드가 나타내는 프로그램을 포함하는 프로세스에 추가됩니다.

  디버그 세션이 시작된 후 디버그 패키지의 구현에 따라 프로그램 노드가 해당 프로그램을 만드는 데 사용됩니다. 해당 프로그램에 대해 프로세스가 쿼리되면 각 프로그램 노드에 대해 하나씩 프로그램이 등록됩니다.

  프로그램을 연결하기 전에 IDE는 프로그램에 대한 간단한 설명만 있으면 됩니다. 이 정보는 프로그램 노드에서 가져올 수 있습니다. 프로그램이 연결되면 IDE는 프로그램에서 실행중인 모든 스레드 목록과 같은 자세한 정보를 표시합니다. 이 정보는 프로그램 자체에서 가져옵니다.

## <a name="see-also"></a>참조
- [Programs](../../extensibility/debugger/programs.md)
- [프로세스](../../extensibility/debugger/processes.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
