---
description: 보류 중인 중단점과 연결 된 패스 수를 설정 하거나 변경 합니다.
title: 'IDebugPendingBreakpoint2:: SetPassCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d83249667bd9489b052f35a4d3d3b7ca826d540f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058354"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
보류 중인 중단점과 연결 된 패스 수를 설정 하거나 변경 합니다.

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
진행 패스 수를 포함 하는 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 중단점이 삭제 되었으면를 반환 `E_BP_DELETED` 합니다.

## <a name="remarks"></a>설명
 보류 중인 중단점과 이전에 연결 된 패스 수가 모두 손실 됩니다. 이 보류 중인 중단점에서 바인딩된 모든 중단점을 호출 하 여 해당 pass count를 `bpPassCount` 매개 변수로 설정 합니다.

## <a name="see-also"></a>참조
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
