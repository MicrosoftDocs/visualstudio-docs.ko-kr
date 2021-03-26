---
description: 사용자가 IDE (통합 개발 환경)에서 입력할 수 있는 문자열을 기준으로 코드 중단점을 설정 하는 데 사용 됩니다.
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9c32a75e4976a81498033a656461d897e4f298a3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096774"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
사용자가 IDE (통합 개발 환경)에서 입력할 수 있는 문자열을 기준으로 코드 중단점을 설정 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>멤버
`bstrContext`\
코드 내의 중단점 컨텍스트 (일반적으로 호출 스택에 표시 되는 메서드 또는 함수 이름)입니다.

`bstrCodeExpr`\
사용자가 코드 중단점을 설명 하기 위해 입력 하는 문자열입니다.

## <a name="remarks"></a>설명
이 구조체는 공용 구조체의 일부로 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조체의 멤버입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
