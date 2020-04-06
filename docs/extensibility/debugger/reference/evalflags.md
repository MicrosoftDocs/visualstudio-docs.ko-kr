---
title: 에발 플래그 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737113"
---
# <a name="evalflags"></a>EVALFLAGS
식 평가를 제어하는 플래그를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>필드
`EVAL_RETURNVALUE`\
반환 값(있는 경우)을 평가할 수 있도록 지정합니다.

`EVAL_NOSIDEEFFECTS`\
부작용이 허용되지 않도록 지정합니다.

`EVAL_ALLOWBPS`\
중단점에 중지를 지정합니다.

`EVAL_ALLOWERRORREPORT`\
허용될 호스트에 대한 오류 보고를 지정합니다. 주로 Internet Explorer의 스크립트에서 식 평가에 사용됩니다.

`EVAL_FUNCTION_AS_ADDRESS`\
함수를 호출하는 대신 주소로 평가할 강제로 함수를 강제합니다.

`EVAL_NOFUNCEVAL`\
함수가 평가되는 것을 방지합니다. 예를 들어 식의 `int` 토큰을 `myExpression(int) + 10`고려합니다. 이 함수는 주소로 올바르게 평가할 수 있지만 값으로 는 평가할 수 없습니다.

`EVAL_NOEVENTS`\
표현식 평가 중에 발생하는 이벤트가 세션 디버그 관리자(SDM) 또는 IDE로 전송되어서는 안 된다는 것을 나타냅니다.

## <a name="remarks"></a>설명
이러한 플래그는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 및 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 메서드에 인수로 전달됩니다.

이러한 플래그는 비트 OR와 결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
