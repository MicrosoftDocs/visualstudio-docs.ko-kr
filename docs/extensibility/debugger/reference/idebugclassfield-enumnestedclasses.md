---
title: 아이디버그클래스필드::에이넘네스트클래스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734437"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
이 클래스에 중첩된 클래스에 대한 열거형기를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
【아웃】 중첩된 클래스 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 중첩된 클래스가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 중첩 된 클래스가없는 경우 S_OK 반환하거나 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
열거형의 각 요소는 중첩된 클래스를 설명하는 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 개체입니다.

중첩된 클래스는 다른 클래스 내에 정의된 클래스입니다. 다음은 그 예입니다.

```
class RootClass {
   class NestedClass { }
};
```

[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 열거형에는 클래스를 나타내는 `NestedClass` 하나의 개체가 포함됩니다.

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
