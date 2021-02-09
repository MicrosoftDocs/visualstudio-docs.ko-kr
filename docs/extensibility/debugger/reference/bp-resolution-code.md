---
title: BP_RESOLUTION_CODE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f888c5cbee5747562af070d310a9ca5d8eea913
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901967"
---
# <a name="bp_resolution_code"></a>BP_RESOLUTION_CODE
코드 중단점의 위치를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_RESOLUTION_CODE {
    IDebugCodeContext2* pCodeContext;
} BP_RESOLUTION_CODE;
```

```csharp
public struct BP_RESOLUTION_CODE {
    public IDebugCodeContext2 pCodeContext;
};
```

## <a name="members"></a>구성원
`pCodeContext`\
코드에서 중단점의 위치를 식별 하는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

## <a name="remarks"></a>설명
이 구조체는 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 메서드에서 반환 하는 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조체의 멤버가 되는 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 구조체의 멤버입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
