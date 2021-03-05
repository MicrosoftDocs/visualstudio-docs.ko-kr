---
description: 세션 디버그 관리자 (SDM)가 프로세스를 분리할 수 있는지 여부를 확인 합니다.
title: 'IDebugProcess2:: CanDetach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e876d5642cf8a4b7b60f5119839e64959f296e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151677"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
세션 디버그 관리자 (SDM)가 프로세스를 분리할 수 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Return Value
 성공 하면 `S_OK.` `S_FALSE` 디버거가 프로세스에서 분리 될 수 없는 경우이 반환 됩니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참고 항목
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
