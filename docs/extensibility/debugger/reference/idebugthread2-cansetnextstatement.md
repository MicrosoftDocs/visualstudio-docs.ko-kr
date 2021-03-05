---
description: 현재 명령 포인터를 지정 된 스택 프레임으로 설정할 수 있는지 여부를 확인 합니다.
title: 'IDebugThread2:: CanSetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b07eb23127abedc4e41af2795c3452401c3e670
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168389"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
현재 명령 포인터를 지정 된 스택 프레임으로 설정할 수 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>매개 변수
`pStackFrame`\
나중에 사용 하도록 예약 되어 있습니다. 을 null 값으로 설정 합니다. 이 값이 null 이면 현재 스택 프레임을 사용 합니다.

`pCodeContext`\
진행 실행할 코드 위치와 해당 컨텍스트를 설명 하는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드가를 반환 하는 경우 `S_OK` [setnextstatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) 메서드를 호출 하 여 실제로 다음 문을 설정 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
