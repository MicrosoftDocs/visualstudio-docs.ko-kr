---
description: 프로그램에서 다음에 스레드 중 하나를 실행 하려고 할 때 프로그램 실행을 중지 하도록 요청 합니다.
title: 'IDebugProgram2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef10a714b6e65b40edb83cb0547ae1a28720d328
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166036"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
프로그램에서 다음에 스레드 중 하나를 실행 하려고 할 때 프로그램 실행을 중지 하도록 요청 합니다.

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
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 이벤트는 프로그램에서 다음에이 메서드를 호출한 후 코드를 실행 하려고 할 때 전송 됩니다.

 이 메서드는 프로그램이 중지 될 때까지 기다릴 필요 없이 즉시 반환 되는 비동기입니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
