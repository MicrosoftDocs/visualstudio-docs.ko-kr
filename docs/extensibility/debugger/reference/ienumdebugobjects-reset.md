---
title: 'IEnumDebugObjects:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39f2949a0c3b0c7009b17c8ceee09eee210c61cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957103"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
이 메서드는 열거형을 첫 번째 요소로 다시 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>매개 변수
 None

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드가 호출 된 후 next에 대 한 다음 호출은 열거형의 첫 번째 요소 [를 반환 합니다](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) .

## <a name="see-also"></a>참고 항목
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
