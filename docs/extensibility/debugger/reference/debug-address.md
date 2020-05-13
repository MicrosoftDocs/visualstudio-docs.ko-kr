---
title: DEBUG_ADDRESS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737514"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
이 구조는 주소를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>멤버
`ulAppDomainID`\
프로세스 ID입니다.

`guidModule`\
이 주소를 포함하는 모듈의 GUID입니다.

`tokClass`\
이 주소의 클래스 또는 유형을 식별하는 토큰입니다.

> [!NOTE]
> 이 값은 기호 공급자에 만국되므로 클래스 형식의 식별자 이외에는 일반적인 의미가 없습니다.

`addr`\
개별 주소 형식을 설명하는 구조의 결합을 포함하는 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조입니다. 값 `addr`.`dwKind` ADDRESS_KIND [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거체에서 유래하여 노조를 해석하는 방법을 설명합니다.

## <a name="remarks"></a>설명
이 구조는 채울 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드에 전달됩니다.

**경고 [C++ 전용]**

있는 `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` 경우 `addr.addr.addrLocal.pLocal` null 값이 아닌 경우 토큰 `Release` 포인터를 호출해야 합니다.

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
