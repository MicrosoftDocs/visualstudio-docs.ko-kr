---
title: IDebug바운드 브레이크포인트2:설정조건 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f23fbe1b353378ca521fa802bdeae25fd12476df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735467"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
이 바인딩된 중단점과 연관된 조건을 설정하거나 변경합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>매개 변수
`bpCondition`\
【인】 조건을 설명하는 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 열거형의 값입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 바인딩된 중단점 개체의 상태가 `E_BP_DELETED` `BPS_DELETED` 설정된 경우(BP_STATE [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 열거형의 일부)가 반환됩니다.

## <a name="remarks"></a>설명
 이전에 이 중단점과 연관된 모든 조건이 손실됩니다.

## <a name="see-also"></a>참조
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
