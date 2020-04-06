---
title: BPREQI_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737754"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
중단점 요청에 대해 검색할 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>필드
`BPREQI_BPLOCATION`\
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 또는 BP_REQUEST_INFO2 `bpLocation` 구조의 (중단점 위치) [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 필드를 초기화/사용합니다.

`BPREQI_LANGUAGE`\
또는 구조체의 `guidLanguage` `BP_REQUEST_INFO2` 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_PROGRAM`\
또는 구조체의 `pProgram` `BP_REQUEST_INFO2` 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_PROGRAMNAME`\
또는 구조체의 `bstrProgramName` `BP_REQUEST_INFO2` 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_THREAD`\
또는 구조체의 `pThread` `BP_REQUEST_INFO2` 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_THREADNAME`\
또는 구조체의 `bstrThreadName` `BP_REQUEST_INFO2` 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_PASSCOUNT`\
또는 구조체의 `bpPassCount` `BP_REQUEST_INFO2` 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_CONDITION`\
또는 구조체의 `bpCondition` `BP_REQUEST_INFO2` (중단점 조건) 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_FLAGS`\
또는 구조체의 `dwFlags` `BP_REQUEST_INFO2` 필드를 초기화/사용합니다. `BP_REQUEST_INFO`

`BPREQI_ALLOLDFIELDS`\
`BP_REQUEST_INFO` 구조체에 대한 모든 필드를 초기화/사용합니다.

`BPREQI_VENDOR`\
`BP_REQUEST_INFO2` 구조 `guidVendor` 필드를 초기화/사용합니다.

`BPREQI_CONSTRAINT`\
`BP_REQUEST_INFO2` 구조 `bstrConstraint` 필드를 초기화/사용합니다.

`BPREQI_TRACEPOINT`\
`BP_REQUEST_INFO2` 구조 `bstrTracepoint` 필드를 초기화/사용합니다.

`BPREQI_ALLFIELDS`\
구조에 대한 모든 `BP_REQUEST_INFO2` 필드를 지정합니다.

## <a name="remarks"></a>설명
[GetRequestInfo에](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 인수로 전달 되고 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조의 필드를 초기화할 필드를 지정하는 [메서드를 BP_REQUEST_INFO.](../../../extensibility/debugger/reference/bp-request-info.md)

이러한 플래그는 `BP_REQUEST_INFO` 각 구조가 반환될 `BP_REQUEST_INFO2` 때 사용되는 및 구조의 필드와 유효한 필드를 나타내는 데도 사용됩니다.

이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
