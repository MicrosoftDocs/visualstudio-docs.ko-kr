---
description: 이 클래스의 중첩 된 열거자에 대 한 열거자를 만듭니다.
title: 'IDebugClassField:: EnumNestedEnums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2e0d908c88b82e9ed706ab919050e1f4943df0c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088564"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
이 클래스의 중첩 된 열거자에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 중첩 된 열거 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 중첩 된 열거형이 없으면 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 S_OK을 반환 하거나, 중첩 된 열거자가 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
열거형의 각 요소는 중첩 된 열거형을 설명 하는 [Idebugenumfield](../../../extensibility/debugger/reference/idebugenumfield.md) 개체입니다.

클래스 내에서 선언 된 열거형은 중첩 된 열거형으로 간주 됩니다. 예를 들어 다음이 지정될 경우

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums`메서드는 열거형을 나타내는 [Idebugenumfield](../../../extensibility/debugger/reference/idebugenumfield.md) 개체 하나를 포함 하는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다 `NestedEnum` .

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
