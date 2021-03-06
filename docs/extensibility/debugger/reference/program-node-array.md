---
description: 관련 프로그램을 설명 하는 개체의 배열을 포함 합니다.
title: PROGRAM_NODE_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b1397737003216b843d893af696a5ad14607a19
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079529"
---
# <a name="program_node_array"></a>PROGRAM_NODE_ARRAY
관련 프로그램을 설명 하는 개체의 배열을 포함 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagPROGRAM_NODE_ARRAY {
   DWORD                dwCount;
   IDebugProgramNode2** Members;
} PROGRAM_NODE_ARRAY;
```

```csharp
public struct tagPROGRAM_NODE_ARRAY {
   public uint                 dwCount;
   public IDebugProgramNode2[] Members;
}
```

## <a name="members"></a>멤버
 `dwCount`\
 배열에 있는 개체의 수 `Members` 입니다.

 `Members`\
 요청 된 프로그램을 설명 하는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체의 배열입니다.

## <a name="remarks"></a>설명
 이 구조는 [Getproviderprocessdata](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 메서드를 호출 하 여 차례로 채워지는 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 구조체의 일부입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
