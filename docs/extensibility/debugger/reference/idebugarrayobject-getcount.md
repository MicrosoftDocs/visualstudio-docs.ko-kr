---
title: 'IDebugArrayObject:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9750b2982ad0b2d70375fe0519a9fd888bcac8a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870222"
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
제한이 개수를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 배열 개체가 다차원 인 경우에도 배열 개체의 모든 요소를 1 차원 배열로 표시 합니다. 예를 들어 배열이 지정 된 경우 `myarray[3][2][6]` 이 메서드는 매개 변수에 36을 반환 `pdwElements` 합니다. [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) 메서드를 사용 하 여 개별 요소를 한 번에 하나씩 검색 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
