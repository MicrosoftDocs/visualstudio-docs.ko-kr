---
title: 아이디버그메소드필드::에이넘파라미터 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727188"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
메서드의 매개 변수에 대한 열거수를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>매개 변수
`ppParams`\
【아웃】 메서드에 매개 변수 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 그렇지 않으면 매개 변수가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 매개 변수가 없는 경우 S_OK 반환하거나 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 각 요소는 서로 다른 유형의 매개 변수를 나타내는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 각 개체에 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드를 호출하여 개체가 나타내는 매개 변수의 종류를 정확히 확인합니다.

 매개 변수에는 변수 이름과 해당 형식이 모두 포함됩니다. 클래스 메서드에 대 한 첫 번째 매개 변수는 일반적으로 "this" 포인터입니다.

 매개 변수의 형식만 필요한 경우 [EnumArguments 메서드를 호출합니다.](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
