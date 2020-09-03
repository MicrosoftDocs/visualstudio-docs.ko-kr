---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713773"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
이 구조는 컴퓨터에서 실행 되는 프로세스에 대 한 정보를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>멤버
 `Fields`\
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) 열거형의 플래그 조합으로, 입력 된 필드를 나타냅니다.

 `ProgramNodes`\
 프로그램 노드의 배열을 포함 하는 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) 구조체입니다.

 `fIsDebuggerPresent`\
 디버거가 실행 중인 경우 0이 아닌 ()이 고 `TRUE` [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , `FALSE` 그렇지 않으면 0 ()입니다.

## <a name="remarks"></a>설명
 이 구조는 채워진 [Getproviderprocessdata](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 메서드에 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
