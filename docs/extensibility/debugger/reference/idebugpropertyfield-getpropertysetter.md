---
title: 아이디버그프로퍼필드::겟프로퍼티세터 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76834b3d4d61f0a58d7a0d2c36f8e30c444ddca2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720856"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
속성을 설정하는 메서드를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPropertySetter( 
   IDebugMethodField** ppField
);
```

```csharp
int GetPropertySetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
【아웃】 속성을 설정하는 메서드를 나타내는 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 속성을 얻는 메서드를 얻으려면 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
