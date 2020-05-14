---
title: IDebugThread2::이력서 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718679"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
스레드 실행을 다시 시작합니다.

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
【아웃】 다시 시작 작업 후 일시 중단 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드에 대한 각 호출은 일시 중단 수가 0에 도달할 때까지 중단 수를 감소시고 실행이 실제로 다시 시작됩니다. 이 일시 중단 수는 **스레드** 디버그 창에 표시됩니다.

 이 메서드에 대 한 각 호출에 대 한 [일시 중단](../../../extensibility/debugger/reference/idebugthread2-suspend.md) 메서드에 대 한 이전 호출 이 있어야 합니다. 일시 중단 수는 `IDebugThread2::Suspend` 메서드가 지금까지 호출된 횟수를 결정합니다.

## <a name="see-also"></a>참조
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [일시 중단](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
