---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737359"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
디스어셈블리 필드와 관련 하 여 검색할 정보를 지정 합니다.

## <a name="syntax"></a>Syntax

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
필드를 초기화/사용 `bstrAddress` 합니다.

`DSF_ADDRESSOFFSET`\
필드를 초기화/사용 `bstrAddressOffset` 합니다.

`DSF_CODEBYTES`\
필드를 초기화/사용 `bstrCodeBytes` 합니다.

`DSF_OPCODE`\
필드를 초기화/사용 `bstrOpCode` 합니다.

`DSF_OPERANDS`\
필드를 초기화/사용 `bstrOperands` 합니다.

`DSF_SYMBOL`\
필드를 초기화/사용 `bstrSymbol` 합니다.

`DSF_CODELOCATIONID`\
필드를 초기화/사용 `uCodeLocationId` 합니다.

`DSF_POSITION`\
및 필드를 초기화/사용 `posBeg` `posEnd` 합니다.

`DSF_DOCUMENTURL`\
필드를 초기화/사용 `bstrDocumentUrl` 합니다.

`DSF_BYTEOFFSET`\
필드를 초기화/사용 `dwByteOffset` 합니다.

`DSF_FLAGS`\
`dwFlags`([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) 필드를 초기화/사용 합니다.

`DSF_OPERANDS_SYMBOLS`\
필드에 기호 이름을 포함 `bstrOperands` 합니다.

`DSF_ALL`\
디스어셈블리 스트림에 대 한 모든 필드를 지정 합니다.

## <a name="remarks"></a>설명
초기화 될 [Disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) 구조체의 필드를 나타내기 위해를 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드에 매개 변수로 전달 합니다.

구조체 `dwFields` 의 멤버에서 사용 되는 `DisassemblyData` 필드 및 구조가 반환 될 때 유효한 필드를 표시 하는 데 사용 됩니다.

이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
