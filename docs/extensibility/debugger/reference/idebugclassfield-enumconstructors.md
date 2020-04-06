---
title: 아이디버그클래스필드::에이넘컨스컨스컨스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734462"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
이 클래스에 대 한 생성자에 대 한 열거를 만듭니다.

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
【인】 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) 열거할 생성자 유형을 지정하는 값입니다.

`ppEnum`\
【아웃】 생성자 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 생성자가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 생성자가 없는 경우 S_OK 반환하거나 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 열거형의 각 요소는 생성자 메서드를 설명하는 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체입니다.

 생성자 목록에는 일반적으로 컴파일러에서 제공하는 기본 생성자가 포함되지 않습니다.

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
