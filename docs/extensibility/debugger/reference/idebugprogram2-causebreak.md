---
title: 아이디버그프로그램2:원인중단 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e96db32d7ba5a01f89530623c949500a265cdb60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723103"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
다음에 스레드 중 하나가 실행하려고 할 때 프로그램이 실행을 중지하도록 요청합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 이벤트는 다음 프로그램이 이 메서드를 호출한 후 코드를 실행하려고 시도할 때 전송됩니다.

 이 메서드는 프로그램이 중지될 때까지 기다리지 않고 메서드가 즉시 반환된다는 점에서 비동기적입니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
