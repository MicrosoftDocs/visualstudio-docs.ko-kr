---
description: 속성을 가져오는 메서드를 가져옵니다.
title: 'IDebugPropertyField:: GetPropertyGetter | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b86315d7991e8ca76a4d08ec38292a9157bbdb1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167986"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
속성을 가져오는 메서드를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPropertyGetter( 
   IDebugMethodField** ppField
);
```

```cpp
int GetPropertyGetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
제한이 속성을 가져오는 메서드를 나타내는 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 속성을 설정 하는 메서드를 가져오기 위해 [Getpropertysetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) 는 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
