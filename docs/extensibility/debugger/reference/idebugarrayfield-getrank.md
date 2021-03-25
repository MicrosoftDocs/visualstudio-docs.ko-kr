---
description: 배열의 차원 수 또는 차수를 가져옵니다.
title: 'IDebugArrayField:: GetRank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ac945e23090b649ffb5ad2f452ec9245aac81ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058978"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
배열의 차원 수 또는 차수를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>매개 변수
`pdwRank`\
제한이 순위를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 배열의 순위는 차원 수에 해당 합니다. C + + 및 c #에서 다차원 배열은 배열의 배열 이므로 1 차원 배열로만 간주 될 수 있으며 `GetRank` 메서드는 항상 1을 반환 합니다. 반면에서 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 다차원 배열은 다르게 처리 되며 이러한 배열의 순위는 차원의 수를 반영 하 고 `GetRank` 메서드는 항상 차원의 수를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
