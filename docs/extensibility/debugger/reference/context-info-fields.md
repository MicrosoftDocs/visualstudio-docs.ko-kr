---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c0d67afa2b20e239180848ef1e68d0f0a0c3079
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912966"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
메모리 컨텍스트 관련 정보를 검색할 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>필드
`CIF_MODULEURL`\
`bstrModuleUrl` [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 구조체의 필드를 초기화/사용 합니다.

`CIF_FUNCTION`\
`bstrFunction`구조체의 필드를 초기화/사용 `CONTEXT_INFO` 합니다.

`CIF_FUNCTIONOFFSET`\
`posFunctionOffset`구조체의 필드를 초기화/사용 `CONTEXT_INFO` 합니다.

`CIF_ADDRESS`\
`bstrAddress`구조체의 필드를 초기화/사용 `CONTEXT_INFO` 합니다.

`CIF_ADDRESSOFFSET`\
`bstrAddressOffset`구조체의 필드를 초기화/사용 `CONTEXT_INFO` 합니다.

`CIF_ALLFIELDS`\
구조체의 모든 필드를 초기화/사용 `CONTEXT_INFO` 합니다.

## <a name="remarks"></a>설명
이러한 값은 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 메서드에 매개 변수를 전달 하 여 초기화할 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 구조체의 필드를 표시 합니다.

이러한 플래그는 구조체가 반환 될 때 사용 되는 구조체의 필드 및 유효한 필드를 표시 하는 데도 사용 됩니다 `CONTEXT_INFO` .

이러한 값은 비트 or와 함께 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
