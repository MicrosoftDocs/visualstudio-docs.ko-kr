---
description: 프로세스 열거형을 첫 번째 요소로 다시 설정 합니다.
title: 'IEnumDebugProcesses2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Reset
helpviewer_keywords:
- IEnumDebugProcesses2::Reset
ms.assetid: 31cbde4f-0bba-497a-9969-d2c342ef4a7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e812385425fa711b9bb0f2da57ba242c3031386b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224397"
---
# <a name="ienumdebugprocesses2reset"></a>IEnumDebugProcesses2::Next
열거형을 첫 번째 요소로 다시 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드가 호출 된 후 [다음](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md) 메서드에 대 한 다음 호출에서 열거형의 첫 번째 요소를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
