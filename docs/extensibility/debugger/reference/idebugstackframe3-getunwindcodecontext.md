---
description: 스택 해제 작업이 발생 한 경우 위치를 나타내는 코드 컨텍스트를 반환 합니다.
title: 'IDebugStackFrame3:: GetUnwindCodeContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ef0a66729a2e9061a9e71ec0634a65999b55bf2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159733"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
스택 해제 작업이 발생 한 경우 위치를 나타내는 코드 컨텍스트를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetUnwindCodeContext(
   IDebugCodeContext2 **ppCodeContext
);
```

```csharp
int GetUnwindCodeContext(
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>매개 변수
`ppCodeContext`\
제한이 스택 해제가 발생 한 경우 코드 컨텍스트 위치를 나타내는 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 스택 해제 후의 위치에 대 한 코드 컨텍스트를 반환할 수 있지만 실제로 현재 스택 프레임에서 스택 해제가 발생할 수 있음을 반드시 의미 하는 것은 아닙니다.

## <a name="see-also"></a>참고 항목
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
