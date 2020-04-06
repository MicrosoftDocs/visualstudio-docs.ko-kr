---
title: 아이데버그어레이오브젝트::겟엘리먼트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736175"
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
【인】 요소 인덱스입니다.

`ppElement`\
【아웃】 요소를 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 배열 개체가 다차원인 경우에도 배열 개체의 모든 요소를 1차원 배열로 봅니다. 예를 들어 배열과 `myarray[3][2][6]` 매개 `dwIndex` 변수가 20인 경우 이 `myarray[1][1][2]`메서드는 `dwIndex` 에서 요소를 반환하고 21의 매개 변수는 에서 `myarray[1][1][3]`요소를 반환합니다. [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 메서드를 사용하여 배열의 총 요소 수를 확인합니다.

## <a name="see-also"></a>참조
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
