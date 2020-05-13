---
title: IDebugFunctionObject::원시적 개체 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728538"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
단순 정수와 같은 기본 데이터 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`ot`\
【인】 만들 [기본](../../../extensibility/debugger/reference/object-type.md) 형식의 OBJECT_TYPE 열거형의 값입니다.

`ppObject`\
【아웃】 새로 만든 개체를 나타내는 [IDebugObject를](../../../extensibility/debugger/reference/idebugobject.md) 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표시되는 함수의 매개 변수인 기본 개체를 나타내는 개체를 만들기 위해 이 메서드를 호출합니다. 예를 들어 식 문자열이 "myString(5)"인 경우 이 메서드는 정수 5를 나타내는 개체를 만드는 데 사용됩니다.

## <a name="see-also"></a>참조
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
