---
description: 자동 연결이 실패 한 이유를 확인 하려고 합니다.
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a7e41842842850f7eb9ff4993bba348aea9816f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077709"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
자동 연결이 실패 한 이유를 확인 하려고 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>매개 변수
`pszUrl`\
진행 현재 사용 되지 않습니다. 항상 null 값으로 설정 해야 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음은 일반적인 반환 코드입니다.

|코드|Description|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|원격 서버에서 디버깅을 시작 하지 못한 이유를 확인할 수 없습니다.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|사용 권한이 부족 하거나 디버그 동사를 사용할 수 없기 때문일 수 있습니다. 원격 서버에서 디버그할 수 없습니다.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|웹 서버가 잠겨 있어 디버깅을 사용 하도록 설정 하는 데 필요한 디버그 동사를 차단 합니다.|

## <a name="see-also"></a>참조
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
