---
title: BP_REQUEST_INFO2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737885"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
공급업체 GUID, 제약 조건 및 추적 점을 포함하여 중단점을 구현하는 데 필요한 정보를 포함합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>멤버
`dwFields`\
채워지는지 지정하는 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 열거형의 플래그 조합입니다.

`guidLanguage`\
언어 GUID입니다.

`bpLocation`\
중단점 위치의 유형을 지정하는 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조입니다.

`pProgram`\
중단점이 발생하는 응용 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체입니다.

`bstrProgramName`\
중단점이 발생하는 응용 프로그램의 이름입니다.

`pThread`\
중단점이 발생하는 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

`bstrThreadName`\
중단점이 발생하는 스레드의 이름입니다.

`bpCondition`\
중단점이 발사되는 조건을 설명하는 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 구조입니다.

`bpPassCount`\
중단점의 통과 개수 정보를 포함하는 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 구조입니다.

`dwFlags`\
요청된 중단점에 대한 플래그를 지정하는 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 열거형의 플래그 조합입니다.

`guidVendor`\
공급 업체의 GUID. null 값일 수 있습니다.

`bstrConstraint`\
중단점 구속조건의 이름입니다. null 값일 수 있습니다.

`bstrTracepoint`\
추적점의 이름입니다. null 값일 수 있습니다.

## <a name="remarks"></a>설명
이 구조는 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) 메서드에 의해 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
