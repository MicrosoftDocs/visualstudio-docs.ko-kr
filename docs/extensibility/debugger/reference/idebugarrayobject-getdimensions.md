---
description: 배열의 크기를 가져옵니다.
title: 'IDebugArrayObject:: GetDimensions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5bb935ea4aba6ab6ebd0a39f8dfc8d539d6555c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158685"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
배열의 크기를 가져옵니다.

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
진행 검색할 차원의 수입니다.

`dwDimensions`\
[in, out] 각 차원의 크기로 채워진 배열입니다. `dwCount` 배열의 최대 크기를 지정 합니다 `dwDimensions` .

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 다차원 배열에는 각 차원에 대해 서로 다른 크기를 사용할 수 있습니다. 예를 들어 3 차원 배열이 지정 된 경우 `myarray[3][2][6]` 이 메서드는 매개 변수에서 3, 2, 6을 순서 대로 반환 `dwDimensions` 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
