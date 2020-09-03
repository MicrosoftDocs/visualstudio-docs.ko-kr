---
title: DEBUG_REASON | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737431"
---
# <a name="debug_reason"></a>DEBUG_REASON
디버깅을 위해 프로세스가 시작 된 이유를 지정 합니다.

## <a name="syntax"></a>Syntax

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
특정 하지 않은 오류가 발생 했습니다 .이는 다른 이유로 적합 하지 않을 때 기본 조건으로 사용 됩니다.

`DEBUG_REASON_USER_LAUNCHED`\
프로세스가 사용자 요청에서 시작 되었습니다.

`DEBUG_REASON_USER_ATTACHED`\
사용자가 이미 실행 중인 프로세스를 연결 했습니다.

`DEBUG_REASON_AUTO_ATTACHED`\
프로세스가 시작 될 때 자동으로 연결 되었습니다.

`DEBUG_REASON_CAUSALITY`\
JIT ( *just-in-time* ) 디버깅 이벤트로 인해 프로세스가 시작 되었습니다.

## <a name="remarks"></a>설명
[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) 메서드에서 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
