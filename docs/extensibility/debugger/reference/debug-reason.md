---
title: DEBUG_REASON | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737431"
---
# <a name="debug_reason"></a>DEBUG_REASON
디버깅을 위해 프로세스가 시작된 이유를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>필드
`DEBUG_REASON_ERROR`\
비특정 오류가 발생했습니다(다른 이유가 맞지 않을 때 기본 조건으로 사용됨).

`DEBUG_REASON_USER_LAUNCHED`\
이 프로세스는 사용자의 요청에 따라 시작되었습니다.

`DEBUG_REASON_USER_ATTACHED`\
이미 실행 중인 프로세스가 사용자가 연결했습니다.

`DEBUG_REASON_AUTO_ATTACHED`\
프로세스가 시작될 때 프로세스가 자동으로 연결되었습니다.

`DEBUG_REASON_CAUSALITY`\
*JIT(Just-In-Time)* 디버깅 이벤트로 인해 프로세스가 시작되었습니다.

## <a name="remarks"></a>설명
[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) 메서드에서 반환되었습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
