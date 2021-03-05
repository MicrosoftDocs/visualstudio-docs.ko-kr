---
description: 데이터 중단점을 바인딩한 결과를 설명 합니다.
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d33f05036965e500a007b97e7575a5c0d788158
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162617"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
데이터 중단점을 바인딩한 결과를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>멤버
`bstrDataExpr`\
바인딩된 데이터 식입니다.

`bstrFunc`\
데이터 중단점이 바인딩된 함수의 이름입니다 (있는 경우).

`bstrImage`\
데이터 중단점이 바인딩된 모듈의 이름 (예: MyModule.dll)입니다.

`dwFlags`\
데이터 중단점을 구현 하는 방법을 설명 하는 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) 열거형의 값입니다.

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
