---
title: 아이디버그바운드브레이크포인트2:셋패스카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735438"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
이 바인딩된 중단점과 연관된 패스 수를 설정하거나 변경합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>매개 변수
`bpPassCount`\
【인】 통과 수를 지정하는 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 바인딩된 중단점 개체의 상태가 `E_BP_DELETED` `BPS_DELETED` 설정된 경우(BP_STATE [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 열거형의 일부)가 반환됩니다.

## <a name="remarks"></a>설명
 통과 수는 중단점이 발생하는 시기를 결정합니다. 현재 패스 또는 적중 횟수는 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) 메서드를 호출하여 얻을 수 있습니다.

 이전에 이 중단점과 연관된 패스 수는 손실됩니다.

## <a name="see-also"></a>참조
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
