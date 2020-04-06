---
title: IDebugThread2::SetNextStatement | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718655"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
현재 명령 포인터를 지정된 코드 컨텍스트로 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>매개 변수
`pStackFrame`\
향후 사용을 위해 예약; null 값으로 설정합니다.

`pCodeContext`\
【인】 실행될 코드 위치와 해당 컨텍스트를 설명하는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 다음 표에서는 다른 가능한 값을 보여 주며 있습니다.

|값|Description|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|다음 문은 프레임 스택의 더 깊은 스택 프레임에 있을 수 없습니다.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|다음 문은 스택의 프레임과 연결되지 않습니다.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|일부 디버그 엔진은 예외 후 다음 문을 설정할 수 없습니다.|

## <a name="remarks"></a>설명
 명령 포인터는 실행할 다음 명령 또는 문을 나타냅니다. 이 메서드는 소스 코드 줄을 다시 시도하거나 실행을 강제로 다른 함수에서 계속하도록 하는 데 사용됩니다.

## <a name="see-also"></a>참조
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
