---
title: DISASSEMBLY_STREAM_FIELDS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737359"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
분해 필드에 대해 검색할 정보를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>필드
`DSF_ADDRESS`\
`bstrAddress` 필드를 초기화/사용합니다.

`DSF_ADDRESSOFFSET`\
`bstrAddressOffset` 필드를 초기화/사용합니다.

`DSF_CODEBYTES`\
`bstrCodeBytes` 필드를 초기화/사용합니다.

`DSF_OPCODE`\
`bstrOpCode` 필드를 초기화/사용합니다.

`DSF_OPERANDS`\
`bstrOperands` 필드를 초기화/사용합니다.

`DSF_SYMBOL`\
`bstrSymbol` 필드를 초기화/사용합니다.

`DSF_CODELOCATIONID`\
`uCodeLocationId` 필드를 초기화/사용합니다.

`DSF_POSITION`\
`posBeg` 및 `posEnd` 필드를 초기화/사용합니다.

`DSF_DOCUMENTURL`\
`bstrDocumentUrl` 필드를 초기화/사용합니다.

`DSF_BYTEOFFSET`\
`dwByteOffset` 필드를 초기화/사용합니다.

`DSF_FLAGS`\
(DISASSEMBLY_FLAGS) 필드를 초기화/사용합니다.[DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) `dwFlags`

`DSF_OPERANDS_SYMBOLS`\
필드에 기호 이름을 `bstrOperands` 포함합니다.

`DSF_ALL`\
디스어셈블리 스트림에 대한 모든 필드를 지정합니다.

## <a name="remarks"></a>설명
[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 구조의 어떤 필드를 초기화할지 나타내기 [메서드에](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 매개 변수로 전달됩니다.

`DisassemblyData` 구조의 멤버에 `dwFields` 사용 되는 필드 와 구조가 반환 될 때 유효한 나타내는 데 사용 됩니다.

이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
