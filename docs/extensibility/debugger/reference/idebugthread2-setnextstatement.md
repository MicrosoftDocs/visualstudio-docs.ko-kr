---
title: 'IDebugThread2:: SetNextStatement | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718655"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
현재 명령 포인터를 지정 된 코드 컨텍스트로 설정 합니다.

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
나중에 사용 하도록 예약 되어 있습니다. 을 null 값으로 설정 합니다.

`pCodeContext`\
진행 실행할 코드 위치와 해당 컨텍스트를 설명 하는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음 표에서는 다른 가능한 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|다음 문은 프레임 스택에서 더 깊은 스택 프레임 안에 있을 수 없습니다.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|다음 문은 스택의 프레임에 연결 되지 않습니다.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|일부 디버그 엔진은 예외 후에 다음 문을 설정할 수 없습니다.|

## <a name="remarks"></a>설명
 명령 포인터는 실행할 다음 명령 또는 문을 나타냅니다. 예를 들어이 메서드는 소스 코드 줄을 다시 시도 하거나 다른 함수에서 계속 실행 하도록 강제 하는 데 사용 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
