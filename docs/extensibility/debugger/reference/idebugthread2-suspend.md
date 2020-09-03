---
title: 'IDebugThread2:: Suspend | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718635"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
스레드를 일시 중단 합니다.

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
제한이 일시 중단 작업 후 일시 중단 횟수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드에 대 한 각 호출은 일시 중단 횟수가 0 보다 증가 합니다. 이 일시 중단 횟수는 **스레드** 디버그 창에 표시 됩니다.

 이 메서드에 대 한 각 호출에 대해 나중에 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 메서드를 호출 해야 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [재개](../../../extensibility/debugger/reference/idebugthread2-resume.md)
