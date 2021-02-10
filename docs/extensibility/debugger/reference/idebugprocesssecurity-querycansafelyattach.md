---
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3f2c02610b5fbe99335ccea6d7c566a0fe58df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931463"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
이 방법을 사용 하면 사용자가 안전 하지 않은 프로세스에 연결 하기 전에 포트 공급자가 경고를 표시할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Return Value
 반환 값은 다음과 같습니다.

- `S_OK`: 프로세스에 연결 하는 것은 안전 하며 경고 대화 상자가 표시 되지 않습니다.

- `S_FALSE`: 연결 하면 보안 문제가 발생할 수 있으며 경고가 표시 된 대화 상자가 표시 됩니다.

- `FAILURE`: 프로세스에 연결 하지 못했습니다.

## <a name="see-also"></a>참고 항목
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
