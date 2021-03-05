---
description: 메서드의 정적 지역 변수에 대 한 열거자를 만듭니다.
title: 'IDebugMethodField:: EnumStaticLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c31d8644bf918b57c1d97b2ee2ddbc840a33ff1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164983"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
메서드의 정적 지역 변수에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>매개 변수
`ppLocals`\
제한이 정적 지역 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 정적 로컬이 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK 반환 하거나 정적 로컬이 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 각 요소는 서로 다른 형식의 정적 지역을 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 각 개체에 대해 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드를 호출 하 여 개체가 나타내는 정적 로컬의 종류를 정확 하 게 확인 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
