---
description: 배열의 요소를 가져옵니다.
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43659e8dfbd86f800105cbfa35fa3b3a13c099cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094382"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
배열의 요소를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>매개 변수
`dwIndex`\
진행 요소 인덱스입니다.

`ppElement`\
제한이 요소를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 배열 개체가 다차원 인 경우에도 배열 개체의 모든 요소를 1 차원 배열로 표시 합니다. 예를 들어, 배열 `myarray[3][2][6]` 및 `dwIndex` 매개 변수가 20 인 경우이 메서드는에서 요소를 반환 `myarray[1][1][2]` 하 고 `dwIndex` 21의 매개 변수는에서 요소를 반환 `myarray[1][1][3]` 합니다. [Getcount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 메서드를 사용 하 여 배열에 있는 요소의 총 수를 확인 합니다.

## <a name="see-also"></a>참조
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
