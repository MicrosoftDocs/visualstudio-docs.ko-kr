---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738073"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
중단점의 오류 유형을 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>필드
`BPET_NONE`\
중단점 오류를 지정 하지 않습니다.

`BPET_TYPE_WARNING`\
경고 스타일 중단점 오류를 지정 합니다.

`BPET_TYPE_ERROR`\
오류 스타일 중단점 오류를 지정 합니다.

`BPET_SEV_HIGH`\
심각도가 높은 중단점 오류를 지정 합니다.

`BPET_SEV_GENERAL`\
중간 심각도 중단점 오류를 지정 합니다.

`BPET_SEV_LOW`\
낮은 심각도 중단점 오류를 지정 합니다.

`BPET_TYPE_MASK`\
마스크 스타일 중단점 오류를 지정 합니다.

`BPET_SEV_MASK`\
심각도-마스크 스타일의 중단점 오류를 지정 합니다.

`BPET_GENERAL_WARNING`\
일반 경고 스타일 중단점 오류를 지정 합니다.

`BPET_GENERAL_ERROR`\
일반 오류 스타일 중단점 오류를 지정 합니다.

`BPET_ALL`\
모든 중단점 오류 유형을 지정 합니다.

## <a name="remarks"></a>설명
이러한 값은 비트 and와 결합 되어 `OR` `dwType` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 구조체의 멤버에 사용할 수 있습니다. [Enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) 메서드에 매개 변수로 전달 됩니다.

중단점 오류 형식은 형식 및 심각도로 구성 됩니다. 즉, 중단점 오류 형식은 단지 형식 (예:, `BPET_TYPE_ERROR` ) 또는 심각도 (예:)만이 아닌 형식입니다 `BPET_SEV_GENERAL` . `BPET_GENERAL_WARNING` 및 `BPET_GENERAL_ERROR` 는 일반 경고 및 오류 중단점에 대해 미리 정의 된 값을 제공 합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
