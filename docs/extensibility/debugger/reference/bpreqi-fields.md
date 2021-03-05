---
description: 중단점 요청에 대 한 정보를 검색할 정보를 지정 합니다.
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f7ee5d8dbf48ad8d1b07512727b1b91635ab990
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162461"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
중단점 요청에 대 한 정보를 검색할 정보를 지정 합니다.

## <a name="syntax"></a>Syntax

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
`bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 또는 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조체의 (중단점 위치) 필드를 초기화/사용 합니다.

`BPREQI_LANGUAGE`\
`guidLanguage`또는 구조체의 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_PROGRAM`\
`pProgram`또는 구조체의 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_PROGRAMNAME`\
`bstrProgramName`또는 구조체의 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_THREAD`\
`pThread`또는 구조체의 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_THREADNAME`\
`bstrThreadName`또는 구조체의 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_PASSCOUNT`\
`bpPassCount`또는 구조체의 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_CONDITION`\
`bpCondition`또는 구조체의 (중단점 조건) 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_FLAGS`\
`dwFlags`또는 구조체의 필드를 초기화/ `BP_REQUEST_INFO` 사용 `BP_REQUEST_INFO2` 합니다.

`BPREQI_ALLOLDFIELDS`\
구조체의에 대 한 모든 필드를 초기화/사용 `BP_REQUEST_INFO` 합니다.

`BPREQI_VENDOR`\
구조체의 필드를 초기화/사용 `guidVendor` `BP_REQUEST_INFO2` 합니다.

`BPREQI_CONSTRAINT`\
구조체의 필드를 초기화/사용 `bstrConstraint` `BP_REQUEST_INFO2` 합니다.

`BPREQI_TRACEPOINT`\
구조체의 필드를 초기화/사용 `bstrTracepoint` `BP_REQUEST_INFO2` 합니다.

`BPREQI_ALLFIELDS`\
구조체의 모든 필드를 지정 합니다 `BP_REQUEST_INFO2` .

## <a name="remarks"></a>설명
는 [Getrequestinfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 에 대 한 인수로 전달 되 고 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 메서드는 초기화할 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조체의 필드를 지정 하는 데 사용할 수 있습니다.

이러한 플래그는 사용 되는 `BP_REQUEST_INFO` 및 구조체의 필드 `BP_REQUEST_INFO2` 와 각 구조가 반환 될 때 유효한 지 여부를 나타내는 데에도 사용 됩니다.

이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
