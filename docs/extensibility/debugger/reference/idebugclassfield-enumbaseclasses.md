---
title: 아이디버그클래스필드::에넘베이스클래스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734479"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
이 클래스의 기본 클래스에 대한 열거수를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\

【아웃】 기본 클래스 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 기본 클래스가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환하고 기본 클래스가 없는 경우 `ppEnum` S_SH_NO_BASE_CLASSES 반환합니다(매개 변수가 null 값으로 설정됨). 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 열거체 개체의 기본 클래스는 가장 원격 기본 클래스에 가장 즉각적인(또는 가장 파생된) 기본 클래스의 순서로 지정됩니다. 예를 들어 C++ 클래스가 제공됩니다.

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 열거형은 기본 클래스를 순서대로 `Level2` `Level1` `Root`반환합니다.

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
