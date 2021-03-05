---
description: 배열의 차수 (차원 수)를 가져옵니다.
title: 'IDebugArrayObject:: GetRank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a246cda3f5b9395ae013b4bca9d4d27d6f8a5c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158542"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
배열의 차수 (차원 수)를 가져옵니다.

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
 [Getdimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) 메서드를 사용 하 여 배열 개체의 각 차원 크기를 검색 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
