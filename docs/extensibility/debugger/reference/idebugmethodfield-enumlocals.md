---
title: 'IDebugMethodField:: EnumLocals | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727209"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
메서드의 선택 된 지역 변수에 대 한 열거자를 만듭니다.

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
진행 로컬을 가져올 컨텍스트 또는 범위를 선택 하는 디버그 주소를 나타내는 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체입니다.

`ppLocals`\
제한이 지역 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 그렇지 않으면 로컬이 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 S_OK 반환 하거나 로컬이 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
지정 된 디버그 주소를 포함 하는 블록 내에 정의 된 변수만 열거 됩니다. 컴파일러에서 생성 된 지역을 포함 하는 모든 지역에 필요한 경우 [Enumalllocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) 메서드를 호출 합니다.

메서드에는 여러 범위 지정 컨텍스트 또는 블록이 포함 될 수 있습니다. 예를 들어, 다음 거리가 메서드는 두 개의 범위, 두 개의 내부 블록과 메서드 본문 자체를 포함 합니다.

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

[Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체는 `func` 메서드 자체를 나타냅니다. `EnumLocals`주소에 설정 된 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 를 사용 하 여 메서드를 호출 하면 `Inner Scope 1` 변수가 포함 된 열거형 `temp1` (예:)이 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
