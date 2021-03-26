---
description: 이 클래스를 포함 하는 클래스를 가져옵니다.
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c59eb2559634c67b210f4fc3b4ce41743346c8ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088486"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
이 클래스를 포함 하는 클래스를 가져옵니다.

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
제한이 바깥쪽 클래스를 나타내는 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체를 반환 합니다. 바깥쪽 클래스가 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
이 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체가 나타내는 클래스가 중첩 된 클래스인 경우 `ppClassField` 매개 변수는 `IDebugClassField` 바깥쪽 클래스를 나타내는 개체를 반환 합니다. 예를 들어, 다음 클래스 정의가 제공 됩니다.

```
class RootClass {
    class NestedClass { }
};
```

`GetEnclosingClass`클래스를 나타내는 개체에서 메서드를 호출 하면 `IDebugClassField` `NestedClass` `IDebugClassField` 클래스를 나타내는 개체가 반환 `RootClass` 됩니다.

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
