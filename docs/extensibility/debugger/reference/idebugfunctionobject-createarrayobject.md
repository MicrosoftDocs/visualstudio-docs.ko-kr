---
description: 배열 개체를 만듭니다.
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94216521f0a57a76f83c68f168ed1afcac199a0e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073549"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
배열 개체를 만듭니다. 이 배열에는 기본 또는 개체 인스턴스 값이 포함 될 수 있습니다.

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
진행 새 배열 개체의 형식을 나타내는 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 열거형의 값을 지정 합니다.

`pClassField`\
진행 개체 인스턴스 값의 배열을 만드는 경우 개체의 클래스를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 기본 개체의 배열을 만드는 경우이 매개 변수는 null 값입니다.

`dwRank`\
진행 배열의 차원 수 또는 차수입니다.

`dwDims`\
진행 배열의 각 차원 크기입니다.

`dwLowBounds`\
진행 각 차원의 원본 (일반적으로 0 또는 1)입니다.

`ppObject`\
제한이 새로 만든 배열을 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체를 반환 합니다. 실제로 [Idebugarrayobject](../../../extensibility/debugger/reference/idebugarrayobject.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현 되는 함수에 대 한 배열 매개 변수를 나타내는 개체를 만들려면이 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
