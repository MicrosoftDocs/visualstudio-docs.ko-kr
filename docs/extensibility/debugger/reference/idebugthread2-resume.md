---
description: 스레드의 실행을 다시 시작 합니다.
title: 'IDebugThread2:: Resume | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93552bac60d16a21212bfa89816481cf7099d399
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053024"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
스레드의 실행을 다시 시작 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>매개 변수
`pdwSuspendCount`\
제한이 다시 시작 작업 후 일시 중단 횟수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드에 대 한 각 호출은 0에 도달할 때까지 일시 중단 횟수를 감소 시킵니다. 이때 실행은 실제로 다시 시작 됩니다. 이 일시 중단 횟수는 **스레드** 디버그 창에 표시 됩니다.

 이 메서드에 대 한 각 호출에는 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) 메서드를 이전에 호출 해야 합니다. 일시 중단 횟수는 `IDebugThread2::Suspend` 지금까지 메서드가 호출 된 횟수를 결정 합니다.

## <a name="see-also"></a>참조
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [일시 중지됨](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
