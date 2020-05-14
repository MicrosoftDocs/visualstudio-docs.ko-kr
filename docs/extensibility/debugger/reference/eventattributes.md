---
title: 이벤트 속성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737066"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
이벤트 특성을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>필드
`EVENT_ASYNCHRONOUS`\
이벤트가 비동기이며 이벤트에 대한 응답이 필요하지 없음을 나타냅니다.

`EVENT_SYNCHRONOUS`\
이벤트가 동기임을 나타냅니다. [계속에서](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)시작 동기 를 통해 회신이벤트 .

`EVENT_STOPPING`\
이 이벤트가 중지 이벤트임을 나타냅니다. 또는 와 `EVENT_ASYNCHRONOUS` 결합해야 `EVENT_SYNCHRONOUS`합니다.

`EVENT_ASYNC_STOP`\
비동기 중지 이벤트를 나타냅니다. 현재 이러한 이벤트는 없습니다. 이 플래그는 자리 표시자일 뿐입니다.

`EVENT_SYNC_STOP`\
동기 중지 이벤트(및 `EVENT_SYNCHRONOUS` `EVENT_STOPPING`의 조합)를 나타냅니다. 이 값은 중지 이벤트를 보낼 때 DE(디버그 엔진)에서 사용됩니다. 응답은 [실행,](../../../extensibility/debugger/reference/idebugprogram2-execute.md) [단계](../../../extensibility/debugger/reference/idebugprogram2-step.md)또는 [계속에](../../../extensibility/debugger/reference/idebugprogram2-continue.md)대한 호출을 통해 이루어집니다.

`EVENT_IMMEDIATE`\
IDE에 즉시 동기적으로 전송되는 이벤트를 나타냅니다. 이 플래그는 의 `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`와 같은 `EVENT_SYNC_STOP` 다른 플래그와 결합하거나 이벤트 유형및 회신 메커니즘(있는 경우)이 알려져 있다는 사실을 나타냅니다.

`EVENT_EXPRESSION_EVALUATION`\
이벤트는 식 평가의 결과입니다.

## <a name="remarks"></a>설명
이러한 값은 `dwAttrib` [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드의 매개 변수에 전달됩니다.

이러한 값은 약간 과 `OR`결합될 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
