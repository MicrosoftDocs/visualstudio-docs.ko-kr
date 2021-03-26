---
description: 보류 중인 중단점과 연결 된 조건을 설정 하거나 변경 합니다.
title: 'IDebugPendingBreakpoint2:: SetCondition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3cf12bce424e523702da92b86e8894a54ce58b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076604"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
보류 중인 중단점과 연결 된 조건을 설정 하거나 변경 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>매개 변수
`bpCondition`\
진행 설정할 조건을 지정 하는 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이전에 보류 중인 중단점과 연결 된 모든 조건이 손실 됩니다. 이 보류 중인 중단점에서 바인딩된 모든 중단점을 호출 하 여 해당 조건을 매개 변수에 지정 된 값으로 설정 `bpCondition` 합니다.

## <a name="see-also"></a>참조
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
