---
description: 단순 정수와 같은 기본 데이터 개체를 만듭니다.
title: 'IDebugFunctionObject:: CreatePrimitiveObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eed6bf305667b98e16f4a112b1196456269e5b3c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165543"
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
진행 만들 기본 형식을 나타내는 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 열거형의 값입니다.

`ppObject`\
제한이 새로 만든 개체를 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스로 표현 되는 함수에 대 한 매개 변수인 기본 개체를 나타내는 개체를 만들려면이 메서드를 호출 합니다. 예를 들어 식 문자열이 "myString (5)" 인 경우이 메서드는 정수 5를 나타내는 개체를 만드는 데 사용 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
