---
title: 이데버그메소드필드::에이넘로컬 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727209"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
메서드의 선택한 로컬 변수에 대한 열거수를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
【인】 지역 주민을 얻을 컨텍스트 또는 범위를 선택하는 디버그 주소를 나타내는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체입니다.

`ppLocals`\
【아웃】 지역 주민 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 그렇지 않으면 지역 주민이 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 S_OK 반환하거나 지역 주민이없는 경우 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
지정된 디버그 주소를 포함하는 블록 내에 정의된 변수만 열거됩니다. 컴파일러에서 생성된 지역 주민을 포함한 모든 지역 주민이 필요한 경우 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) 메서드를 호출합니다.

메서드에는 여러 범위 지정 컨텍스트 또는 블록이 포함될 수 있습니다. 예를 들어, 다음 고안된 메서드에는 세 개의 범위, 즉 두 개의 내부 블록과 메서드 본문 자체가 포함됩니다.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체는 `func` 메서드 자체를 나타냅니다. 예를 `EnumLocals` 들어 [주소로 IDebugAddress를](../../../extensibility/debugger/reference/idebugaddress.md) 설정한 메서드를 호출하면 변수가 포함된 열거형이 `temp1` 반환됩니다. `Inner Scope 1`

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
