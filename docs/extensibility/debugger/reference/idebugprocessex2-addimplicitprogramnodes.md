---
description: 이 메서드는 지정 된 각 디버그 엔진 (DE)에 대해 프로그램 노드를 추가 합니다.
title: 'IDebugProcessEx2:: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3a4c6446c2106d79dd14fc0378fc848eac3df18
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159993"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
이 메서드는 지정 된 각 디버그 엔진 (DE)에 대해 프로그램 노드를 추가 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>매개 변수
`guidLaunchingEngine`\
진행 `GUID` 프로그램을 시작 하는 데 사용 되 고 자체 프로그램 노드를 추가 하는 것으로 간주 되는 DE의입니다.

`rgguidSpecificEngines`\
진행 `GUID`프로그램 노드가 추가 될 DEs의 배열입니다.

`celtSpecificEngines`\
진행 `GUID`배열에 있는의 수입니다 `rgguidSpecificEngines` .

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
- 프로그램 [노드](../../../extensibility/debugger/program-nodes.md) 는 `rgguidSpecificEngines` `guidLaunchingEngine` 프로그램을 시작할 때 자체 프로그램 노드를 추가 하는 것으로 간주 되는 시작 엔진을 제외 하 고에 나열 된 각 DE에 대해 추가 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [프로그램 노드](../../../extensibility/debugger/program-nodes.md)
