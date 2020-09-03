---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 298312ae285eed1de29a3092db900f06e8f7d19a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724165"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
이 프로세스에서 코드를 실행 하는 다음 프로그램이 중단 하 고 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 이벤트 개체를 전송 하도록 요청 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CauseBreak( 
   void
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
