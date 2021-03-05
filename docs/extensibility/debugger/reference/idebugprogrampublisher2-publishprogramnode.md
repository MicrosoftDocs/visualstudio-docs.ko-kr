---
description: 디버그 엔진 (DEs) 및 세션 디버그 관리자 (SDM)에서 프로그램 노드를 사용할 수 있도록 합니다.
title: IDebugProgramPublisher2::P ublishProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 56d407e22aabb396b331c14047f5a1753a5adf09
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161328"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
디버그 엔진 (DEs) 및 세션 디버그 관리자 (SDM)에서 프로그램 노드를 사용할 수 있도록 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>매개 변수
`pProgramNode`\
진행 사용할 수 있도록 설정할 프로그램 노드를 나타내는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 방법을 사용 하면 디버깅을 위해 프로그램을 선택 하 고 시작 하기 전에 정보를 쿼리할 수 있습니다.

 가용성에서 프로그램 노드를 제거 하려면 [unpublishprogramnode 노드](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
