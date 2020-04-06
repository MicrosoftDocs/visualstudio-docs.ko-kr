---
title: 이데버그메소드필드::에이넘올로컬 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727337"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
컴파일러에서 내부적으로 생성된 변수를 포함하여 메서드의 모든 로컬 변수에 대해 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
【인】 메서드 내에서 디버그 주소를 나타내는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체는 특정 범위 또는 컨텍스트를 가리킵니다.

`ppLocals`\
【아웃】 지정된 범위의 모든 지역 주민 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 그렇지 않으면 지역 주민을 나타내는 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환하거나 지역 주민이없는 경우 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 지정된 디버그 주소를 포함하는 블록 내에 정의된 변수만 열거됩니다. 이 메서드에는 컴파일러에서 생성된 모든 지역 주민이 포함됩니다. 필요한 모든 것이 원본에 명시적으로 정의된 지역 주민인 경우 EnumLocals 메서드를 [호출합니다.](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)

 메서드에는 여러 범위 지정 컨텍스트 또는 블록이 포함될 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
