---
description: GUID의 목록을 포함 하는 구조체입니다.
title: CONST_GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6bcaff422702b9c1c381c1d4e9199bb4578a0f7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059511"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
의 목록을 보유 하는 구조체입니다 `GUID` .

## <a name="syntax"></a>구문

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>멤버
`dwCount`\
`GUID`배열에 있는의 수 `Members` 입니다.

`Members`\
S의 배열 `GUID` 입니다.

## <a name="remarks"></a>설명
이 구조체는 WatchForProviderEvents [program](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) 메서드에 전달 되며 [Getproviderprocessdata](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 및 [](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) 메서드에서 반환 됩니다.

이 구조체 인스턴스의 소유자는 할당 된 모든 메모리를 해제 해야 합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
