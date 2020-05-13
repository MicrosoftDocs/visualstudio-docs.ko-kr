---
title: IDebugFunctionObject::배열 오브젝트 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728610"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
배열 개체를 만듭니다. 이 배열에는 기본 또는 개체 인스턴스 값이 포함될 수 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`ot`\
【인】 새 배열 개체의 형식을 나타내는 [OBJECT_TYPE 열거형의](../../../extensibility/debugger/reference/object-type.md) 값을 지정합니다.

`pClassField`\
【인】 개체 인스턴스 값의 배열을 만드는 경우 개체의 클래스를 나타내는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 기본 개체의 배열을 만드는 경우 이 매개 변수는 null 값입니다.

`dwRank`\
【인】 배열의 차원 의 순위 또는 수입니다.

`dwDims`\
【인】 배열의 각 차원의 크기입니다.

`dwLowBounds`\
【인】 각 차원의 원수(일반적으로 0 또는 1)입니다.

`ppObject`\
【아웃】 새로 만든 배열을 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체를 반환합니다. 이것은 실제로 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표시되는 함수에 대한 배열 매개 변수를 나타내는 개체를 만들기 위해 이 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
