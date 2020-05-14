---
title: 아이디버그코어서버3::DiagnoseWebDebuggingError | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732957"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
자동 연결실패 이유를 확인하려고 시도합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>매개 변수
`pszUrl`\
【인】 현재 사용되지 않음; 항상 null 값으로 설정해야 합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 다음은 다른 일반적인 반환 코드입니다.

|코드|설명|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|원격 서버가 디버깅을 시작하지 못한 이유를 확인할 수 없습니다.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|사용 권한이 부족하거나 DEBUG 동사가 활성화되어 있지 않기 때문에 원격 서버에서 디버깅할 수 없습니다.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|웹 서버가 잠겨 디버깅을 활성화하는 데 필요한 DEBUG 동사를 차단하고 있습니다.|

## <a name="see-also"></a>참조
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
