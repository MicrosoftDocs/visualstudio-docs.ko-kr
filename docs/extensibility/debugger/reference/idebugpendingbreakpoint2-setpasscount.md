---
title: IDebugPending중단점2::세트패스카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 732eadc955b9a6c9bdded3d52f038ff58ed9c217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725683"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
보류 중인 중단점과 연결된 통과 수를 설정하거나 변경합니다.

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
【인】 통과 수를 포함하는 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 중단점이 삭제된 경우 반환합니다. `E_BP_DELETED`

## <a name="remarks"></a>설명
 보류 중인 중단점과 이전에 연관된 모든 패스 수는 손실됩니다. 이 보류 중인 중단점에서 바인딩된 모든 중단점은 `bpPassCount` 매개 변수에 대한 패스 수를 설정하도록 호출됩니다.

## <a name="see-also"></a>참조
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
