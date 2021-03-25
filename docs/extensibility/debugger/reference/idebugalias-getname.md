---
description: 이 별칭의 이름을 가져옵니다.
title: 'IDebugAlias:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetName
helpviewer_keywords:
- IDebugAlias::GetName method
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51deb460e5ce30bfea076af9a1f0c1efd2df9673
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059160"
---
# <a name="idebugaliasgetname"></a>IDebugAlias::GetName
이 별칭의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName(
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
제한이 별칭의 이름입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
