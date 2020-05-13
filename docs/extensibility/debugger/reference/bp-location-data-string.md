---
title: BP_LOCATION_DATA_STRING | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737974"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
사용자가 통합 개발 환경(IDE)에서 입력할 수 있는 문자열을 기반으로 하는 데이터 중단점을 설정하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>멤버
`pThread`\
중단점이 발생하는 스레드를 나타내는 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 개체입니다.

`bstrContext`\
코드 내의 중단점의 컨텍스트(일반적으로 호출 스택에서 볼 수 있는 메서드 또는 함수 이름)입니다.

`bstrDataExpr`\
중단점을 설정하기 위해 사용자가 입력하는 데이터 문자열입니다.

`dwNumElements`\
중단점이 발생하는 데이터 문자열의 요소 수입니다.

## <a name="remarks"></a>설명
이 구조는 공용 구조의 일부로 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조의 멤버입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
