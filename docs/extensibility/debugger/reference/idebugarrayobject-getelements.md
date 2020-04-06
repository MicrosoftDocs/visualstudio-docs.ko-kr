---
title: 아이데버그어레이오브젝트::겟엘리먼츠 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be06acbef93d8858557fea5bd7563168be2d28aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736244"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
배열의 모든 요소의 열거수를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
【아웃】 모든 요소를 열거할 수 있는 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 또는 [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 및 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) 메서드를 사용하여 요소를 반복합니다.

## <a name="see-also"></a>참조
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
