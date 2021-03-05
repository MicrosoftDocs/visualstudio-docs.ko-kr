---
description: 이 메서드는 디버깅을 위해 프로세스가 시작 된 이유를 반환 합니다.
title: 'IDebugProcess3:: GetDebugReason | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ab36134f8085ba13279332e3c1b8dc2fe65c200
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158477"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
이 메서드는 디버깅을 위해 프로세스가 시작 된 이유를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDebugReason(
   DEBUG_REASON* pReason
);
```

```csharp
int GetDebugReason(
   out enum_DEBUG_REASON pReason
);
```

## <a name="parameters"></a>매개 변수
`pReason`\
제한이 [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) 열거형의 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)
