---
title: 이데버그어레이필드::겟랭크 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736303"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
배열의 순위 또는 차원 수를 가져옵니다.

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
【아웃】 순위를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 배열의 순위는 차원 수에 해당합니다. C++ 및 C#에서 다차원 배열은 실제로 배열의 배열이므로 1차원 배열로 간주될 수 `GetRank` 있습니다(메서드는 항상 1을 반환합니다). 반면에 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]다차원 배열은 다르게 처리되고 이러한 배열의 순위는 차원 수를 반영합니다(메서드는 `GetRank` 항상 차원 수를 반환합니다).

## <a name="see-also"></a>참조
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
