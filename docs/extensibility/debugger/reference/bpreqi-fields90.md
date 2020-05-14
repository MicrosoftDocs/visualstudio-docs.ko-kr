---
title: BPREQI_FIELDS90 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737741"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
중단점 요청에 대해 검색할 정보를 지정하는 유효한 값을 여밈합니다. 이 열거형은 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 열거를 확장합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>필드
`BPREQI90_BPLOCATION`\
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 또는 BP_REQUEST_INFO2 `bpLocation` 구조의 (중단점 위치) [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 필드를 초기화하거나 사용합니다.

`BPREQI90_LANGUAGE`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `guidLanguage` 필드를 초기화하거나 사용합니다.

`BPREQI90_PROGRAM`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `pProgram` 필드를 초기화하거나 사용합니다.

`BPREQI90_PROGRAMNAME`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `bstrProgramName` 필드를 초기화하거나 사용합니다.

`BPREQI90_THREAD`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `pThread` 필드를 초기화하거나 사용합니다.

`BPREQI90_THREADNAME`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `bstrThreadName` 필드를 초기화하거나 사용합니다.

`BPREQI90_PASSCOUNT`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `bpPassCount` 필드를 초기화하거나 사용합니다.

`BPREQI90_CONDITION`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `bpCondition` (중단점 조건) 필드를 초기화하거나 사용합니다.

`BPREQI90_FLAGS`\
`BP_REQUEST_INFO` 또는 `BP_REQUEST_INFO2` 구조의 `dwFlags` 필드를 초기화하거나 사용합니다.

`BPREQI90_ALLOLDFIELDS`\
`BP_REQUEST_INFO` 구조에 대한 모든 필드를 초기화하거나 사용합니다.

`BPREQI90_VENDOR`\
`BP_REQUEST_INFO2` 구조 `guidVendor` 필드를 초기화하거나 사용합니다.

`BPREQI90_CONSTRAINT`\
`BP_REQUEST_INFO2` 구조 `bstrConstraint` 필드를 초기화하거나 사용합니다.

`BPREQI90_TRACEPOINT`\
`BP_REQUEST_INFO2` 구조 `bstrTracepoint` 필드를 초기화하거나 사용합니다.

`BPREQI90_MACROTRACEPOINT`\
`BP_REQUEST_INFO2` 구조 `bstrMacroTracepoint` 필드를 초기화하거나 사용합니다. BPREQI_ALLFIELDS 이 필드를 포함하지 않습니다.

`BPREQI90_ALLFIELDS`\
구조에 대한 모든 `BP_REQUEST_INFO2` 필드를 지정합니다.

## <a name="requirements"></a>요구 사항
헤더: Msdbg90.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
