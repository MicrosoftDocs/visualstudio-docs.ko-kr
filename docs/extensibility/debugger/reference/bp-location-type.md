---
title: BP_LOCATION_TYPE | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737946"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
중단점 요청에 대한 중단점의 위치 유형을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>필드
`BPLT_NONE`\
중단점 위치를 지정하지 않습니다.

`BPLT_FILE_LINE`\
중단점의 위치 유형을 파일 줄로 지정합니다.

`BPLT_FUNC_OFFSET`\
중단점의 위치 유형을 함수 오프셋으로 지정합니다.

`BPLT_CONTEXT`\
중단점의 위치 유형을 컨텍스트로 지정합니다.

`BPLT_STRING`\
중단점의 위치 유형을 문자열로 지정합니다.

`BPLT_ADDRESS`\
중단점의 위치 유형을 주소로 지정합니다.

`BPLT_RESOLUTION`\
중단점의 위치 유형을 해상도로 지정합니다.

`BPLT_CODE_FILE_LINE`\
중단점의 위치 유형을 소스 코드 줄로 지정합니다.

`BPLT_CODE_FUNC_OFFSET`\
중단점의 위치 유형을 코드 함수 오프셋으로 지정합니다.

`BPLT_CODE_CONTEXT`\
중단점의 위치 유형을 코드 컨텍스트로 지정합니다.

`BPLT_CODE_STRING`\
중단점의 위치 형식을 코드 문자열로 지정합니다.

`BPLT_CODE_ADDRESS`\
중단점의 위치 유형을 코드 주소로 지정합니다.

`BPLT_DATA_STRING`\
중단점의 위치 유형을 데이터 문자열로 지정합니다.

`BPLT_TYPE_MASK`\
비트 마스크를 지정하여 중단점 유형을 값에서 추출할 수 있도록 합니다.

`BPLT_LOCATION_TYPE_MASK`\
중단점 위치 유형을 값에서 추출할 수 있도록 비트 마스크를 지정합니다.

## <a name="remarks"></a>설명
[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) 메서드에 매개 변수로 전달 되었습니다.

중단점 위치 유형은 중단점 유형과 위치 유형으로 구성됩니다. 즉, 중단점 위치 형식은 중단점 유형(예: `BPT_CODE`위치 유형)이 `BPLT_FILE_LINE`아닙니다. 현재 지원되는 모든 중단점 위치 유형에 대해 미리 정의된 상수는 `BPLT_DATA_STRING`이 열거형(through)에`BPLT_CODE_FILE_LINE` 포함됩니다.

`BPT_CODE``BPT_DATA` [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) 열거형의 구성원입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
