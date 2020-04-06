---
title: IDebugThread2::일시 중단 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718635"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
스레드를 일시 중단합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>매개 변수
`pdwSuspendCount`\
【아웃】 일시 중단 작업 후 일시 중단 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드에 대한 각 호출은 일시 중단 수를 0보다 증가시입니다. 이 일시 중단 수는 **스레드** 디버그 창에 표시됩니다.

 이 메서드에 대 한 각 호출에 대 한 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드에 대 한 나중에 호출 해야 합니다.

## <a name="see-also"></a>참조
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [다시 시작](../../../extensibility/debugger/reference/idebugthread2-resume.md)
