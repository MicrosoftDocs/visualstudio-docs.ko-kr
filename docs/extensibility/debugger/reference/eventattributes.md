---
title: EVENTATTRIBUTES | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737066"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
이벤트 특성을 지정 합니다.

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
이벤트가 비동기 이며 이벤트에 대 한 회신이 필요 하지 않음을 나타냅니다.

`EVENT_SYNCHRONOUS`\
이벤트가 동기식 임을 나타냅니다. [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)을 통해 회신 합니다.

`EVENT_STOPPING`\
중지 이벤트 임을 나타냅니다. 는 또는와 함께 사용 해야 합니다 `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
비동기 중지 이벤트를 나타냅니다. 현재 이러한 이벤트가 없습니다. 이 플래그는 자리 표시자입니다.

`EVENT_SYNC_STOP`\
동기 중지 이벤트 (및의 조합)를 `EVENT_SYNCHRONOUS` 나타냅니다 `EVENT_STOPPING` . 이 값은 중지 이벤트를 보낼 때 디버그 엔진 (DE)에서 사용 됩니다. 회신은 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)또는 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)호출을 통해 수행 됩니다.

`EVENT_IMMEDIATE`\
IDE에 즉시 보내고 받는 이벤트를 나타냅니다. 이 플래그는 `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` `EVENT_SYNC_STOP` 이벤트 유형 및 회신 메커니즘 (있는 경우)이 알려진 팩트를 나타내는, 또는와 같은 다른 플래그와 결합 됩니다.

`EVENT_EXPRESSION_EVALUATION`\
이 이벤트는 식 계산의 결과입니다.

## <a name="remarks"></a>설명
이러한 값은 `dwAttrib` [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드의 매개 변수에 전달 됩니다.

이러한 값은 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
