---
title: 아이디버그디스어셈블리스트림2::겟사이즈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75fa12b1e9e70601626667dd3707f1e230f5de0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732109"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
이 디스어셈블리 스트림의 지침에서 크기를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>매개 변수
`pnSize`\
【아웃】 지침에 따라 크기를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드에서 반환 된 값을 사용 하 고 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 구조의 배열을 할당 하는 데 사용할 수 있습니다.다음 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드에 전달 됩니다.

## <a name="see-also"></a>참조
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
