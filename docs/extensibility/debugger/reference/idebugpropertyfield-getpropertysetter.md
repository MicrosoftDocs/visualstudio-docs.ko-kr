---
description: 속성을 설정 하는 메서드를 가져옵니다.
title: 'IDebugPropertyField:: GetPropertySetter | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd787b88ae0e45de7afe944a79fdd0a788aa1449
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167934"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
속성을 설정 하는 메서드를 가져옵니다.

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
제한이 속성을 설정 하는 메서드를 나타내는 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 속성을 가져오는 메서드를 가져오려면 [Getpropertygetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
