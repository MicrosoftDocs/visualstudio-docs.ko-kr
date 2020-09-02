---
title: 'IDebugClassField:: EnumBaseClasses | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734479"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
이 클래스의 기본 클래스에 대 한 열거자를 만듭니다.

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

제한이 기본 클래스 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 기본 클래스가 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 하 고, 기본 클래스가 없고 매개 변수가 null 값으로 설정 된 경우 S_SH_NO_BASE_CLASSES을 반환 하 고 `ppEnum` , 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 열거자 개체의 기본 클래스는 가장 직접적 이거나 가장 많이 파생 된 기본 클래스를 가장 많은 원격 클래스로 지정 합니다. 예를 들어 다음과 같은 c + + 클래스가 있다고 가정 합니다.

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 열거형은,, 순서로 기본 클래스를 반환 합니다 `Level2` `Level1` `Root` .

## <a name="see-also"></a>추가 정보
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
