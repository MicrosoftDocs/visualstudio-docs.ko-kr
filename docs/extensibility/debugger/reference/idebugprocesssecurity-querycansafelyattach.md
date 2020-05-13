---
title: IDebugProcess 보안::쿼리안전연결 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723204"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
이 방법을 사용하면 포트 공급자가 안전하지 않은 프로세스에 연결하기 전에 경고를 표시할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Return Value
 반환 값은 다음과 같습니다.

- `S_OK`: 처리에 부착해도 안전하며 경고 대화 상자가 표시되지 않습니다.

- `S_FALSE`: 연결은 보안 문제가 될 수 있으며 경고가 있는 대화 상자가 표시됩니다.

- `FAILURE`: 프로세스에 연결하지 못합니다.

## <a name="see-also"></a>참조
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
