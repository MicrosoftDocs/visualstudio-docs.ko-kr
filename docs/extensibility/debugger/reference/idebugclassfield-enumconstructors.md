---
description: 이 클래스의 생성자에 대 한 열거자를 만듭니다.
title: 'IDebugClassField:: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8efba9ecb25259b6aa4998a1f22fedf443c1281a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084976"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
이 클래스의 생성자에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`cMatch`\
진행 열거할 생성자의 형식을 지정 하는 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) 열거형의 값입니다.

`ppEnum`\
제한이 생성자 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 생성자가 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 하거나 생성자가 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 열거형의 각 요소는 생성자 메서드를 설명 하는 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체입니다.

 일반적으로 생성자 목록에는 컴파일러에서 제공 하는 기본 생성자가 포함 되어 있지 않습니다.

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
