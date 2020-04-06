---
title: IDebugProcessEx2::추가암시프로그램노드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723402"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
이 메서드는 지정된 각 디버그 엔진(DE)에 대한 프로그램 노드를 추가합니다.

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
【인】 `GUID` 프로그램을 시작하는 데 사용할 DE(자체 프로그램 노드를 추가하는 것으로 가정)입니다.

`rgguidSpecificEngines`\
【인】 `GUID`프로그램 노드가 추가될 DEs의 배열입니다.

`celtSpecificEngines`\
【인】 배열의 `GUID`s 수입니다. `rgguidSpecificEngines`

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
- [프로그램 노드는](../../../extensibility/debugger/program-nodes.md) 프로그램을 시작할 때 `rgguidSpecificEngines`자체 프로그램 노드를 추가하는 것으로 `guidLaunchingEngine`가정되는 시작 엔진(제공된 대로)을 제외한 각 DE에 대해 추가됩니다.

## <a name="see-also"></a>참조
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [프로그램 노드](../../../extensibility/debugger/program-nodes.md)
