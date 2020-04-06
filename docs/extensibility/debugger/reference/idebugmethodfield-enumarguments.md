---
title: 아이디버그메소드필드::열의 논쟁 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727255"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
메서드를 호출하는 데 필요한 각 인수의 형식에 대한 열거수를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>매개 변수
`ppParams`\
【아웃】 인수 유형 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 인수가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 인수가 없는 경우 S_OK 반환하거나 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 각 요소는 각 매개 변수의 형식을 나타내는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 각 매개 변수의 형식에 대 한 정보를 검색 하려면 GetInfo 메서드를 호출 [합니다.](../../../extensibility/debugger/reference/idebugfield-getinfo.md)

 형식과 함께 매개 변수의 이름이 필요한 경우 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
