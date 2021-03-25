---
description: 사용 가능한 디버그 엔진에 대 한 고유 식별자 배열을 설명 합니다.
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 504c917d9fb2b1e2cd15ac8154faf70eaf98beec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054584"
---
# <a name="guid_array"></a>GUID_ARRAY
사용 가능한 디버그 엔진에 대 한 고유 식별자 배열을 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>멤버
`dwCount`\
배열의 고유 식별자 수입니다.

`Members`\
고유 식별자가 포함 된 배열입니다.

## <a name="remarks"></a>설명
이 구조체는 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) 메서드에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: Msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
