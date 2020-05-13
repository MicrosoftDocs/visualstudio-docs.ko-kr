---
title: IDebugExceptionEvent2::PassToDebuggee | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729839"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
실행을 다시 시작할 때 디버깅 되는 프로그램에 예외를 전달 해야 하는지 또는 예외를 삭제 해야 하는지 여부를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>매개 변수
`fPass`\
【인】 Nonzero`TRUE`() 예외가 실행이 다시 시작될 때 디버깅되는 프로그램에 전달되어야 하는 경우 또는 예외를 삭제해야 하는 경우 0()`FALSE`입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드를 호출해도 실제로 디버깅 중인 프로그램에서 코드가 실행되지는 않습니다. 호출은 다음 코드 실행에 대 한 상태를 설정 하는 것입니다. 예를 들어 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 메서드에 대한 `S_OK` 호출은 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)함께 반환될 수 있습니다.`dwState` 필드로 `EXCEPTION_STOP_SECOND_CHANCE`설정됩니다.

 IDE는 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 이벤트를 수신하고 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) 메서드를 호출할 수 있습니다. 디버그 엔진(DE)에는 메서드가 호출되지 않은 경우 `PassToDebuggee` 사례를 처리하는 기본 동작이 있어야 합니다.

## <a name="see-also"></a>참조
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
