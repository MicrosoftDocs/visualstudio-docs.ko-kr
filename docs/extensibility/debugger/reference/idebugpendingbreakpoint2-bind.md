---
title: IDebugPending중단점2::바인드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 83d48e8df847620716b0f581be65ded48e2e5a13
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725980"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
이 보류 중인 중단점을 하나 이상의 코드 위치에 바인딩합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Bind( 
   void 
);
```

```csharp
int Bind();
```

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 중단점이 삭제된 경우 반환합니다. `E_BP_DELETED`

## <a name="remarks"></a>설명
 이 메서드를 호출 하는 경우 디버그 엔진 (DE) 일치 하는 모든 코드 위치에이 보류 중인 중단점을 바인딩 하려고 해야 합니다.

 이 메서드가 반환된 후 호출자는 [EnumBoundBreakpoint](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) 또는 [EnumErrorBreakpoints에](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)대한 호출이 모든 바인딩또는 오류 중단점을 각각 열거한다고 가정하기 전에 보류 중인 중단점이 바인딩되었음또는 오류가 있음을 나타내는 이벤트를 기다려야 합니다.

## <a name="see-also"></a>참조
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
