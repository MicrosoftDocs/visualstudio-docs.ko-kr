---
title: 아이데버그어레이오브젝트::겟차원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 527f79724aeac0de58d0ae63c9c2408ed2eca9ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736165"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
배열의 차원을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>매개 변수
`dwCount`\
【인】 검색할 차원의 수입니다.

`dwDimensions`\
【인, 아웃】 각 차원의 크기로 채워진 배열입니다. `dwCount`배열의 최대 크기를 지정합니다. `dwDimensions`

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 다차원 배열은 각 차원에 대해 서로 다른 크기를 가질 수 있습니다. 예를 들어 3차원 배열이 `myarray[3][2][6]`주어지면 이 메서드는 해당 순서로 `dwDimensions` 매개 변수에서 3, 2 및 6을 반환합니다.

## <a name="see-also"></a>참조
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
