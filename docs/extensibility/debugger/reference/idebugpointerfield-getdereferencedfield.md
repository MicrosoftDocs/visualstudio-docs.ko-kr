---
title: 이데버그 포인터필드::GetDereferenced필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 617711a611e6eb1ea162c3abd8ad2b793b4756cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725617"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
이 메서드는 이 포인터 개체가 가리키는 개체 유형을 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
【아웃】 대상 개체의 형식을 설명하는 [IDebugField를](../../../extensibility/debugger/reference/idebugfield.md) 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 예를 들어 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) 개체가 정수를 가리키는 경우 이 메서드에서 반환되는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 형식은 해당 정수 형식을 설명합니다.

## <a name="see-also"></a>참조
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
