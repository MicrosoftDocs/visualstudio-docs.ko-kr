---
title: DISASSEMBLY_STREAM_SCOPE | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737264"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
디스어셈블리 스트림의 범위를 지정합니다.

## <a name="syntax"></a>구문

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
코드 컨텍스트를 분해하면 클라이언트가 일반적으로 단일 호출에서 검색하려는 것보다 더 많은 출력을 생성하도록 지정합니다.

`DSS_FUNCTION`\
코드 컨텍스트에 포함된 함수를 분해해야 한다고 지정합니다. [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 메서드에서 반환할 때 디스어셈블리 스트림이 함수를 나타내지 는 지정합니다.

`DSS_MODULE`\
메서드에서 `IDebugDisassemblyStream2::GetScope` 반환될 때 분해 스트림이 모듈을 나타내지 지정합니다.

`DSS_ALL`\
전체 주소 공간에 대한 디스어셈블리를 지정합니다.

## <a name="remarks"></a>설명
[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 메서드에 인수로 전달 되 고 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 메서드에 의해 반환 됩니다.

이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
