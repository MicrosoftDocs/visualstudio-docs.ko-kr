---
title: BP_LOCATION_CODE_ADDRESS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: c215630e522adabdbd285e00d4bcd87cae22a931
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738031"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
코드의 주소에서 중단점의 위치를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>멤버
`bstrContext`\
중단점의 컨텍스트(일반적으로 호출 스택에서 볼 수 있는 메서드 또는 함수 이름)입니다.

`bstrModuleUrl`\
중단점을 포함하는 모듈의 URL입니다.

`bstrFunction`\
중단점을 포함하는 함수의 이름입니다.

`bstrAddress`\
[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체에 바인딩하기 위해 식 계산기에 의해 구문 분석되는 중단점의 주소입니다.

## <a name="remarks"></a>설명
이 구조는 공용 구조의 일부로 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조의 멤버입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
