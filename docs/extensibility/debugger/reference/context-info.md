---
description: 이 구조는 메모리 컨텍스트 또는 코드 컨텍스트를 설명 합니다.
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58b524de5d2d230e240ae7338190568ccfe6fb2a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096488"
---
# <a name="context_info"></a>CONTEXT_INFO
이 구조는 메모리 컨텍스트 또는 코드 컨텍스트를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>멤버
`dwFields`\
채울 필드를 지정 하는 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) 열거형의 플래그 조합입니다<strong>.</strong>

`bstrModuleUrl`\
컨텍스트가 있는 모듈의 이름입니다.

`bstrFunction`\
컨텍스트가 있는 함수 이름입니다.

`posFunctionOffset`\
코드 컨텍스트와 연결 된 함수의 줄 및 열 오프셋을 식별 하는 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다.

`bstrAddress`\
지정 된 컨텍스트가 있는 코드의 주소입니다.

`bstrAddressOffset`\
지정 된 컨텍스트가 있는 코드에서 주소의 오프셋입니다.

`bstrAddressAbsolute`\
지정 된 컨텍스트가 있는 메모리의 절대 주소입니다.

## <a name="remarks"></a>설명
이 구조체는 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 메서드에 대 한 호출에서 반환 됩니다.

이 구조체의 일반적인 용도는 **메모리** 디버그 창을 지 원하는 것입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
