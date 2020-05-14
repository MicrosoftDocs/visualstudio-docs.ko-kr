---
title: DISASSEMBLY_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737377"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
분해할 플래그를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>필드
`DF_DOCUMENTCHANGE`\
이 명령이 이전 명령과 다른 문서에 있음을 나타냅니다.

`DF_DISABLED`\
이 명령이 실행되지 않음을 나타냅니다.

`DF_INSTRUCTION_ACTIVE`\
이 명령이 실행할 다음 명령 중 하나임을 나타냅니다(두 개 이상 있을 수 있음).

`DF_DATA`\
이 명령은 코드가 아닌 실제로 데이터임을 나타냅니다.

`DF_HASSOURCE`\
이 명령에 소스가 있음을 나타냅니다. 프로파일링 또는 가비지 수집 코드와 같은 일부 지침에는 해당 소스가 없습니다.

`DF_DOCUMENT_CHECKSUM`\
필드에 `bstrDocumentUrl` 문서 URL 다음의 체크섬 데이터가 포함되어 있음을 나타냅니다. 체크섬 데이터가 저장되는 방법에 대한 [디스어셈블리데이터](../../../extensibility/debugger/reference/disassemblydata.md) 구조에 대한 비고 섹션을 참조하십시오.

## <a name="remarks"></a>설명
`dwFlags` [디스어셈블리데이터](../../../extensibility/debugger/reference/disassemblydata.md) 구조의 멤버로 사용됩니다.

이러한 플래그는 약간 으로 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
