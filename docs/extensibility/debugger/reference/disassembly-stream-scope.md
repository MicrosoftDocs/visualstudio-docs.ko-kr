---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737264"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
디스어셈블리 스트림의 범위를 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>필드
`DSS_HUGE`\
코드 컨텍스트를 디스어셈블 하면 클라이언트에서 일반적으로 단일 호출로 검색 하는 것 보다 많은 출력을 생성 하도록 지정 합니다.

`DSS_FUNCTION`\
코드 컨텍스트에 포함 된 함수를 디스어셈블 하도록 지정 합니다. [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 메서드에서 반환 될 때 디스어셈블리 스트림이 함수를 나타내도록 지정 합니다.

`DSS_MODULE`\
메서드에서 반환 되는 경우 `IDebugDisassemblyStream2::GetScope` 디스어셈블리 스트림이 모듈을 나타내도록 지정 합니다.

`DSS_ALL`\
전체 주소 공간에 대 한 디스어셈블리를 지정 합니다.

## <a name="remarks"></a>설명
[Getdisassemblystream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 메서드에 인수로 전달 되 고 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 메서드에서 반환 됩니다.

이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
