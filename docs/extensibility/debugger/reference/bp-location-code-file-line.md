---
description: 코드 소스 파일의 특정 줄에 있는 중단점의 위치에 대 한 데이터를 포함 합니다.
title: BP_LOCATION_CODE_FILE_LINE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 3711123fd41a0c5cc4adc2e2d90791cf6fe483bf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078229"
---
# <a name="bp_location_code_file_line"></a>BP_LOCATION_CODE_FILE_LINE
코드 소스 파일의 특정 줄에 있는 중단점의 위치에 대 한 데이터를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>멤버
`bstrContext`\
중단점의 컨텍스트 (일반적으로 호출 스택에 표시 되는 메서드 또는 함수 이름)입니다.

`pDocPos`\
중단점의 문서 위치를 나타내는 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 개체입니다.

## <a name="remarks"></a>설명
이 구조체는 공용 구조체의 일부로 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 구조체의 멤버입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
