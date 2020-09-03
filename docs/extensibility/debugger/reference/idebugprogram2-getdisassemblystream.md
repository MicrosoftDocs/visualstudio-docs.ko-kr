---
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722870"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
이 프로그램 또는이 프로그램의 일부에 대 한 디스어셈블리 스트림을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>매개 변수
`dwScope`\
진행 디스어셈블리 스트림의 범위를 정의 하는 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 열거형의 값을 지정 합니다.

`pCodeContext`\
진행 디스어셈블리 스트림을 시작할 위치를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

`ppDisassemblyStream`\
제한이 디스어셈블리 스트림을 나타내는 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_DISASM_NOTSUPPORTED`이 특정 아키텍처에 대해 디스어셈블리가 지원 되지 않는 경우를 반환 합니다.

## <a name="remarks"></a>설명
 `dwScopes`매개 변수에 `DSS_HUGE` [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 열거형 집합의 플래그가 있는 경우 디스어셈블리는 전체 파일 또는 모듈의 경우와 같이 많은 수의 디스어셈블리 명령을 반환 합니다. `DSS_HUGE`플래그가 설정 되지 않은 경우 디스어셈블리는 일반적으로 단일 함수의 작은 영역으로 제한 될 것으로 예상 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
