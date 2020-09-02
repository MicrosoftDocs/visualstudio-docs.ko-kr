---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714480"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

이 구조체는 범위 내에 있는 지역 변수의 주소 (일반적으로 함수 또는 메서드)를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>멤버

`tokMethod`\
지역 변수가 포함 된 메서드 또는 함수의 ID입니다.

[C + +] `_mdToken` 는 `typedef` 32 비트에 대 한입니다 `int` .

`pLocal`\
이 구조체의 주소가 나타내는 토큰입니다.

`dwIndex`\
메서드나 함수에서이 지역 변수의 인덱스 이거나 다른 값 (언어 관련)이 될 수 있습니다.

## <a name="remarks"></a>설명

이 구조체는 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` 구조체의 필드가 `DEBUG_ADDRESS_UNION` `ADDRESS_KIND_LOCAL` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형의 값)로 설정 된 경우 DEBUG_ADDRESS_UNION 구조체의 공용 구조체의 일부입니다.

> [!WARNING]
> [C + + 전용] `pLocal` 가 null이 아니면 토큰 포인터에서를 호출 해야 합니다 `Release` ( `addr` 은 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조체의 필드).
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>요구 사항

헤더: sh

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보

- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
