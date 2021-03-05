---
description: 이 프로세스에서 코드를 실행 하는 다음 프로그램이 중단 하 고 IDebugBreakEvent2 이벤트 개체를 전송 하도록 요청 합니다.
title: 'IDebugProcess2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28a4da4c0f7e4f8770478a47a73f7567506d5ae2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161400"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
이 프로세스에서 코드를 실행 하는 다음 프로그램이 중단 하 고 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 이벤트 개체를 전송 하도록 요청 합니다.

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

## <a name="see-also"></a>참고 항목
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
