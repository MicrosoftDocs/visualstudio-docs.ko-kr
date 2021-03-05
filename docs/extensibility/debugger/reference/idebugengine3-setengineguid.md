---
description: 이 메서드는 디버그 엔진의 (DE) GUID를 설정 합니다.
title: 'IDebugEngine3:: SetEngineGuid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b1f614de2349d7bfae8339d516c991b2906ffe4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153718"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
이 메서드는 디버그 엔진의 (DE)를 설정 합니다 `GUID` .

## <a name="syntax"></a>구문

```cpp
HRESULT SetEngineGuid(
   GUID* guidEngine
);
```

```csharp
int SetEngineGuid(
   ref Guid guidEngine
);
```

## <a name="parameters"></a>매개 변수
`guidEngine`\
[in] `GUID` 엔진의입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
