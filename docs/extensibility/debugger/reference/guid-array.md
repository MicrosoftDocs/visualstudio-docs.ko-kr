---
description: 사용 가능한 디버그 엔진에 대 한 고유 식별자 배열을 설명 합니다.
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbdc8465bef0795649fef5b169a221a3e7b7178c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162422"
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

## <a name="see-also"></a>참고 항목
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
