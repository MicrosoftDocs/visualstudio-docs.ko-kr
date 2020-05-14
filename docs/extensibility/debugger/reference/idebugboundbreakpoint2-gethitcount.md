---
title: 아이디버그바운드브레이크포인트2:겟히트카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c821470cc81c1f4c495f6d71565d79cc9745f65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735511"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
이 바인딩된 중단점에 대한 현재 적중 횟수를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetHitCount( 
   DWORD* pdwHitCount
);
```

```csharp
int GetHitCount( 
   out uint pdwHitCount
);
```

## <a name="parameters"></a>매개 변수
`pdwHitCount`\
【아웃】 적중 횟수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 바인딩된 중단점 개체의 상태가 `E_BP_DELETED` `BPS_DELETED` 설정된 경우(BP_STATE [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 열거형의 일부)가 반환됩니다.

## <a name="remarks"></a>설명
 적중 횟수는 이 중단점이 세션의 현재 실행 중에 발생한 횟수입니다.

## <a name="see-also"></a>참조
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
