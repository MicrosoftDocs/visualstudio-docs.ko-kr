---
title: 이데버그메소드필드::에이넘정적 지역 주민들 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e0a89b4c1ac4318b6dd070dc086b86b45ad24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727161"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
메서드의 정적 로컬 변수에 대한 열거수를 만듭니다.

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
【아웃】 정적 지역 인의 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 정적 지역 주민이 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 정적 지역 주민이 없는 경우 S_OK 반환하거나 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 각 요소는 서로 다른 유형의 정적 지역 요소를 나타내는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 각 개체에 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드를 호출하여 개체가 나타내는 정적 로컬의 종류를 정확히 확인합니다.

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
