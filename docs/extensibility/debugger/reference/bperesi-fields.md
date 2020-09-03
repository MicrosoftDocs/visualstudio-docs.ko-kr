---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737759"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
실패 한 중단점 해결에 대 한 정보를 검색할 정보를 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>필드
`PERESI_BPRESLOCATION`\
`bpResLocation` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 구조체의 (중단점 확인 위치) 필드를 초기화/사용 합니다.

`BPERESI_PROGRAM`\
`pProgram`구조체의 필드를 초기화/사용 `BP_ERROR_RESOLUTION_INFO` 합니다.

`BPERESI_THREAD`\
`pThread`구조체의 필드를 초기화/사용 `BP_ERROR_RESOLUTION_INFO` 합니다.

`BPERESI_MESSAGE`\
`bstrMessage`구조체의 필드를 초기화/사용 `BP_ERROR_RESOLUTION_INFO` 합니다.

`BPERESI_TYPE`\
`dwType`구조체의 (중단점 형식) 필드를 초기화/사용 `BP_ERROR_RESOLUTION_INFO` 합니다.

`BPERESI_ALLFIELDS`\
구조체의 모든 필드를 초기화/사용 `BP_ERROR_RESOLUTION_INFO` 합니다.

## <a name="remarks"></a>설명
초기화할 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 구조체의 필드를 나타내기 위해 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) 메서드에 매개 변수로 전달 됩니다.

이러한 값은 구조체에서 사용 되는 필드 `BP_ERROR_RESOLUTION_INFO` 및 해당 구조가 반환 될 때 유효한 필드를 표시 하는 데도 사용 됩니다.

이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
