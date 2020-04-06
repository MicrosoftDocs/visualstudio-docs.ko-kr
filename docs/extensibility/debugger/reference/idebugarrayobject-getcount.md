---
title: 아이데버그어레이오브젝트::겟카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736204"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
배열의 요소 수를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>매개 변수
`pdwElements`\
【아웃】 개수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 배열 개체가 다차원인 경우에도 배열 개체의 모든 요소를 1차원 배열로 봅니다. 예를 들어 배열이 `myarray[3][2][6]`주어지면 이 메서드는 `pdwElements` 매개 변수에서 36을 반환합니다. [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) 메서드를 사용하여 개별 요소를 한 번에 하나씩 검색합니다.

## <a name="see-also"></a>참조
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
