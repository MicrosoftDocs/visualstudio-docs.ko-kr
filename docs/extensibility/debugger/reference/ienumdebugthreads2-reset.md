---
description: Threads 열거형을 첫 번째 요소로 다시 설정 합니다.
title: 'IEnumDebugThreads2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1521e69b5896422a811714be9e4aefa649824ab4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225788"
---
# <a name="ienumdebugthreads2reset"></a>IEnumDebugThreads2::Reset
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
 이 메서드가 호출 된 후 [다음](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) 메서드에 대 한 다음 호출에서 열거형의 첫 번째 요소를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
