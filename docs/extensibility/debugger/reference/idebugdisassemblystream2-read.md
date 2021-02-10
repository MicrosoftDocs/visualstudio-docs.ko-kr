---
title: 'IDebugDisassemblyStream2:: Read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 720850096e7099ed95cbc5fa914bebb2bee580ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944669"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
디스어셈블리 스트림의 현재 위치에서 시작 하는 명령을 읽습니다.

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
진행 분해할 명령의 수입니다. 이 값은 배열의 최대 길이 이기도 합니다 `prgDisassembly` .

`dwFields`\
진행 에서 채울 필드를 나타내는 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 열거형의 플래그 조합입니다 `prgDisassembly` .

`pdwInstructionsRead`\
제한이 실제로 디스어셈블 된 명령의 수를 반환 합니다.

`prgDisassembly`\
제한이 디스어셈블 코드를 사용 하 여 채워진 [Disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) 구조의 배열로, 디스어셈블 된 명령 당 하나의 구조입니다. 이 배열의 길이는 매개 변수에 의해 결정 됩니다 `dwInstructions` .

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 현재 범위에서 사용할 수 있는 최대 명령 수는 [Getsize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) 메서드를 호출 하 여 가져올 수 있습니다.

 다음 명령을 읽어올 현재 위치는 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) 메서드를 호출 하 여 변경할 수 있습니다.

 `DSF_OPERANDS_SYMBOLS`매개 변수의 플래그에 플래그를 추가 `DSF_OPERANDS` `dwFields` 하 여 명령을 디스어셈블 할 때 기호 이름을 사용 해야 함을 나타낼 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
