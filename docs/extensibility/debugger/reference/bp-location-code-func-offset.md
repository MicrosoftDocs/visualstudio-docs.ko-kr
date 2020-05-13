---
title: BP_LOCATION_CODE_FUNC_OFFSET | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 32331a5b628c27dc79d6a2e5919c8d268c96a3aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738001"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
코드의 함수에서 중단점의 오프셋 위치를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>멤버
`bstrContext`\
중단점의 컨텍스트(일반적으로 호출 스택에서 볼 수 있는 메서드 또는 함수 이름)입니다.

`pFuncPos`\
함수의 이름과 함수의 시작 부분에서 상대 위치를 설명하는 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) 개체입니다.

## <a name="remarks"></a>설명
이 구조는 공용 구조의 일부로 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조의 멤버입니다.

멤버는 `pFuncPos` 함수 중단점을 설정할 위치를 나타냅니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
