---
title: 아이디버그클래스필드::게엔클로징클래스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734399"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
이 클래스를 둘러싸는 클래스를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>매개 변수
`ppClassField`\
【아웃】 둘러싸는 클래스를 나타내는 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 개체를 반환합니다. 둘러싸는 클래스가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
이 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 개체로 표시되는 클래스가 중첩 된 `ppClassField` 클래스인 `IDebugClassField` 경우 매개 변수는 둘러싸는 클래스를 나타내는 개체를 반환합니다. 예를 들어, 이 클래스 정의가 주어지면 다음과 같은

```
class RootClass {
    class NestedClass { }
};
```

클래스를 `GetEnclosingClass` 나타내는 `IDebugClassField` 개체에서 `NestedClass` 메서드를 `IDebugClassField` 호출하는 것은 `RootClass`클래스를 나타내는 개체를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
