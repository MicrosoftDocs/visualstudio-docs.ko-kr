---
title: BP_LOCATION_CODE_STRING | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 0fc0d9a053faf69fde500333ab0faafa0e8d3448
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737988"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
사용자가 통합 개발 환경(IDE)에서 입력할 수 있는 문자열을 기반으로 코드 중단점을 설정하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>멤버
`bstrContext`\
코드 내의 중단점의 컨텍스트(일반적으로 호출 스택에서 볼 수 있는 메서드 또는 함수 이름)입니다.

`bstrCodeExpr`\
사용자가 코드 중단점을 설명하기 위해 입력하는 문자열입니다.

## <a name="remarks"></a>설명
이 구조는 공용 구조의 일부로 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조의 멤버입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
