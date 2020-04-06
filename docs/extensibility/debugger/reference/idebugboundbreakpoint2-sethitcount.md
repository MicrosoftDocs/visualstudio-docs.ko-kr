---
title: 아이디버그바운드브레이크포인트2::셋히트카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e82f12b12c9afbc24f9416ec2639a4b9768d8fd0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735407"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
바인딩된 중단점에 대한 적중 수를 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>매개 변수
`dwHitCount`\
【인】 설정할 적중 횟수입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 바인딩된 중단점 개체의 상태가 `E_BP_DELETED` `BPS_DELETED` 설정된 경우(BP_STATE [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 열거형의 일부)가 반환됩니다.

## <a name="remarks"></a>설명
 적중 횟수는 이 중단점이 세션의 현재 실행 중에 발생한 횟수입니다.

 이 메서드는 일반적으로 디버그 엔진에서 이 중단점에 대한 현재 적중 횟수를 업데이트하기 위해 호출됩니다.

## <a name="see-also"></a>참조
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
