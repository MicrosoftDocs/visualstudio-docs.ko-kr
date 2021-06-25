---
title: 프로그램 노드 | Microsoft Docs
description: 이 문서에서는 Visual Studio의 디버거 아키텍처에서 프로그램 노드의 정의 및 역할에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4c26fa95a5fedf325591ce517e7c12ecebcd705c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899084"
---
# <a name="program-nodes"></a>프로그램 노드
디버거 아키텍처에서 *프로그램 노드* 는 다음과 같습니다.

- 은 프로그램에 대 한 간단한 설명입니다.

- 자체와 해당 프로세스가 실행 되 고 있는 프로세스를 식별할 수 있습니다. 프로그램 노드를에 연결 하 고, 분리 하 고,이를 만든 디버그 엔진 (있는 경우)을 설명할 수 있습니다.

- 는 일반적으로 DE 또는 포트에서 만든 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스로 표시 됩니다. 프로그램 노드는 [add프로그래밍할 node](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)를 호출 하 여 포트에 추가 됩니다. 프로그램 노드는 포트에 추가 될 때이 프로그램 노드가 나타내는 프로그램을 포함 하는 프로세스에 추가 됩니다.

  디버그 세션이 시작 된 후에는 디버그 패키지의 구현에 따라 프로그램 노드를 사용 하 여 해당 프로그램을 만듭니다. 프로그램에 대 한 프로세스를 쿼리하면 프로그램이 각 프로그램 노드에 대해 하나씩 열거 됩니다.

  프로그램이에 연결 되기 전에는 IDE에 프로그램에 대 한 간단한 설명만 필요 합니다. 이 정보는 프로그램 노드에서 가져올 수 있습니다. 프로그램이에 연결 되 면 IDE는 프로그램에서 실행 중인 모든 스레드의 목록과 같은 보다 자세한 정보를 표시 합니다. 이 정보는 프로그램 자체에서 가져옵니다.

## <a name="see-also"></a>참조
- [프로그램](../../extensibility/debugger/programs.md)
- [프로세스](../../extensibility/debugger/processes.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
