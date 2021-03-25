---
description: 다음에 스레드 중 하나가 실행을 시도할 때이 디버그 엔진 (DE)에서 디버그 하는 모든 프로그램의 실행을 중지 하도록 요청 합니다.
title: 'IDebugEngine2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a320cbe9f2414de754b5844aa645bffb857568
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093901"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
다음에 스레드 중 하나가 실행을 시도할 때이 디버그 엔진 (DE)에서 디버그 하는 모든 프로그램의 실행을 중지 하도록 요청 합니다.

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
 이 메서드는 비동기입니다. [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 이벤트는 다음에이 메서드를 호출한 후 프로그램이 실행을 시도할 때 전송 됩니다.

## <a name="see-also"></a>참조
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
