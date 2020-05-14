---
title: 아이데버그어레이오브젝트::겟랭크 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c645683cf1f842afdecba3c3dee8942a3fd6971a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736196"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
배열의 순위, 즉 차원 수를 가져옵니다.

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
 [GetDimensions 메서드를](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) 사용하여 배열 개체의 각 차원 크기를 검색합니다.

## <a name="see-also"></a>참조
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
