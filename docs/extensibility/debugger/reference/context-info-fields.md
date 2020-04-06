---
title: CONTEXT_INFO_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737597"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
메모리 컨텍스트에 대해 검색할 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_CONTEXT_INFO_FIELDS {
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
[CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 구조의 `bstrModuleUrl` 필드를 초기화/사용합니다.

`CIF_FUNCTION`\
`CONTEXT_INFO` 구조의 `bstrFunction` 필드를 초기화/사용합니다.

`CIF_FUNCTIONOFFSET`\
`CONTEXT_INFO` 구조의 `posFunctionOffset` 필드를 초기화/사용합니다.

`CIF_ADDRESS`\
`CONTEXT_INFO` 구조의 `bstrAddress` 필드를 초기화/사용합니다.

`CIF_ADDRESSOFFSET`\
`CONTEXT_INFO` 구조의 `bstrAddressOffset` 필드를 초기화/사용합니다.

`CIF_ALLFIELDS`\
`CONTEXT_INFO` 구조체의 모든 필드를 초기화/사용합니다.

## <a name="remarks"></a>설명
이러한 값은 CONTEXT_INFO [구조의](../../../extensibility/debugger/reference/context-info.md) 필드를 초기화할 필드를 나타내기 위해 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 메서드에 매개 변수를 전달합니다.

이러한 플래그는 구조의 어떤 필드가 `CONTEXT_INFO` 사용되고 구조가 반환될 때 유효한지 나타내는 데도 사용됩니다.

이러한 값은 비트 OR와 결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Context_info](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
