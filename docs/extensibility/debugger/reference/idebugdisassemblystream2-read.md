---
title: '[이디버그디스어셈블리스트림2::읽기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732099"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
디스어셈블리 스트림의 현재 위치에서 시작하는 지침을 읽습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>매개 변수
`dwInstructions`\
【인】 분해할 지침의 수입니다. 이 값은 배열의 최대 `prgDisassembly` 길이이기도 합니다.

`dwFields`\
【인】 입력할 필드를 나타내는 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 열거형의 `prgDisassembly` 플래그 조합입니다.

`pdwInstructionsRead`\
【아웃】 실제로 분해된 명령 수를 반환합니다.

`prgDisassembly`\
【아웃】 분해된 코드로 채워진 [디스어셈블리데이터](../../../extensibility/debugger/reference/disassemblydata.md) 구조의 배열로, 분해된 명령당 하나의 구조입니다. 이 배열의 길이는 매개 `dwInstructions` 변수에 의해 결정됩니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 현재 범위에서 사용할 수 있는 최대 명령 수는 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) 메서드를 호출하여 가져올 수 있습니다.

 Seek [메서드를](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 호출 하여 다음 명령을 읽는 현재 위치를 변경할 수 있습니다.

 플래그를 `DSF_OPERANDS_SYMBOLS` 매개 변수의 `DSF_OPERANDS` 플래그에 추가하여 명령을 분해할 때 기호 이름을 사용해야 함을 나타낼 수 있습니다. `dwFields`

## <a name="see-also"></a>참조
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
