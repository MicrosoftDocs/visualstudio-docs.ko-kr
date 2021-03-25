---
description: 코드의 주소에서 중단점의 위치를 설명 합니다.
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 0b181f82c7364797f246730cb6a82075d7040af1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085236"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
코드의 주소에서 중단점의 위치를 설명 합니다.

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
중단점의 컨텍스트 (일반적으로 호출 스택에 표시 되는 메서드 또는 함수 이름)입니다.

`bstrModuleUrl`\
중단점을 포함 하는 모듈의 URL입니다.

`bstrFunction`\
중단점이 포함 된 함수의 이름입니다.

`bstrAddress`\
식 계산기가 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체에 바인딩하기 위해 구문 분석 하는 중단점의 주소입니다.

## <a name="remarks"></a>설명
이 구조체는 공용 구조체의 일부로 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조체의 멤버입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
