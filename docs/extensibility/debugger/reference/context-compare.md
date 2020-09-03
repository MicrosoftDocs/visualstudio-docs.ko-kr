---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737611"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
두 메모리 컨텍스트를 비교 하는 조건을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>필드
`CONTEXT_EQUAL`\
목록에서 대상 메모리 컨텍스트와 동일한 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_LESS_THAN`\
목록에서 대상 메모리 컨텍스트 보다 작은 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_GREATER_THAN`\
목록에서 대상 메모리 컨텍스트 보다 큰 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_LESS_THAN_OR_EQUAL`\
목록에서 대상 메모리 컨텍스트 보다 작거나 같은 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
목록에서 대상 메모리 컨텍스트 보다 크거나 같은 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_SAME_SCOPE`\
목록에서 대상 메모리 컨텍스트와 동일한 범위에 있는 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_SAME_FUNCTION`\
목록에서 대상 메모리 범위와 동일한 함수에 있는 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_SAME_MODULE`\
목록에서 대상 메모리 컨텍스트와 동일한 모듈에 있는 첫 번째 메모리 컨텍스트를 찾습니다.

`CONTEXT_SAME_PROCESS`\
목록에서 대상 메모리 컨텍스트와 동일한 프로세스에 있는 첫 번째 메모리 컨텍스트를 찾습니다.

## <a name="remarks"></a>설명
[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) 메서드에 인수로 전달 됩니다.

이러한 값은 목록에서 지정 된 비교 조건을 충족 하는 첫 번째 메모리 컨텍스트를 찾는 데 사용 됩니다. 메모리 컨텍스트에는 메서드를 통해 자신을 비교할 메모리 컨텍스트 목록이 제공 됩니다 `IDebugMemoryContext2::Compare` . 비교 연산자가 반환 되는 목록에서 첫 번째 메모리 컨텍스트입니다 `true` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [비교](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
